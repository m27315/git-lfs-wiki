This page lists common issues and feature requests:

- GitHub currently enforces a 2 GiB size limit per-object.
- Windows client corrupts files > 4Gb ([#2434](https://github.com/git-lfs/git-lfs/issues/2434))
- Windows client must have Git Credential Manager installed/and in-use or operations may hang indefinitely ([#1763](https://github.com/git-lfs/git-lfs/issues/1763))
- GitLab currently (as of 11.7.3 CE) has a hard coded timeout for the git-lfs-authenticate token of
30 minutes. GitLab also lacks support for the **expires_in** or **expires_at** properties which would
mitigate this issue. See closed issue: ([#3012](https://github.com/git-lfs/git-lfs/issues/3012))
[comment](https://github.com/git-lfs/git-lfs/issues/3012#issuecomment-390800554).
Update: a fix was introduced in 11.9 to include the **expires_in** property. See ([#57353](https://gitlab.com/gitlab-org/gitlab-ce/issues/57353)) for details.