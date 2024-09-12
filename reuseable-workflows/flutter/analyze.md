# Analyze and Test Workflow

This GitHub Action runs analysis and tests for your Flutter project. It's designed to ensure code quality and catch potential issues in your pull requests and pushes.

## Setup

1. Copy the workflow file (`.github/workflows/analyze-and-test.yml`) to your repository.
2. Ensure you have a `.fvmrc` file in your repository root with the Flutter version and channel specified.

## Functionality

1. **Semantic Pull Request Check**: 
   - Ensures that pull request titles follow semantic conventions.

2. **Run Analysis**:
   - Sets up the specified Flutter version.
   - Installs dependencies.
   - Runs `dart format` to check code formatting.
   - Executes `build_runner` to check for code generation errors.
   - Analyzes the `lib` and `test` directories if changes are detected.

3. **Run Tests**:
   - Sets up the specified Flutter version.
   - Installs dependencies.
   - Runs all tests in the project.

## Variables

| Name | Source | Description |
|------|--------|-------------|
| FLUTTER_VERSION | .fvmrc | Flutter version to use |
| FLUTTER_CHANNEL | .fvmrc | Flutter channel to use (defaults to 'stable') |

## Secrets

If a .env file is used to store secrets:
1. add the secrets to your repository
2. uncomment the "Create env file" step and adjust for your secret names

## Troubleshooting

If you encounter any issues:

1. Check the action logs in the "Actions" tab of your repository.
2. Ensure your `.fvmrc` file is correctly formatted and contains the necessary information.
3. Verify that all Flutter dependencies are correctly specified in your `pubspec.yaml` file.
4. If you're using code generation, make sure all necessary files are committed to the repository.