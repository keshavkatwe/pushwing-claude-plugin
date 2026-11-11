# Release checklist

Work on a feature branch from `main` and open a pull request. `main` requires
passing `validate` CI, an up-to-date branch and resolved conversations, including
for administrators. Squash-merge the PR after review. No build step is needed.

- Run `claude plugin validate . --strict`.
- Install from the marketplace and verify all five skills load.
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
