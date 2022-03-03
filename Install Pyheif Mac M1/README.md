# Install Pyheif on Mac M1

References:
- [Pyheif](https://github.com/carsales/pyheif)
- [Solution from gavinsoe](https://github.com/carsales/pyheif/issues/41#issuecomment-1035915825)
- [Run Terminal with Rosetta](https://osxdaily.com/2020/11/18/how-run-homebrew-x86-terminal-apple-silicon-mac/)
- [Install Brew x86 on Mac M1](https://stackoverflow.com/a/64997047)

# Solution

- Run Terminal with Rosetta:
  - Locate the Terminal application within the Utilities folder (Finder > Go menu > Utilities)
    Select Terminal.app and right-click on it, then choose `Duplicate`
  - Rename the duplicated Terminal app something obvious and distinct, like ‘Rosetta Terminal’
  - Now select the freshly renamed `Rosetta Terminal` app and right-click and choose `Get Info` (or hit `Command+I`)
  - Check the box for `Open using Rosetta`, then close the Get Info window
  - Run the `Rosetta Terminal` as usual, which will fully support Homebrew and other x86 command line apps
- Install Brew x86 on Mac M1:
  - Install Rosetta 2 Emulator:
  ```shell
  /usr/sbin/softwareupdate --install-rosetta --agree-to-license
  ```
  - Install Homebrew at `/usr/local`:
  ```shell
  arch -x86_64 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
  ```
  - **Optional:** Add custom command to `.zshrc`:
  Add this line to `~/.zshrc` (`nano ~/.zshrc`):
  ```
  alias brow='arch -x86_64 /usr/local/bin/brew'
  ```
  Next time you need to install x86 packages, you just need to use `brow install <package>` instead of `arch -x86_64 /usr/local/bin/brew`
- Install `libheif`:
  ```shell
  arch -x86_64 /usr/local/bin/brew install libheif  
  ```
  or
  ```shell
  brow install libheif  
  ```
- Install `pyheif`:
   ```shell
  pip install pyheif
  ```
   
# Hope you succeed in installing pyheif!
