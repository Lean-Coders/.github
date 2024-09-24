# Sync Upstream and Create PR Action

This GitHub Action automatically syncs your private fork with the upstream repository and creates pull requests on a schedule or manual trigger. It's designed to keep your fork up-to-date with minimal manual intervention.

Note that this is only required for forks that are private and thus not inside the fork network. For public forks, there are out-of-the-box Actions available.

## Setup

1. Copy the workflow file (`.github/workflows/sync-upstream.yml`) to your repository.
2. Set up the required variables and secrets in your repository under ` Settings > Secrets and variables > Actions`.

### Variables

| Name | Default | Required |
|------|---------|----------|
| UPSTREAM_REPO | - | ✅ |
| FORK_BASE_BRANCH | main | ❌ |
| OWN_BRANCH | main | ❌ |
| USER_EMAIL | actions@github.com | ❌ |
| USER_NAME | GitHub Actions | ❌ |
| SYNC_SCHEDULE | 0 0 * * 0 *(=weekly on Sunday)* | ❌ |

### Secrets

 A GitHub personal access token with necessary permissions (only required in specific cases, such as when workflow files are written inside a workflow)

| Name | Default | Required |
|------|---------|----------|
| WORKFLOW_TOKEN | github.token | ❌ |



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