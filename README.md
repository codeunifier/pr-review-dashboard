# pr-review-dashboard
A simple little one-pager that fetches GitHub PRs and displays them so that it's easy to see who needs to pair up.

## Local environment config

You can put sensitive or local-only values in `env.local.js`.

Start by copying `env.example.js` to `env.local.js`, then fill in your real values.

The app reads this file (if present) from `window.PR_DASHBOARD_ENV`.

```js
window.PR_DASHBOARD_ENV = {
	repository: 'owner/repo',
	githubToken: 'ghp_xxx_optional',
	allowedAuthors: ['alice', 'bob']
};
```

Notes:
- `env.local.js` is gitignored.
- `env.example.js` is safe to commit and documents the expected shape.
- If both `repository` and `githubToken` are set in `env.local.js`, the repo/token input fields are hidden in the UI.
- `allowedAuthors` is optional. If omitted or empty, PRs from all authors are shown (draft PRs are still excluded).
- A token saved in browser localStorage takes precedence over `githubToken` from `env.local.js`.
