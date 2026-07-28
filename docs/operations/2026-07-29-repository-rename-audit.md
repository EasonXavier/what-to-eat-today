# Repository rename audit

## Operation

- Operation ID: `repo-rename-2026-07-29-what-to-eat-today`
- Status: `prepared`
- Repository ID: `1300417121`
- Default branch: `main`
- Visibility: `public`
- Prepared at: `2026-07-29T07:17:17+08:00` (`2026-07-28T23:17:17Z`)
- Baseline commit: `9604445e2866d4076c480811095e059eea3aad2a`
- Old repository: `EasonXavier/What-to-eat-today`
- New repository: `EasonXavier/what-to-eat-today`
- Old repository URL: `https://github.com/EasonXavier/What-to-eat-today`
- New repository URL: `https://github.com/EasonXavier/what-to-eat-today`
- Old Pages URL: `https://easonx.me/What-to-eat-today/`
- New Pages URL: `https://easonx.me/what-to-eat-today/`

## Preflight findings

- The repository name is being normalized to lowercase; its stable GitHub repository ID must remain unchanged.
- Application assets use relative paths and do not depend on the repository name.
- The application links back to the portal. That link is normalized from the default `github.io` hostname to `https://easonx.me/`.
- No GitHub Actions consumer, submodule, package coordinate, raw-content URL, or API endpoint references this repository by its old name in the owner's other repositories.
- The owner chose a direct Pages cutover. The old project Pages URL is not retained by a compatibility redirect.

## Planned changes

1. Commit this audit and the portal return-link normalization on `main`.
2. Rename the GitHub repository to `what-to-eat-today`.
3. Update `origin` to the new repository URL.
4. Append the actual rename time, commits, and verification evidence to this file.
5. Push the completion record to trigger a Pages deployment and verify the new URL.

## Rollback

1. Rename the GitHub repository back to `What-to-eat-today`.
2. Set `origin` to `https://github.com/EasonXavier/What-to-eat-today.git`.
3. Restore any technical references that were switched to the lowercase Pages path.
4. Append a rollback event to this audit file; do not delete the audit history.
5. Commit and push the rollback record to `main`.
6. Verify `https://easonx.me/What-to-eat-today/` returns HTTP 200 and serves the application.

Do not create a new repository using the old name because doing so would break GitHub's repository redirect.
