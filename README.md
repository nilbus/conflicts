Conflicts
=========

A curated set of merge conflicts from various open-source git repositories for conflict resolution practice.

When resolving confilcts in git, it's recommended to use diff3 (`git config --global conflictstyle.diff3`).
See the blog post [Take the pain out of git conflict resolution: use diff3][blog].

[blog]: https://blog.nilbus.com/take-the-pain-out-of-git-conflict-resolution-use-diff3/

<!-- Different, compatible changes made to the same/adjacent lines -->
<!-- ------------------------------------------------------------- -->

<!-- Lines added to the same location; you determine order -->
<!-- ----------------------------------------------------- -->

<!-- Changes with the same intent -->
<!-- ---------------------------- -->

<!-- Apply a branch's intent to lines that didn't exist in the common ancestor -->
<!-- ------------------------------------------------------------------------- -->

<!-- Code I changed isn't there any more (removed) -->
<!-- --------------------------------------------- -->

<!-- Code I changed isn't there any more (moved) -->
<!-- ------------------------------------------- -->

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
