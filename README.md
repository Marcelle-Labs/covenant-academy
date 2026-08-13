# Covenant Academy

The semantic truth of the Academy: who the household is, which figures the
stories may name, and the editorial writing itself — what the child hears.

This is **not** a production runtime. Nothing here executes, builds, or ships.
Production (ElevenLabs narration, captions, packaging, the Yoto pipeline) lives
in the sibling `demo-studio` repo, which reaches into this tree read-only
through an explicit manifest contract.

## Layout

```text
canon/
  people.json        the real household: roles, voice policy, dated ages
  cast.json          story figures, each attested to a committed document
series/
  sukkot/
    arc.md           the twelve-track arc spec (curriculum)
    script.md        the authored narration beats the child hears
```

## The contract

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

## Editing rules

- `canon/people.json` holds personal detail about real people, one of them a
  child. Ages are dated observations (`{ years, asOf }`), re-confirmed each
  feast cycle — never birth dates.
- `canon/cast.json` introduces nothing: every figure cites where it is
  attested in a committed document. A figure without a citation is an
  invention and fails validation on the Director side.
- Neither file ever enters a delivery bundle.
- `series/sukkot/script.md` carries the `DRAFT — NOT PARENT APPROVED` marker
  until `review.childFacingCleared` flips true on the Director side. Clearance
  requires `parent_approved` status and `family_recorded` narration.
