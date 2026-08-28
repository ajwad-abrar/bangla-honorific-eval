# A Bangla honorific evaluation set

Data for an anonymous submission to GeBNLP 2026.

English does not mark respect. Bangla forces the choice: every sentence about a
person selects either the ordinary register (সে *shey*, করে *kore*) or the
honorific one (তিনি *tini*, করেন *koren*). A translation system therefore has to
commit to a level of deference the English never specified, and whatever
deference appears in the Bangla was supplied by the model rather than the
source.

These files are the English inputs for measuring that choice.

## Files

**`bangla_honorific_eval.csv`** — 2,016 items: 72 occupations × 7 sentence
frames × 4 conditions.

| Column | |
|---|---|
| `id` | serial number, 1–2016 |
| `item_id` | `occupation|template|condition` |
| `occupation_en`, `occupation_bn` | the occupation, in English and Bangla |
| `template_id` | `T1`–`T5`, `P1`–`P2` |
| `primed` | whether the frame states outright that the person is respected |
| `gender` | `male` / `female` / `they` / `nopronoun` |
| `source_en` | the English sentence to translate |

**`occupations.csv`** — the 72 occupations and the Bangla term used for each,
with columns `id`, `en` and `bn`.

## The four conditions

Each occupation appears under a masculine pronoun, a feminine one, singular
*they*, and no pronoun at all.

The masculine and feminine versions are identical apart from the pronoun, which
is what makes them a matched pair: any difference in the Bangla register came
from that one token and nothing else. The no-pronoun condition carries no gender
signal at all, so it isolates what a model does on the occupation alone. Two of
the seven frames, `P1` and `P2`, state outright that the person is respected,
which tests whether an explicit cue in the source overrides whatever the model
would otherwise do.

## Grounding

The set is built for Bangladesh rather than for Bangla in general. It includes
roles that carry particular weight there — মুক্তিযোদ্ধা (freedom fighter), ইমাম
(imam), গার্মেন্টস কর্মী (garment worker), রিকশাচালক (rickshaw puller),
গৃহকর্মী (domestic helper).

Bangla terms were chosen as a newspaper would print them, and deliberately avoid
words that carry gender in the term itself. নার্স was used rather than সেবিকা
for that reason: the latter is morphologically feminine, and would build gender
marking into an item designed to measure it.

## Encoding

UTF-8 with BOM, so the Bangla renders correctly when opened in Excel. On
Windows, set `PYTHONIOENCODING=utf-8` before printing these columns from Python.

## Use

Released for research use.
