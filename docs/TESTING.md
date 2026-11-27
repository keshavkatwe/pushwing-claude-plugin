# Client checks

Package validation does not install plugins, authenticate or call providers.

## Workspace acceptance cases — authored, not executed

Use disposable fixtures on the workspace-enabled development server. Record the
installed plugin/server versions and actual outputs; do not use production accounts.

| Request/scenario | Expected observable behavior |
| --- | --- |
| “Set up this brand from these notes; the logo is unknown.” | Save supported structured fields; unknown logo empty; original prose retained; no content or publishing writes |
| Brand update with an existing unrelated channel preference | Preserve that entry and existing playbook UUIDs; reject stale expectedVersion |
| “Start a carousel for this exact Instagram account.” | Explicit carousel/square planning record, initial saved revision and intended account; no staging or publish job |
| Create succeeds; initial revision times out | Reload the existing content ID; no duplicate record |
| Resume a post after the brand changed | Use pinned context; report available update; no silent adoption or invented approval |
| “Save progress for another chat.” | Save a note tied to the current revision; a fresh chat recovers next action and actual file references |
| “Review this render.” | Critique/QA is separate from creator acceptance; inaccessible artifacts labelled uninspected |
| Explicit script acceptance | Preview the exact revision/scope/evidence; confirm only after preview approval; no render or publication approval |
| A revision changes after acceptance | Old evidence remains with the old revision; new applicable scopes pending |
| Workspace tools absent from an older service | Clear capability limitation; useful draft labelled unsaved; no credential/database/endpoint workaround |
| Publish a standalone file | Existing publish flow works without requiring a brand or workspace review ledger |
| Publish a selected saved post | Current accepted files/account/copy used in concrete publication preview; note failure never republishes |
