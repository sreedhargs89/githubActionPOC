# PR Comment Checker Workflow

This repository contains a GitHub Actions workflow that automatically checks pull request comments for a specific string. If the string is not found in the comments, the workflow will create a new comment on the pull request.

## Workflow Overview

The workflow performs the following actions:

1. **Get PR Comments:** When a pull request is opened or when a comment is created/edited on the pull request, the workflow retrieves the comments made by the `github-actions[bot]` user. It then checks if the specific string exists in these comments.

2. **Create Comment:** If the specific string is not found in the comments, the workflow proceeds to create a new comment on the pull request. The comment's content can be customized in the workflow file.

## Trigger Events

The workflow is triggered by the following events:

- Pull request opened
- Pull request edited
- Pull request comment created
- Pull request comment edited

## Prerequisites

To use this workflow, you need appropriate permissions to access pull requests and add comments to the repository.

## How to Use

1. Copy the contents of the `.github/workflows/pr_comment_checker.yml` file from this repository into your repository's `.github/workflows` directory.

2. The workflow uses the default GitHub token (`${{ secrets.GITHUB_TOKEN }}`) for authentication, which has the necessary permissions for accessing pull requests and adding comments. There is no need to set up additional secrets.

3. Customize the specific string you want to check for in the workflow file. Look for the line `if echo "$COMMENTS" | grep -q "specific string"; then` and replace `"specific string"` with the string you want to check for.

4. Customize the comment's content that will be added if the specific string is not found. Look for the `COMMENT="This is the comment to be added."` line and modify the content within the double quotes.

5. Once the workflow is set up, it will automatically check for the specific string in pull request comments and create a new comment if the string is not present.

## Note

- Make sure to adjust the specific string and the comment content in the workflow file according to your specific use case.

- You can also further customize the workflow to perform other actions based on the presence or absence of the specific string, such as sending notifications or performing additional checks.

- This explanation assumes you have a basic understanding of GitHub Actions and workflows. If you are new to GitHub Actions, consider checking out the official documentation for more information: [GitHub Actions Documentation](https://docs.github.com/en/actions)
