# Build Android Artifact + GitHub Release

This GitHub Action automates the build process for your Flutter Android application. It's triggered on pushes to the `develop` and `main` branches, or can be manually dispatched with custom build flavor options.

## Setup

1. Copy the workflow file (`.github/workflows/cd-android.yml`) to your repository.
2. Set up the required secrets in your repository under `Settings > Secrets and variables > Actions`.
3. Ensure you have a `.fvmrc` file in your repository root with the Flutter version and channel specified.

## Functionality

1. **Build Android**:
   - Sets up the specified Flutter version.
   - Creates an `.env` file with secrets.
   - Runs `build_runner` for code generation.
   - Checks code formatting and runs analysis.
   - Builds both APK and AppBundle.
   - Uploads the built artifacts to GitHub.

2. **Tag Version and Create Release**:
   - Creates a Git tag with the version number.
   - Downloads the built artifacts.
   - Creates a GitHub release with the artifacts attached.

## Variables

| Name | Source | Description |
|------|--------|-------------|
| FLUTTER_VERSION | .fvmrc | Flutter version to use |
| FLUTTER_CHANNEL | .fvmrc | Flutter channel to use |
| BUILD_FLAVOR | Workflow | Build flavor (dev/prod) based on branch or manual input |
| RELEASE_DATE | Workflow | Current date in ISO format |
| ARTIFACT_NAME_APK | Workflow | Generated name for the APK artifact |

## Secrets

| Name | Required | Description |
|------|----------|-------------|
| SENTRY_DSN | ✅ | Sentry DSN for error tracking |
| KEYSTORE_PASSWORD | ✅ | Password for the Android keystore |
| KEYSTORE_KEY_ALIAS | ✅ | Alias for the key in the keystore |
| KEYSTORE_KEY_PASSWORD | ✅ | Password for the key in the keystore |
| KEYSTORE | ✅ | Base64 encoded Android keystore file |

## .env

If a .env file is used to store secrets:
1. add the secrets to your repository
2. uncomment the "Create env file" step and adjust for your secret names

## Customization

- The workflow can be manually triggered with a choice of build flavor (dev/prod).
- Artifact retention period is set to 90 days for the main branch and 30 days for other branches.
- The workflow creates a pre-release when manually triggered and a full release for pushes to the main branch.

## Troubleshooting

If you encounter any issues:

1. Check the action logs in the "Actions" tab of your repository.
2. Ensure all required secrets are correctly set in your repository settings.
3. Verify that your `.fvmrc` file is correctly formatted and contains the necessary information.
4. If you're using code generation, ensure all necessary files are committed to the repository.