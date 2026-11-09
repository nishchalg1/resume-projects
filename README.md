# Project - Resume

Three portfolio projects, kept in this repo and deployed to GitHub and Vercel.

**Status:** repo set up. No project has been built yet.

## Projects

| Project | Folder | Problem | Status |
| --- | --- | --- | --- |
| Reporting Workflow Automation | `reporting-workflow-automation/` | Recurring reports consumed analyst hours that could go to analysis — manual pulls, formatting and distribution, repeated every cycle. | Not started |
| Customer Segmentation with K-Means | `customer-segmentation-kmeans/` | One-size-fits-all marketing treats a high-value regular and a lapsed one-timer the same. The goal: find behaviourally distinct customer groups that can each get a different strategy. | Not started |
| Customer Recommendation Model | `customer-recommendation-model/` | Customers see the same catalogue regardless of what they have bought. The goal: surface relevant products per customer to support cross-sell, engagement and retention. | Not started |

## Deployment accounts

Use these accounts for every deployment.

| Service | Account | Check with |
| --- | --- | --- |
| Email | `nishchal.gupta03@gmail.com` | `git config user.email` |
| GitHub | `nishchalg1` | `gh auth status` |
| Vercel user | `nishchalgupta03-5254` | `vercel whoami` |
| Vercel team (Hobby) | `nishchal4` | `vercel teams ls` |

Stop and fix the login if either CLI reports a different account. Pass `--scope nishchal4` to Vercel CLI commands.

The `nishchal_gupta` project in this team is the live portfolio site (`nishchalgupta.vercel.app`). It is separate from this repo, so never link or deploy these projects to it.

## Deployment setup

Each project is a separate Vercel project, connected to this one GitHub repo. Each one uses its own folder as its Root Directory.

### 1. Git identity

Commits need this email so GitHub and Vercel attribute them to the right account. It is set for this repo only, because this machine has no global git identity.

```bash
git config user.name "nishchalg1"
git config user.email "nishchal.gupta03@gmail.com"
```

This email is verified on the `nishchalg1` GitHub account.

### 2. GitHub remote

Already created as a public repo: <https://github.com/nishchalg1/resume-projects>. Pushes go to `origin main`.

Because the repo is public, everything committed is visible to anyone.

### 3. Vercel projects

Repeat for each project once its folder exists:

1. In the `nishchal4` team, go to Add New > Project and import this GitHub repo.
2. Set **Root Directory** to the project's folder from the table above.
3. Add the project's environment variables.
4. Deploy.

Vercel then deploys that project's production site on every push to `main`, and a preview for other branches.

## Avoiding deployment problems

- **Never commit secrets.** Keep them in `.env` locally and in Vercel's environment variables. `.gitignore` already excludes `.env*` and `.vercel/`.
- **Keep model files and datasets small.** Vercel Functions have a bundle size limit. For the K-Means and recommendation projects, precompute results and serve them, or host large files elsewhere.
- **Don't rely on Vercel for long-running jobs.** Functions have execution time limits and no persistent filesystem. Scheduled report runs need Vercel Cron or GitHub Actions, and outputs need external storage.
- **Confirm the commit author before debugging a blocked deployment.** Run `git log -1 --format='%ae'`; it should print the email above.
