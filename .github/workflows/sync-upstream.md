# Sync Upstream and Create PR Action

This GitHub Action automatically syncs your private fork with the upstream repository and creates pull requests on a schedule or manual trigger. It's designed to keep your fork up-to-date with minimal manual intervention.

Note that this is only required for forks that are private and thus not inside the fork network. For public forks, there are out-of-the-box Actions available.

## Setup

1. Copy the workflow file (`.github/workflows/sync-upstream.yml`) to your repository.
2. Set up the required variables and secrets in your repository under ` Settings > Secrets and variables > Actions`.

### Required Variables

- `UPSTREAM_REPO`: The upstream repository to sync from (e.g., `original-owner/original-repo`)

### Optional Variables

- `FORK_BASE_BRANCH`: The branch in the upstream repo to sync from (default: 'main')
- `OWN_BRANCH`: Your branch to sync into (default: 'main')
- `USER_EMAIL`: The email for git config (default: 'actions@github.com')
- `USER_NAME`: The name for git config (default: 'GitHub Actions')
- `SYNC_SCHEDULE`: Cron schedule for automated sync (default: '0 0 * * 0', which is weekly on Sunday)

### Optional Secrets

- `WORKFLOW_TOKEN`: A GitHub personal access token with necessary permissions (only required in specific cases, such as when workflow files are written inside a workflow)

## Functionality

1. The action then checks if there are any new commits in the upstream that are not in your fork.
2. If new changes are detected:
   a. A new branch is created with the current date.
   b. The changes from the upstream are merged into this new branch.
   c. A pull request is created to merge these changes into your specified branch.
3. If no changes are detected, the workflow completes without creating a pull request.

## Troubleshooting

If you encounter any issues:

1. Check the action logs in the "Actions" tab of your repository.
2. Check the `Debug Information` step of the action.
3. Ensure all required variables are set correctly.
4. Verify that the upstream repository and branch names are correct.
