- [Syncing a fork from the command line](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork)
	- 1. Fork the repository
	  2. Add the upstream to the repository 
	  `$ git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git`
	  3. Fetch the branches and their respective commits from the upstream repository. Commits to BRANCHNAME will be stored in the local branch upstream/BRANCHNAME. 
	  ```bash
	  $ git fetch upstream
	  > remote: Counting objects: 75, done.
	  > remote: Compressing objects: 100% (53/53), done.
	  > remote: Total 62 (delta 27), reused 44 (delta 9)
	  > Unpacking objects: 100% (62/62), done.
	  > From https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY
	  >  * [new branch]      main     -> upstream/main
	  ```
	  4. Check out your fork's local default branch - in this case, we use main.
	  ```bash
	  $ git checkout main
	  > Switched to branch 'main'
	  ```
	  5. Merge the changes from the upstream default branch - in this case, upstream/main - into your local default branch. This brings your fork's default branch into sync with the upstream repository, without losing your local changes.
	  ```bash
	  $ git merge upstream/main
	  > Updating a422352..5fdff0f
	  > Fast-forward
	  >  README                    |    9 -------
	  >  README.md                 |    7 ++++++
	  >  2 files changed, 7 insertions(+), 9 deletions(-)
	  >  delete mode 100644 README
	  >  create mode 100644 README.md
	  ```
	  If your local branch didn't have any unique commits, Git will instead perform a "fast-forward":
	  ```bash
	  $ git merge upstream/main
	  > Updating 34e91da..16c56ad
	  > Fast-forward
	  >  README.md                 |    5 +++--
	  >  1 file changed, 3 insertions(+), 2 deletions(-)
	  ```
	-
- Checking out an individual branch from a remote
  id:: 626064f7-e8c2-47a9-a645-9f5edb63a9a3
	- Fetch the upstream or <remote> to have everything up to date.
		- `git fetch upstream`
	- List all the branches
		- `git branch -v -a`
	- Switch to the desired branch
		- `git switch -c <name_local_branch> <desired_branch>`