# Nia — Character Brief

The canon document for Nia, Covenant Academy's recurring child companion. This
file is the attestation source cited by her entry in `canon/cast.json`.

Nia is an **authored original character**, not a figure retold from scripture or
household history. Every other entry in `cast.json` is attested in series
material because it was retold from a source; Nia is attested here because this
brief is where she was authored. That distinction is deliberate — see the
editing rules in `README.md`.

**Status:** canon defined · one pilot drafted, pending parent review · voice not cleared

---

## 1. Identity

| | |
|---|---|
| Name | Nia |
| Spoken as | NEE-ah |
| Type | child companion (recurring, voiced) |
| Canonical age | 8 — fixed, not a dated observation |
| Pronouns | she/her |
| Primary language | English |
| Dialect baseline | contemporary American English |
| Voice alias | `nia-companion` |

Her age is written as a fixed canonical value, not as the
`{ years, asOf }` dated observation that `people.json` uses. Real household ages
drift and are re-confirmed each feast cycle. Nia is eight in every track she
appears in, this year and next.

**Nia is not the narrator.** Abba narrates. Nia is a second person in the room.
Her entrance into a scene should be recognizable within a sentence as someone
else's point of view — a different vantage, not a different tone of the same
voice.

## 2. Cultural identity

Nia's family has **Jamaican roots and Haitian roots**. This is intentional and
load-bearing: Covenant Academy is countering culturally flattened and
whitewashed presentations of biblical stories, and a companion whose own family
carries real geography, migration, food, and memory is part of how the child
learns that the people in these stories were culturally and geographically real
too.

Her culture is carried by **character, not by accent**.

**Where it lives:**

- warmth and the way she addresses people
- musical intonation and rhythmic phrasing
- family expressions, stories, and what gets remembered out loud
- food, geography, history, and relationships
- who taught her a thing, and when

**Where it does not live:**

- Her ordinary speech is natural contemporary American English.
- She does not perform a generic "Caribbean accent."
- She does not default to Jamaican Patois.
- She does not default to Haitian Creole.
- Patois or Creole may appear **only** where the wording and its meaning have
  been sourced or explicitly family-approved, per track.

**Operating decision (2026-08-13): permission is preserved, usage is deferred.**
No Patois or Haitian Creole appears in Nia's default dialogue. Individual
sourced, family-approved items are introduced only when a story gives one a real
reason to exist. This is deliberate: the predictable failure mode is sprinkling
culturally marked language around to make her read as "authentic," which is
caricature arriving by a politer road. Her heritage should already be detectable
through her world, her family, and her perspective. The first Creole or Jamaican
moment should therefore mean something.
- Do not invent Creole, Patois, transliteration, pronunciation, or cultural
  sayings. This is the same rule the Shema slot already operates under in
  `series/school-start/2026-08-13-thursday-am/script.md`: unretrieved wording
  stays unwritten rather than getting a plausible substitute.
- No caricature.

## 3. Personality

Curious · observant · playful · emotionally grounded · warm · thoughtful ·
willing to ask sincere questions · confident without being precocious.

Her intelligence shows up as **noticing, remembering, wondering, connecting, and
reasoning** — not as adult vocabulary.

She is not a miniature adult, not a teacher, not a children's-TV mascot, not an
exposition device, and not exaggeratedly cute.

## 4. Pedagogical function

Nia helps the listener:

- notice details
- wonder aloud
- ask the question the listener may also have
- retrieve something learned earlier
- connect covenant themes across stories
- meet biblical events from a child's vantage
- experience people in biblical history as culturally and geographically real
- model curiosity without always knowing the answer

She does **not** replace the parent, the narrator, or the source material as an
authority. She can ask, notice, remember, and make reasonable child-level
connections. She does not announce theological conclusions.

This is the same formation target the school-start track already names —
*"your job is to notice"* — given a second body in the room. Nia models the
posture rather than instructing the listener into it.

## 5. Register

The canonical listener (Quinn, 6) is younger than Nia and the delivery is
voice-first, so Nia's dialogue targets a first-to-second-grade listening level:

