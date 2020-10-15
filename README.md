# gitFW-checkout-failed-issue-urlfolder
For the purpose of reporting issue relating to Git For Windows relating to URL folder names.

## How to reproduce
From [WSL 2](https://docs.microsoft.com/en-us/windows/wsl/install-win10) [Ubuntu 20.04](https://www.microsoft.com/en-us/p/ubuntu-2004-lts/9n6svws3rx71?atc=true&rtc=1&activetab=pivot:overviewtab)
```
mkdir newrepo
cd newrepo
git init
curl https://wikipedia.com -L --create-dirs -o "https://wikipedia.com/mon.html"
```

From Windows PowerShell, or any other programs that uses Git for Windows (as of version `2.28.0.windows.1`).
- `git clone`
- **Checkout failed**
See [Appendix 1](https://github.com/kaovilai/gitFW-checkout-failed-issue-urlfolder#Appendix-1)
This behavior was initially discovered when I was in [GitKraken](https://www.gitkraken.com/) and repeated the behavior on CLI git-scm

### Other issues
[https/wikipedia.com](https://github.com/kaovilai/gitFW-checkout-failed-issue-urlfolder/tree/main/https%EF%80%BA/wikipedia.com) was commited from a Windows machine. It does not appear that `git version 2.25.1` for Ubuntu is able to clone this folder as `ls` show it is missing. See [Appendix 2](https://github.com/kaovilai/gitFW-checkout-failed-issue-urlfolder#Appendix-2)

#### Appendix 1
```
git clone https://github.com/kaovilai/gitFW-checkout-failed-issue-urlfolder/ test
Cloning into 'test'...
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 8 (delta 1), reused 8 (delta 1), pack-reused 0
Unpacking objects: 100% (8/8), 19.06 KiB | 591.00 KiB/s, done.
error: invalid path 'https:/wikipedia.com/mon.html'
fatal: unable to checkout working tree
warning: Clone succeeded, but checkout failed.
You can inspect what was checked out with 'git status'
and retry with 'git restore --source=HEAD :/'
```

#### Appendix 2
WSL2 Ubuntu 20.04 not showing file commited from Windows
```
$ git log
commit 09997cdce1e50ddd25c454f7ec9636469ac31427 (HEAD -> main, origin/main)
Author: Tiger Kaovilai <passawit.kaovilai@gmail.com>
Date:   Wed Oct 14 21:27:59 2020 -0400

    Create README.md

commit cddc92978766f1ef8936eebe86c8b241a1d5784d
Author: Passawit Kaovilai <passawit.kaovilai@gmail.com>
Date:   Wed Oct 14 21:17:29 2020 -0400

    httpscolon test from WSL 2 Ubuntu 20.04

commit b3302f662988eff67fa0f385a7ed8b71b963d0f5
Author: Passawit Kaovilai <passawit.kaovilai@gmail.com>
Date:   Wed Oct 14 21:15:38 2020 -0400

    httpscolon test

commit d5837617e29a79a95e40443a6c5c9e94a64759a1
Author: Passawit Kaovilai <passawit.kaovilai@gmail.com>
Date:   Wed Oct 14 21:10:30 2020 -0400

    testWithoutHTTPColon
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
$ ls -a
.  ..  .git  README.md  https:  wikipedia.com
$
```
