# Release checklist

Work on a feature branch from `main` and open a pull request. `main` requires
passing `validate` CI, an up-to-date branch and resolved conversations, including
for administrators. Squash-merge the PR after review. No build step is needed.

- Run `claude plugin validate . --strict`.
- Install from the marketplace and verify all nine skills load.
- Authenticate through Claude; verify setup with no accounts, one account, multiple accounts, expired consent, and exhausted limits.
- Verify status and reporting are read-only and unsupported metrics are unavailable rather than zero.
- Test requested private YouTube uploads only with selected test media and an explicitly authorized test account.
- Verify public/unlisted YouTube and all Instagram previews require approval before execution.
- Verify schedules show exact date, time, timezone, and asset expiry checks.
- Verify unknown upload outcomes are inspected before retrying.
- Test each intended Claude surface; record results before claiming support.
- Confirm privacy, retention, minors, and contact answers with the service owner before submitting.
- Submit the hosted MCP server separately as an MCP connector if it has not already been submitted.
- In https://claude.ai/directory/manage select Submit new > Plugin bundle; use keshavkatwe/pushwing-claude-plugin, root path, and main branch.
- Validate in the portal, address findings, and submit for review.
- Keep the repository public for publication. Increment plugin.json version for updates.

Authenticated behavior and portal validation have not been completed by the repository scaffold.

## Publishing guidance for MCP 0.13 and later

New publication reviews use `pushwing_prepare_publish_preview`, including private YouTube uploads, followed by the named original publishing tool after approval. Pass the resolved IANA `timezone` at the preparation root when its schema supports it. Account/usage checks remain plain reads; their display tools are for explicit requests. Future queued jobs are acknowledged without polling until their execution date; native YouTube publication schedules still require verifying the immediate upload. Older catalogs use the documented safe fallback and need a refresh after the server rollout. Plugin source updates do not deploy MCP or refresh an installed client catalog.

## Workspace workflows from plugin 0.2.0

Four additional skills cover brand-setup, new-post, continue-post and review-post.
The existing account setup remains read-only; publish/schedule can hand off a
selected saved post without requiring workspace records for standalone files.
Before release, deploy/verify the MCP workspace catalog separately, refresh it
in the intended client, and verify all nine skill entries. Preserve endpoint,
OAuth scope, app identity and installed-cache configuration. Merging source into
`main` makes it available through this Git marketplace.
Installation, server deployment, directory publication and fresh-client acceptance
remain separate actions; record their evidence separately.

## Discovery gate for 0.2.1 and later

Run package validation, `python3 -m unittest discover -s tests -v` and
`python3 scripts/smoke_discovery.py --host claude` before release. CI runs these
checks using a pinned client. The isolated native marketplace check must expose
all 97 baseline tools with both 35- and 100-entry pages. It uses mock local
endpoints and no real credentials, models or publishing operations.

Before claiming a marketplace fix, separately run the real-client catalog check
in [TESTING.md](TESTING.md). Preserve the incomplete-catalog failure as a failed
acceptance result even when the custom-MCP fallback works. Do not infer desktop
acceptance from the controlled CLI check or package validation.
