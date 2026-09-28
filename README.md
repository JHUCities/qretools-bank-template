# A question bank for qretools

Survey questions and their documentation, one YAML file per question, edited with
[qretools](https://jhucities.github.io/qretools/), which elaborates them to
DDI-Lifecycle 4.0.

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

`questions/examples/service_satisfaction.yaml` is an example to copy or delete. Name
questions and folders however your team prefers: qretools reads nothing into either.
