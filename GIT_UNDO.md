### HEAD in Git

Sometme you will see the Git documentation saying something about **HEAD**. For example:

The branch must be fully merged in HEAD.s

But what exactly is Git **HEAD**?

### Answer

**HEAD** is a reference to the last commit in the currently check-out branch.

You can think of the **HEAD** as the "current branch". When you switch branches with git checkout, the HEAD revision changes to point to the tip of the new branch.

You can see what **HEAD** points to by doing:

`cat .git/HEAD`

For example, in my current branch it shows:

`$ cat .git/HEAD`

`ref: refs/heads/master`

It is possible for HEAD to refer to a specific revision that is not associated with a branch name. This situation is called a [detached HEAD](https://git-scm.com/docs/git-checkout#_detached_head "detached HEAD").
