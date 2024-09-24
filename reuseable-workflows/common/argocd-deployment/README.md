# ArgoCD Manifest Update

This GitHub Action helps automate the process of updating a deployment manifest in your deployment repository with the latest image hash for your application. It helps simplify keeping your application's deployment configuration up-to-date with the latest image references.

## Setup

1. Copy the workflow file (`.github/workflows/argocd-deployment.yml`) to your repository.
2. Change the build step and variables passed to the action to fit your requirements
3. Set up the required secrets in your repository under ` Settings > Secrets and variables > Actions`.

### Variables to be passed to 'pujux/argocd-manifest-update' action

| Name                | Default                          | Required | Description                                                                                                         |
| ------------------- | -------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| deployment-repo     | -                                | ✅       | The deployment repository holding the deployment manifests                                                          |
| deployment-repo-ref | main                             | ❌       | The deployment repository ref to be used                                                                            |
| github-token        | -                                | ✅       | The GitHub Token required to access the deployment repository. Needs read and write access to deployment repository |
| manifest-file       | -                                | ✅       | The path of the manifest file in your deployment repository                                                         |
| image-name          | -                                | ✅       | The Docker image name                                                                                               |
| image-tag           | -                                | ✅       | The new tag value name                                                                                              |
| git-email           | pujux@argocd-manifest-update.com | ❌       | The email to be used for the Git commit                                                                             |
| git-name            | pujux                            | ❌       | The username to be used for the Git commit                                                                          |

## Troubleshooting

If you encounter any issues:

1. Check the action logs in the "Actions" tab of your repository.
2. Ensure all required variables are set correctly.
3. Ask for help in the 'Internal Development' Teams Channel.
