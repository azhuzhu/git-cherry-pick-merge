Cherry picking merges in git
============================

This is a fairly simple script I use to cherry pick (simple) merges while
preserving the merge. Underneath it is using `git rebase --onto`.

It is very particular to the way I handle pull requests, so YMMV.

Usage: `git-cpm <merge-ref>`


Failures
--------

As I said the script is mostly just running rebase --onto. If the rebase
fails, the script will exit immediately. At that point you can either

1. manually fix the rebase, as with any other rebase
2. abort


### Fixing the rebase

If you want to fix the rebase, you can proceed with this as with any other
rebase. Once finished, simple run `git-cpm` again to resume the process
(it will still need to perform the actual merge commit).

### Aborting the process

If you'd rather just abort, run `git-cpm abort` and the script will do its
best to put you back where you were.

WARNING
-------

While I use this script all the time myself, there could easily be corner case
bugs. I have not extensively tested it against all git versions.


TIPS
----

* If you put this script in your path (I just symlink it under ~/bin), then
  git should be able to invoke it as `git cpm`.
* If you don't care about preserving the merge structure, then you might
  consider using something like `git cherry-pick -m1`
