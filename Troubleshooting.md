# Troubleshooting

Sometimes things don't go exactly right.  Here are some tips for basic troubleshooting:

* First, try running with the environment variable `GIT_TRACE` set to 1 (e.g. `GIT_TRACE=1 git push origin master`).  This can often show what's going on under the hood.
* Check that the remote place you're pushing to or pulling from is actually running a Git LFS server.  Git upstream doesn't provide one, so see the [[Implementations]] page if you need to find one.
* With the `GIT_TRACE` output, try to determine if the problem is on the client side (with the `git lfs` command itself) or on the server side.
* If the error message you're receiving says `batch response` or `remote`, that message comes from the server.  See the server-side troubleshooting below.

## Client-Side Issues

* Check that you've run `git lfs install` or `git lfs install --skip-repo` to set up your Git configuration to use Git LFS.  Without this step, Git LFS won't work.  There isn't a way to do this automatically for users without changing the system-wide configuration file (usually `/etc/gitconfig`).
* Check that the output of running `git lfs env` produces what you think it should produce.  The `git config` entries at the bottom should contain non-empty values; if they are empty, run `git lfs install`.  Similarly, the endpoint URLs should point to the server you think they should, and the entries starting with _Access_ should reflect the type of authentication you're using (`basic`, for most username-and-password or token authentication).
* If you get a message that says `'lfs' is not a git command`, see the [[Installation]] page for steps on how to make sure it's installed properly.

## Server-Side Issues

* If you're seeing a message that Git LFS is disabled, check to see if Git LFS is enabled for your repository on the server side.  Some server implementations require that the repository be specifically enabled for Git LFS.
* If you're using GitHub for hosting and you see a message that Git LFS is disabled or that you're over quota (or another server-side issue), please see the [documentation for GitHub](https://help.github.com/) (look for "large file") or [open a support ticket](https://github.com/contact) to get help with your account.