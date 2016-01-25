# `how-to-git`

### <a name="setup"></a>Setup:
  1. Fork the main [CodeNetworkTV][codenetwork] repository on [Github.com][codenetwork].
  2. Clone your fork of the repository: `git clone https://github.com/YourUsername/CodeNetworkTV.git`
  3. Add `upstream` remote repository: `git remote add upstream https://github.com/codenetwork/CodeNetworkTV.git`

### <a name="sync"></a>Sync changes made to `upstream`:
  1. Fetch any changes to `upstream`: `git fetch upstream`
  2. Checkout `master`: `git checkout master`
  3. Then rebase onto the `upstream/master`: `git rebase upstream/master`

### <a name="changes"></a>Making changes:
  1. Create a branch off `origin/master` (make sure it is [up-to-date][sync]): `git checkout master && git checkout -b <branch-name>`
  2. Commit changes on `<branch-name>`: `git add <appropriate files> && git commit -m "Put commit message here."`
  3. Push `<branch-name>` to hosted repo: `git push origin <branch-name>`
  4. **BEFORE** merging the `<branch-name>` into your `master` branch, [sync your `master` with `upstream/master`][sync].
  5. Then do an interactive rebase of your `<branch-name>` branch onto `master`, now that it is up-to-date: `git rebase -i master`
  6. The interactive rebase will open a text editor with all your commits. Please squash **all** your commits into one and change the commit message to reflect the overall changes that have been made.

```
pick fda59df commit 1
pick x536897 commit 2
pick c01a668 commit 3
```

To squash your commits, change the word `pick` of all the commits after `commit 1` to squash:

```
pick fda59df commit 1
squash x536897 commit 2
squash c01a668 commit 3
```

  7. Checkout your `master` and merge in the `<branch-name>` branch: `git checkout master && git merge <branch-name>`
  8. Push your `master` branch: `git push origin master`
  8. Go to your fork of the CodeNetworkTV repository (https://github.com/YourUsername/CodeNetworkTV), make sure you are on your `master` branch, and click the `New Pull Request` button.
  9. If there are issues or improvements that need to be made to your pull request follow [Making Changes][changes] from step 2.

[codenetwork]: https://github.com/codenetwork/CodeNetworkTV
[setup]: #setup
[sync]: #sync
[changes]: #changes