# gitFW-checkout-failed-issue-urlfolder
For the purpose of reporting issue relating to Git For Windows relating to URL folder names.

## How to reproduce
From [WSL 2](https://docs.microsoft.com/en-us/windows/wsl/install-win10) [Ubuntu 20.04](https://www.microsoft.com/en-us/p/ubuntu-2004-lts/9n6svws3rx71?atc=true&rtc=1&activetab=pivot:overviewtab)
- `mkdir newrepo`
- `cd newrepo`
- `git init`
- `curl https://wikipedia.com -L --create-dirs -o "https://wikipedia.com/mon.html"`

From Windows PowerShell, or any other programs that uses Git for Windows (as of version `2.28.0.windows.1`).
- `git clone`
- **Checkout failed**

This behavior was initially discovered when I was in [GitKraken](https://www.gitkraken.com/) and repeated the behavior on CLI git-scm
