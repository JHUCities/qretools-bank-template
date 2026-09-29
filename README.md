# A question bank for qretools

Survey questions and their documentation, one YAML file per question, edited with
[qretools](https://jhucities.github.io/qretools/), which elaborates them to
DDI-Lifecycle 4.0.

This repository is the template for new banks:
<https://github.com/JHUCities/qretools-bank-template>. Start one with
[Use this template](https://github.com/JHUCities/qretools-bank-template/generate).

## Set up a new bank from this template

1. **Create your bank:** "Use this template" → "Create a new repository". A private
   repository is fine.
2. **Install the qretools app** on the new repository:
   <https://github.com/apps/qretools/installations/new> → choose your account or
   organisation → "Only select repositories" → this one. Without it you can read the
   bank in qretools but not save.
3. **Protect `main`:** Settings → Rules → Rulesets → New branch ruleset. Target the
   default branch; turn on "Require a pull request before merging", "Block force
   pushes" and "Restrict deletions". qretools saves each author's work to their own
   branch (`qretools-<login>`); the bank changes only when a pull request is merged.
4. **Tidy merged branches:** Settings → General → Pull Requests → "Automatically delete
   head branches".
5. **Open it:** sign in at <https://jhucities.github.io/qretools/> and enter the
   repository as `owner/name`.

## Layout

| Path | Holds |
|---|---|
| `questions/<folder>/<name>.yaml` | one question each; the folder is chosen when a question is first saved, and says nothing about the question's name |
| `scales/<name>.yaml` | shared response scales (`labels:`), used by name from `responses:` |
| `universes/<name>.yaml` | shared universes (`text:`), used by name from `universe:` |
| `instructions/<name>.yaml` | shared instructions (`text:`), used by name from `instruction:` |
| `missing.yaml` | the bank's missing-value codes (`labels:`) |

`scales/yesno01.yaml` must stay as it is (`0: No`, `1: Yes`): select-all-that-apply
questions record each option on it. The codes in `missing.yaml` are this template's
example; use your own conventions.

## Shared values, and keeping the bank free of duplicates

Four things can be written once and named from any question:

| Shared | Named from | Example here |
|---|---|---|
| a response scale | `responses: satisfied5` | `scales/satisfied5.yaml` |
| a universe | `universe: all_respondents` | `universes/all_respondents.yaml` |
| an instruction | `instruction: select_one` | `instructions/select_one.yaml`, `select_all.yaml` |
| the missing-value codes | every question, implicitly | `missing.yaml` |

Anything else is written in the question. qretools points out repetition as you type:

- the same question text, response list, universe or instruction in two questions, or
  two shared scales with the same labels (a warning on each, linking to the other);
- a response list, universe or instruction written out that a shared one already says
  ("use the name");
- a unit spelled two ways (`days` and `Days`);
- a question worded much like another (a note, quoting the other).

When two questions are alike on purpose, say so in either of them, with why they
differ, and the warning goes:

```yaml
variant_of:
  income_high: split ballot, lower income range
```

`questions/examples/service_satisfaction.yaml` is an example to copy or delete. Name
questions and folders however your team prefers: qretools reads nothing into either.
