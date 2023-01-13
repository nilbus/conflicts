Conflicts Playground
====================

This is a curated set of merge conflicts from various open-source git repositories for conflict resolution practice. This repository includes the git commits from several open-source projects. None are merged into the master branch, but you can access the code and reproduce each conflict by cloning this repository and using the git commands given in the examples below.

When resolving conflicts in git, it's recommended to use diff3.
See the blog post [Take the pain out of git conflict resolution: use diff3][blog].

[blog]: https://blog.nilbus.com/take-the-pain-out-of-git-conflict-resolution-use-diff3/

Steps to reproduce a conflict
=============================

After cloning this repository,

1. Ensure your working directory is clean.

        git reset --hard; git clean -df

2. Check out first parent (`^1`) of the merge commit. This is the commit that was checked out when the merge originally happened.

        git checkout <merge_commit>^1

3. Merge the commit that was originally merged, the second parent (`^2`).

        git merge <merge_commit>^2

4. Resolve the conflict, and commit the result.

5. Compare your result to the original merge result to yours (differences in your resolution are prefixed with `+`). Keep in mind that the author may not have resolved the conflict correctly.

        git diff <merge_commit>


Tips
====

Enable diff3

    git config --global conflictstyle.diff3

View the left side of the merge, what was checked out (HEAD / ours, always the top conflict section):

    git diff <merge_commit>^2...<merge_commit>^1 [file_paths...]

View the right side of the merge, what was merged (MERGE_HEAD / theirs, always the bottom conflict section):

    git diff <merge_commit>^1...<merge_commit>^2 [file_paths...]

----------------------------------------------------------------------------------------------------------------


Basic conflict examples
=======================

Different, compatible changes made to the same/adjacent lines (small)
---------------------------------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout rails.a^1
    git merge rails.a^2

Commit, then check your work:

    git diff rails.a

Different, compatible changes made to the same/adjacent lines (medium)
----------------------------------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout pry.a^1
    git merge pry.a^2

Commit, then check your work:

    git diff pry.a

<!-- Lines added to the same location; you determine order -->
<!-- ----------------------------------------------------- -->

Changes with the same intent
----------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout pry.e^1
    git merge pry.e^2

Commit, then check your work:

    git diff pry.e

Since both branches approached solving the same problem in different ways, it's up to you as the merger to decide which to choose. Your solution may vary from the original merger's.


Conflicts requiring context beyond diff3 ancestor
=================================================

Code I changed isn't there any more, v1
---------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout pry.b^1
    git merge pry.b^2

Commit, then check your work:

    git diff pry.b

Code I changed isn't there any more, v2
---------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout guard.a^1
    git merge guard.a^2

Commit, then check your work:

    git diff guard.a

A changed file was deleted on the other merge parent
----------------------------------------------------

Note: "deleted by us" in `git status` refers not to authorship but rather which parent deleted.
- Ours / by us = 1st parent (`^1`)
- Theirs / by them = 2nd parent (`^2`)

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout docker-sync.a^1
    git merge docker-sync.a^2

Commit, then check your work:

    git diff docker-sync.a

You'll likely come up with a different resolution, but both could be considered correct!

There's also a semantic conflict resolved in the official resolution.


Semantic conflicts
==================

Apply a branch's intent to lines that didn't exist in the common ancestor
-------------------------------------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout pry.d^1
    git merge pry.d^2

Commit, then check your work:

    git diff pry.d

Both branches performed a similar refactoring
---------------------------------------------

**External repository**: doximity

_Be sure to first commit or stash any work in progress!_

Reproduce this conflict:

    git reset --hard
    git checkout 1e4e700cbee^1
    git merge 1e4e700cbee^2

Commit, then check your work:

    git diff 1e4e700cbee

Check out the branch you were on previously:

    git checkout -

<!-- A local variable I referenced was renamed -->
<!-- ----------------------------------------- -->

<!-- A distant method I called was refactored away / removed -->
<!-- ------------------------------------------------------- -->

<!-- A library I made a new use of was replaced with another -->
<!-- ------------------------------------------------------- -->

<!-- Rebase a merge, which results in conflicts -->
<!-- ------------------------------------------ -->


Reviewing conflict resolutions
==============================

<!-- Review a simple merge conflict resolution that was done correctly -->
<!-- ----------------------------------------------------------------- -->

Review a merge conflict resolution that was done incorrectly
------------------------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout pry.c^1
    git merge pry.c^2

Commit, then compare your solution with the original merge commit:

    git diff pry.c

Check your work against my corrected solution:

    git diff pry.c.corrected

<!-- We come up with a different resolution; both are correct -->
<!-- -------------------------------------------------------- -->

<!-- We come up with a different resolution; we discover a mistake in the pushed resolution -->
<!-- -------------------------------------------------------------------------------------- -->

<!-- Recovering from a bad merge -->
<!-- --------------------------- -->

<!-- Recovering from committed conflict markers -->
<!-- ------------------------------------------ -->


Intimidating conflicts
======================

Indentation level change
------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout expertiza.c^1
    git merge expertiza.c^2

For this exercise, focus only on the conflicting `.erb` files.

Easiest to check out file using --ours / --theirs, then apply the other change
------------------------------------------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout rails.b^1
    git merge rails.b^2

Commit, then compare your solution with the original merge commit:

    git diff rails.b

Check your work against my corrected solution:

    git diff rails.b.corrected

Massive size: Many adjacent hunks, and compared code seems unrelated
--------------------------------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout guard.b^1
    git merge guard.b^2

Commit, then check your work:

    git diff guard.b


DOS/UNIX line endings swapped unintentionally
---------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout expertiza.b^1
    git merge expertiza.b^2

<!-- Criss-cross merge scenario -->
<!-- -------------------------- -->
