# Covenant Academy

The semantic truth of the Academy: who the household is, which figures the
stories may name, and the editorial writing itself — what the child hears.

This is **not** a production runtime. Nothing here executes, builds, or ships.
No `package.json`, no framework, no generated media, no deploy configuration.

## The three-repo split

This repo is one of three. Each answers a different question, and none of them
owns the other two's truth.

```text
                     covenant-academy
                    semantic/editorial truth
                            │
                ┌───────────┴───────────┐
                ▼                       ▼
          demo-studio            covenant-academy-web
        media production          experience runtime
                │                       │
          audio / captions          Astro shell
          validated media           React islands
          Yoto packaging       child/family/parent UX
                └───────────┬───────────┘
                            ▼
                     child experience
```

| Repo | Answers | Must not own |
| --- | --- | --- |
| `covenant-academy` | What is true? What may be said? Who is speaking? | runtime code, generated media, provider config, deploys |
| `demo-studio` | How is approved spoken content produced and packaged? | curriculum authorship, canonical character truth |
| `covenant-academy-web` | How does the family encounter approved material? | invented theology, canonical scripts, provider config |

**Academy authors. Director produces. Web presents.**

Both consumers reach into this tree **read-only** through an explicit manifest
contract — Director through `product-lock.json`, Web through
`academy-lock.json`. Each pins the commit of this repo it was locked against.
Neither keeps a copy of `canon/` or `series/`: there is exactly one copy of each
canon file, and it is this one.

### What that means for the web runtime

`covenant-academy-web` never crawls `series/**/script.md` and renders what it
finds. This tree deliberately holds drafts carrying the
`DRAFT — NOT PARENT APPROVED` marker, and **editorial existence here is not
child-facing clearance**. The web runtime consumes only a cleared projection:

```text
Academy content → source + policy validation → artifact review → web-visible catalog
```

That distinction is the same one the editing rules below draw between entity
permission (`voicePolicy`, `finalRequirement`) and artifact state
(`narrationMode`, `childFacingCleared`). It holds across repo boundaries too.

## Layout

```text
canon/
  people.json        the real household: roles, voice policy, dated ages
  cast.json          story figures, each attested to a committed document
  nia.md             character brief for the recurring child companion
series/
  sukkot/
    arc.md           the twelve-track arc spec (curriculum)
    script.md        the authored narration beats the child hears
  school-start/
    2026-08-13-thursday-am/
      script.md      one dated daily track, authored per morning
  nia-story-specials/
    arc.md           the long-form experiment's spec
    miriam-watch-by-the-water/
      script.md      Pilot 01 — the first two-voice track
```

A feast arc, a daily track, and a story special are shaped differently. An arc
is one curriculum spanning many tracks, so `sukkot/` holds an `arc.md` beside a
single script. The school-start series is a run of separate mornings with no
shared arc spec, so each track gets its own dated directory and stands alone.
The story specials are long single episodes that do share a spec, so
`nia-story-specials/` keeps an `arc.md` at the series root and gives each
episode its own named directory — the two shapes composed, not a third one.

An episode directory is what a Director production points `evidenceRoot` at, so
the file inside it is always `script.md`. The episode's own title lives in the
directory name and in the script's frontmatter, never in the filename.

## The Director contract

A Director production declares this repo as its canon source in its
`product-lock.json`:

```json
{
  "productRoot": "<path to this repo, relative to the project dir>",
  "evidenceRoot": "series/sukkot",
  "academyCanon": {
    "people": "canon/people.json",
    "cast": "canon/cast.json"
  }
}
```

`productCommit` in that manifest anchors the commit of this repo the
production was locked against. There is exactly one copy of each canon file —
this one. Director keeps no synchronized copies, and `studio validate` fails
if a declared registry is missing or a duplicate survives in the legacy
group directory.

## The Web contract

`covenant-academy-web` declares this repo as its editorial source in its
`academy-lock.json`, following the same pattern — explicit path, pinned source
revision, explicit allowed inputs:

```json
{
  "academyRoot": "../covenant-academy",
  "academyCommit": "<git commit>",
  "contentManifest": "<path to the cleared projection>",
  "allowedInputs": {
    "canon": ["canon/people.json", "canon/cast.json"],
    "series": []
  }
}
```

`academyCommit` anchors the commit of this repo the runtime was locked against.
`allowedInputs` is declared for provenance; listing a path there is **not**
permission to render its contents to a child. The runtime reads only
`contentManifest`, and while that is null it renders empty rather than falling
back to this tree — the fallback is exactly how a draft would reach a child.

The lock is deliberately not a glob. Coupling to `covenant-academy/**/*` would
bind the runtime to this repo's filesystem instead of to a contract.

## Editing rules

- `canon/people.json` holds personal detail about real people, one of them a
  child. Ages are dated observations (`{ years, asOf }`), re-confirmed each
  feast cycle — never birth dates.
- `canon/cast.json` is the source of truth for narrative characters, and it
  introduces nothing: every figure cites where it is attested in a committed
  document. A figure without a citation is an invention and fails validation on
  the Director side. Retold figures cite the series material they were retold
  into. An authored original — a recurring companion who was never retold from a
  source — cites a canon character brief beside these registries instead
  (`canon/nia.md`). The citation requirement does not relax; only the document
  it points at differs.
- Neither registry ever enters a delivery bundle.
- Voice aliases (`qwynn-narrator`, `nia-companion`) are stable editorial
  identifiers, kebab-case, and unique across both registries. Canon and scripts
  name a voice only by alias; provider voice ids, model choices, and synthesis
  settings live in Director and never appear here. Character canon is not
  synthesis configuration.
- Cultural language — Hebrew, Patois, Haitian Creole, anything a household or
  a family speaks — is retrieved or family-approved before it is written. An
  unretrieved wording stays unwritten. A plausible substitute is an invention.
- **Entity permission is not artifact state.** `voicePolicy` says what a person
  or character is permitted to use and `finalRequirement` says what must be true
  of the final child-facing artifact — both are properties of the entity, and
  both live in the canon registries. `narrationMode` and `childFacingCleared`
  describe how one recording is being produced right now, and live in that
  script's frontmatter. A track can move from prototype to cleared without
  anything in `canon/` changing. Do not collapse the two vocabularies into one
  enum; they answer different questions.

## Multi-voice scripts

A track with more than one voice declares its aliases in frontmatter, then
labels each speaker in the body:

```yaml
voices:
  narrator: qwynn-narrator
  nia: nia-companion
```

```md
### Beat 3 — The Little Path

**NARRATOR**

There was one more path behind the trees.

*Direction: warm, close, unhurried.*

**NIA**

Wait. Did you see that?

*Direction: curious; excitement beginning to rise.*
```

Academy says **who** speaks and gives human performance direction. Director maps
each alias to a provider voice and translates direction into whatever tags or
settings that provider wants. Provider tag syntax never appears in a script —
write `*Direction: curious*`, not `[curious]`. The notation stays readable to a
parent, and stays portable if the provider ever changes.
- Every `script.md` carries the `DRAFT — NOT PARENT APPROVED` marker until
  `review.childFacingCleared` flips true on the Director side. Clearance
  requires `parent_approved` status and `family_recorded` narration.
- Scripts carry no provider voice ids, synthesis settings, secret configuration,
  or generated media. A script names its narrator by alias (`qwynn-narrator`);
  Director resolves that alias to a provider and a voice, and only Director
  knows which.
