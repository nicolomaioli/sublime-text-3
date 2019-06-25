# Install

Install Sublime, open it and install Package Manager. Follow the instructions for the appropriate operating system to clone the repo.

## Linux/Mac

Simply clone the repository to the appropriate folder:

```bash
git clone <REPO> $HOME/.config/sublime-text-3/Packages/User # Linux
git clone <REPO> $HOME/Library/Application\ Support/Sublime\ Text\ 3/Packages/User # Mac
```

## Windows + WSL

Open `.bashrc` and add the following:

```bash
# Windows WSL integration

win2lin () {
  # Convert Windows filepath to Linux prepending with /mnt/c
  f="${1/C://mnt/c}";
  printf '%s\n' "${f//\\//}";
}

# Get %userprofile% from CMD, convert it to a linux path and clean up printf
# This isn't a very clean solution, open to suggestions here
export WIN_HOME=`/mnt/c/Windows/System32/cmd.exe /C "echo %userprofile%"`
export WIN_HOME=`win2lin $WIN_HOME`
export WIN_HOME="${WIN_HOME%%[[:cntrl:]]}"
```

Save it, `source ~/.bashrc` then clone the repo:

```bash
git clone <REPO> $WIN_HOME/AppData/Roaming/Sublime\ Text\ 3/Packages/User
```

Add the following to `.bashrc` to open Sublime Text (or Sublime Merge) from WSL:

```bash
alias subl='"/mnt/c/Program Files/Sublime Text 3/subl.exe"'
alias smerge='"/mnt/c/Program Files/Sublime Merge/smerge.exe"'
```
