
# Lint Autofix CI Demo

A demo of a GitHub Actions setup that automatically fixes PRs of external contributors.

Using `pull_request_target` to elevate your permissions to push to a contributor's fork is **unsafe** according to [GitHub Security Labs best practices](https://securitylab.github.com/research/github-actions-preventing-pwn-requests/). 

For security reasons, the process is split in 2 workflows:
- a `pull_request` workflow that safely runs on the untrusted PR, and only generates a git diff patch
- a `workflow_run` workflow with elevated permissions that push the diff patch to the repository
