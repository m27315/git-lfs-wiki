## Requirements ##

- `git >= 1.8.2`

## Installing ##

On all operating systems, once git-lfs is downloaded, `git lfs install` must be run. Each user that intends to use git lfs must run this command, but they only ever need to run it once. git-lfs can be disabled by running `git lfs uninstall`, in which case that user would have to run `git lfs install` again, before git-lfs features work again.

Some users may wish to only enable git-lfs on specific repositories instead of always having it on for all of the repositories. Instead of running `git lfs install` and enabling git-lfs for that entire user, `git lfs install --local` can be used instead on a per repository basis.

Note: If git-lfs is installed without `--local`, then `git lfs uninstall --local` would not disable it for a specific repository.

An additional option of `--skip-smudge` can be added to skip automatic downloading of objects on clone or pull. This requires a manual `git lfs pull` every time a new commit is checked out on your repository. This is more useful for cases where you don't always want to download/checkout every large file.

### Debian and Ubuntu ###

Ubuntu 18.04, Debian 10, and newer versions of those OSes offer a `git-lfs` package. If you'd like to use that and don't need the latest version, skip step 1 below.

1. `curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash`
2. `sudo apt-get install git-lfs`
3. `git lfs install`

### Mac OSX ###

1. You may need to `brew update` to get all the new formulas
2. `brew install git-lfs`
3. `git lfs install`

### RHEL/CentOS ###

1. Install git >= 1.8.2

    - Recommended method for RHEL/CentOS 5 and 7 (not 6!)

        1. Install the epel repo [link](https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F) (For CentOS it's just `sudo yum install epel-release`)
        2. `sudo yum install git`

    - Recommended method for RHEL/CentOS 6

        1. Install the IUS Community repo. `curl -s https://setup.ius.io/ | sudo bash` or [here](https://ius.io/GettingStarted/)
        2. `sudo yum install git2u`

    - You can also build git from source and install it. If you do that, you will need to either manually download the git-lfs rpm and install it with `rpm -i --nodeps git-lfs*.rpm`, or just use the [Other](#Other) instructions. The only other advanced way to fool yum is to create and install a fake/real git rpm to satisfy the git >= 1.8.2 requirement.

2. To install the git-lfs repo, run `curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.rpm.sh | sudo bash` from [here](https://packagecloud.io/github/git-lfs/install)
3. `sudo yum install git-lfs`
4. `git lfs install`

### Windows ###

1. Download the windows installer from [here](https://github.com/git-lfs/git-lfs/releases)
2. Run the windows installer
3. Start a command prompt/or git for windows prompt and run `git lfs install`

### Docker Recipes ###

For Debian Distros, you can use

```dockerfile
RUN build_deps="curl" && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends ${build_deps} ca-certificates && \
    curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | bash && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends git-lfs && \
    git lfs install && \
    DEBIAN_FRONTEND=noninteractive apt-get purge -y --auto-remove ${build_deps} && \
    rm -r /var/lib/apt/lists/*
```

## Other ##

To install on any supported operating system, manually install git-lfs with no man pages.

Only one file is required for git-lfs, the `git-lfs` binary. i386 and x86_64 versions are available [here](https://github.com/git-lfs/git-lfs/releases) for FreeBSD, Linux, Mac and Windows. Currently, linux arm6 must be compiled from source

1. Install git version 1.8.2 or newer
2. Download and put the git-lfs (.exe for windows) in your path, and `git lfs` commands start working, as long as both git and git-lfs are in your path.

## Source ##

1. Ensure that you have a reasonably modern version of [Go](https://golang.org).
2. If you are using Windows, build `goversioninfo` (e.g., with `go get github.com/josephspurrier/goversioninfo/cmd/goversioninfo`) and place the binary in your PATH.
3. Obtain a copy of the repository, either with `git clone` (into the appropriate location within your `$GOPATH`), or with `go get`, i.e., `go get github.com/git-lfs/git-lfs`.
4. In your copy of the source, execute `make` to ensure that you are able to build a fresh copy of Git LFS. If successful, the binary will appear in `bin/git-lfs`.
