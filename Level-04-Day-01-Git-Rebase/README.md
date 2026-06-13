# ❤️ Level 04 - Day 01 - Git Rebase

---

### 💡 Complete Step-by-Step Execution Guide

Run these commands sequentially inside your current terminal session (`ssh natasha@ststor01`):

#### 🧑‍💻 1. Add the Safe Directory Exception for Root

Because you will be using `sudo`, Git will run under the root user profile. Tell Git that root trusts this directory:

```bash
sudo git config --global --add safe.directory /usr/src/kodekloudrepos/cluster

```

#### 🧑‍💻 2. Fetch the Latest Remote Changes

Update the local repository tracking branches with the central repository (`origin`):

```bash
sudo git fetch origin

```

#### 🧑‍💻 3. Update the Local Master Branch

Switch to the `master` branch and pull down the latest commits pushed by the other developers:

```bash
sudo git checkout master
sudo git pull origin master

```

#### 🧑‍💻 4. Switch Back to the Feature Branch

Based on your `git branch -a` output, the developer's branch is named exactly `feature`. Switch back to it:

```bash
sudo git checkout feature

```

#### 🧑‍💻 5. Rebase the Feature Branch onto Master

This applies the new `master` changes to the `feature` branch cleanly, positioning the developer's in-progress work directly on top of the fresh master commits without creating an ugly merge commit:

```bash
sudo git rebase master

```

*(If Git alerts you to any merge conflicts, open the specified files, fix the conflicts, run `sudo git add <file>`, and then run `sudo git rebase --continue`).*

#### 🧑‍💻 6. Force-Push the Rebased Branch to Origin

Because rebasing modifies the commit history, a normal push will be rejected. Force-push the changes to finish the task:

```bash
sudo git push origin feature --force

```

---

### 💡 How to Verify Your Success

To confirm that the branch has been successfully rebased and has a clean, linear history, run:

```bash
sudo git log --oneline --graph -n 10

```

You should see the commits from the `master` branch cleanly aligned underneath the `feature` branch commits, with no "Merge branch 'master' into feature" commit logs visible.
