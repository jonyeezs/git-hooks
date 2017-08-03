# GIT-HOOKS

Useful [hooks](https://www.atlassian.com/git/tutorials/git-hooks) in for your git pipeline

## How To Use

### Installation

`git clone https://github.com/jonyeezs/git-hooks.git`

### On a new git project

`cp -R {dir-of-git-hooks}\{language-specific-hook-folder-in-git-hooks}\ {dir-of-your-git-project}\.git\hooks\`

### Copy specific file to your git project hooks folder

`cp {dir-of-git-hooks}\{language-specific-hook-folder-in-git-hooks}\post-merge {dir-of-your-git-project}\.git\hooks\`


## Goals

1. Save devs from forgetting to DoD their code before pushing to remote.
  * The DOD:
    1. Do not leave debug code scattered.
    2. Make sure test passes every time new code is hacked
    3. Ensure housekeeping is done when possible. ie syncing package versions.

### Reasons which hook process to use

* post-merge
  * Only operate housekeeping where environmental state has changed between your local and remote
  * Operations that you only need to do once during a merge, rebase, or a pull
* pre-commit
  * Code clean-ups, linting, etc.
  * Low-fi operations that don't take too much processing
  * You don't want a heavy process like running all your test that could take more than 2 seconds
  * Commits should be done quick
* pre-push
  * Runs important process that would not make your commit unusable or broken
  * Good where you need to run long processes
  * Best time to run your test or notifications