- short spoken sentences
- concrete language
- natural contractions
- conversational rhythm
- one idea at a time
- minimal abstract terminology
- read-aloud friendly

She may occasionally know something the listener doesn't. She should read as a
slightly older friend, never as an instructor.

## 6. Narrative safety

Nia is a **companion lens**, not a historical witness.

In bounds:

> "I wonder what that felt like."
> "That reminds me of…"
> "Did you notice…?"
> "Wait. We heard something like that before."

Out of bounds by default:

> "I was there when…"
> "I saw Moses…"
> "God definitely meant X because…"

A future series may establish an explicit imaginative framing that permits a
witness posture. Until such a framing is authored and approved, it is not
available, and Nia is not placed inside a biblical event as though present.

She is recurring and capable of dialogue inside a scene — she is not limited to
introducing lessons — but she does not narrate every story, and she does not
narrate in Abba's place.

## 7. Voice canon

Editorial voice intent only. No provider, no voice id, no synthesis settings —
those belong to Director.

```yaml
voice_alias: nia-companion
perceived_age: 8
language: en
voice_policy: synthetic-prototype-only
final_requirement: family_recorded
```

These are **entity permissions** — what Nia is allowed to use, true of her
across every track. They are not artifact state. `narration_mode` and
`child_facing_cleared` describe how one particular recording is currently being
produced, so they live in that script's frontmatter, never here. A track can be
mid-prototype or fully cleared without anything about Nia changing.

**Qualities:** youthful · warm · clear · natural · conversational · expressive ·
curious · playful · emotionally responsive.

**Cultural delivery intent** — the canonical wording, kept self-contained so it
can be handed to a voice-design step verbatim without re-editing:

> An eight-year-old girl. Warm, clear, natural, conversational, curious and
> playful, emotionally responsive. Contemporary American English with subtle
> Jamaican-Haitian family influence expressed through warmth, musical
> intonation, and rhythmic phrasing — inherited and natural rather than
> performed. Not an exaggerated Jamaican or Haitian accent, not a generic
> Caribbean impression, not sing-song children's-media delivery, not commercial
> voiceover, not exaggerated cuteness, not adult-sounding precociousness. She
> sounds like a real child talking to a friend.

**Explicitly avoid:** exaggerated Jamaican accent · imitated Haitian accent ·
generic Caribbean caricature · invented Patois · invented Haitian Creole ·
exaggerated cuteness · sing-song children's-media delivery · commercial
voiceover delivery · adult-sounding precociousness.

**Clearance.** COV-79 governs: family voice is formation doctrine. A synthetic
take of Nia is a pacing prototype only and is never child-facing cleared. The
final requirement is `family_recorded`, exactly as it is for Abba. Nothing in
this file approves her voice.

## 8. Relationships

- **Nia ↔ Abba (narrator).** Complementary perspectives, never the same voice or
  role. Abba tells; Nia wonders. Distinct alias, distinct performer.
- **Nia ↔ Quinn (listener).** Companion, sideways rather than downward. Nia
  wonders alongside her; she does not quiz her, correct her, or hand her
  conclusions.
- **Nia ↔ the rest of the cast.** She may interact where existing canon already
  supports it. No family relationship between Nia and the household is canon,
  and none is invented here.

## 9. Open

1. ~~First series appearance is unwritten.~~ **Drafted 2026-08-14** — the
   long-form pilot at `series/nia-story-specials/miriam-watch-by-the-water/`,
   the one episode the gate in §7 and Character Canon v2 require before any
   bulk production. It is `pending_parent_review`; nothing in it is approved,
   and nothing places her in an earlier episode.
2. ~~Scripts have no speaker-attribution notation.~~ **Settled 2026-08-13** —
   frontmatter alias map plus human speaker labels. See `README.md`,
   *Multi-voice scripts*.
3. ~~Whether Patois or Creole appears at all.~~ **Settled 2026-08-13** —
   permission preserved, usage deferred. See §2.
4. Nia's `final_requirement` is `family_recorded`, and the current household
   roster contains no one who can satisfy it for an eight-year-old girl. Open.
