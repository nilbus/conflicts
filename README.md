A curated set of merge conflicts from various open-source git repositories for conflict resolution practice.

When resolving conflicts in git, it's recommended to use diff3.
See the blog post [Take the pain out of git conflict resolution: use diff3][blog].

[blog]: https://blog.nilbus.com/take-the-pain-out-of-git-conflict-resolution-use-diff3/

Steps to reproduce a conflict
=============================

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

Conflict examples
=================

Different, compatible changes made to the same/adjacent lines
-------------------------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout guard.1^1
    git merge guard.1^2

Commit, then check your work:

    git diff guard.1

<!-- Lines added to the same location; you determine order -->
<!-- ----------------------------------------------------- -->

<!-- Changes with the same intent -->
<!-- ---------------------------- -->

<!-- Apply a branch's intent to lines that didn't exist in the common ancestor -->
<!-- ------------------------------------------------------------------------- -->

<!-- Code I changed isn't there any more (removed) -->
<!-- --------------------------------------------- -->

Code I changed isn't there any more (moved)
-------------------------------------------

Reproduce this conflict:

    git reset --hard; git clean -df
    git checkout guard.2^1
    git merge guard.2^2

Commit, then check your work:

    git diff guard.2

<!-- A changed file was deleted on the other merge parent -->
<!-- ---------------------------------------------------- -->

<!-- A local variable I referenced was renamed -->
<!-- ----------------------------------------- -->

<!-- A distant method I called was refactored away / removed -->
<!-- ------------------------------------------------------- -->

<!-- A library I made a new use of was replaced with another -->
<!-- ------------------------------------------------------- -->

<!-- Rebase a merge, which results in conflicts -->
<!-- ------------------------------------------ -->

<!-- Review a simple merge conflict resolution that was done correctly -->
<!-- ----------------------------------------------------------------- -->

<!-- Indentation level change -->
<!-- ------------------------ -->

<!-- Review a merge conflict resolution that was done incorrectly -->
<!-- ------------------------------------------------------------ -->

<!-- We come up with a different resolution; both are correct -->
<!-- -------------------------------------------------------- -->

<!-- We come up with a different resolution; we discover a mistake in the pushed resolution -->
<!-- -------------------------------------------------------------------------------------- -->

<!-- Massive size: Many adjacent hunks, and compared code seems unrelated -->
<!-- -------------------------------------------------------------------- -->

<!-- DOS/UNIX line endings swapped unintentionally -->
<!-- --------------------------------------------- -->

<!-- Criss-cross merge scenario -->
<!-- -------------------------- -->

<!-- Recovering from a bad merge -->
<!-- --------------------------- -->

<!-- Recovering from committed conflict markers -->
<!-- ------------------------------------------ -->

<!-- Easiest to check out file using --ours / --theirs, then apply the other change -->
<!-- ------------------------------------------------------------------------------ -->
