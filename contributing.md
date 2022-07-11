* Go to the GitHub page of the repo to contribute to.
* Read the README.md file
* Read the contributing.md file, if available.
* Read the code of conduct, if available.
* Go to the issues tab on the repo
* Find a `good first issue` if possible.
* Click on the issue of your choice and read it, optionally asking a question or leave a comment.

### Now, to contribute:
* Fork the repository in GitHub
* Click fork in the top right
* Choose the account to fork into, if applicable.
* You will then see the repo under your GitHub account directory, eg. mrwillett/<repo just forked>
* Clone the repo using ssh by clicking `clone` and copying the URL
* Open terminal and cd to your desired directory, eg. ~/open_source
* Clone the forked repo copied form above by typing: `git clone [url copied above]`
* Go back into the contributing guide before making any edits.
* Make a new branch off of the main or master branch of the repo you just forked
* cd into the repo
* optionally type `ls` to list the content of the repo
* type `git branch` which will show what branch you’re currently on (at this stage it will be the main branch)
* type `git branch [new branch name]` to create a different branch
* type `git checkout [new branch name]` to switch the branch to the new branch
* optionally, use git checkout -b <branchname> to do (d) and (e) in one step.
* everything in the new branch links back to master, meaning if you type git pull, you will pull from master and get the most updated version based on master.
* Once in the new branch, open your IDE of choice and make the edits
* After making changes, refer to contributing guidelines for steps that must be taken to get your code ready to be contributed to master (varies)
* Type `git diff` to see the changes you just made
* Ensure no changes have been made to master in the time you contributed:
* Switch back to the master branch by typing `git checkout master`
* Type` git pull` to see if any changes have been made to the source while you made your changes. If so, make your changes again, if necessary.
* Switch branch back to your new branch
* Git pull in the new branch
* If necessary, clarify with `git branch –set-upstream-to=origin/<branch (master)> [new branch name]` which might be suggested as the second option.
* This will sync your new branch with master
* Type `git add .` to add all the files in the repo
* Type `git commit -m ‘[message of the changes made]’
* Type `git push` to push the changes to the repo
* If it’s your first commit, you’re likely to get a message asking:
* Choose the second option `git push origin [new branch name]`
* or ‘git push origin HEAD’
* Return to GitHub
* You should see your pushed branch in your forked version of the repo
* Click `compare and pull request`
* base reposity: the main repo
* base: the main branch, such as ‘master’
* head repository (where the changes are coming from, ie. Your fork of the repo)
* compare: [your branch name]
* again, refer to the contributing guidelines
* leave a comment describing the changes made
* click `create pull request` and your PR is live!
* Wait for feedback from reviewers
* If you need to make edits:
* Go back to local directory and your branch in terminal
* Make the changes,
* Repeat the pull from master to check that everything is up to date on master an no further changes have been made
* Add, commit, push the changes to the pull request

Other notes:
* You should only have 1 pull request per branch, if you want to make separate contributions, create a new branch off of master again.
* See the naming conventions for branches
* The `head` branch is the branch you are making changes in. the `base` branch is the branch off of which the head is based. Ie. A fork of the base branch that is already or is to be modified, is the head branch.
 



The very helpful video this guide was based on:
https://www.youtube.com/watch?v=c6b6B9oN4Vg


### Notes on not forking a repo for every contribution:
Don't refork a GitHub repository every time you want to contribute
Written on 14 July 2019

Sometimes people contribute to one of my projects, and every time that they want to contribute, they delete their fork and fork the project again.

They usually do this because they don't know how to easily get an up-to-date master branch again. Since it's much easier to just hit "delete" and "fork" again, that's what they do instead.

However, this problem usually occurs when people start working on the `master` branch instead of a branch specifically made for their PR.

So the next time you want to work on a fork of some project with the intent to contribute your changes via a PR, do the following instead:
```
# Clone your fork
git clone git@github.com:/you/project
# Add the original repository as a new remote
git remote add original https://github.com/someone/project
# Now you'll have the remotes "origin" (fork) and "original" (original)
# We assume that your current master branch has no exclusive changes
# Now update your master using the originals masters state
git pull original master
# Now that you have an up-to-date master, create a new branch of that
git checkout -b your_new_feature
# This creates a new branch called `your_new_feature` and checks it out
# Now start implementing your feature and commit the changes.
# When you are done, push your changes to the fork
git push --all origin
# --all will push all branches to the remote
# Now create your PR via GitHub. As soon as it gets accepted into
# master, you can repeat the same procedure starting at
# `git pull original master`
```

This way you won't have to worry about both remotes having different commits, merge commits or whatever, since all your changes happen on a throwaway branch anyway.

In case you already have a poluted master branch, you can do the following:

```
# Check the originals master out
git checkout original/master
# This will bring you into a "Detached HEAD" state, meaning you aren't on a
# branch, but on a specific commit you could say.
# Now delete master locally
git branch -D master
# After deleting master, we use our current state to recreate it
git checkout -b master
# Now we'll locally have an up-to-date master
# Now we push, but we need to apply `--force`, since our commit will delete commits that already exist upstream.
git push --force
```

found at: https://marcelschr.me/articles/do-not-refork-a-project-every-time-you-contribute.html

