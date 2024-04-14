# Development environment setup on ubuntu 20.04

First of all, update package list using: 
``` bash
sudo apt update
```

## 1. Install git and gh cli
  - Install git:
    ``` bash
    sudo apt install git
    ```
  - Install gh cli:
      ``` bash
      sudo mkdir -p -m 755 /etc/apt/keyrings && wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
      && sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
      && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
      && sudo apt update \
      && sudo apt install gh -y
      ```
  - After gh cli installed, login to gh using:
    ``` bash
    gh auth login
    ```
## 2. Install Neovim
  - Download the latest version for linux and extract to `/opt` directory by running:
    ``` bash
    curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux64.tar.gz
    sudo rm -rf /opt/nvim
    sudo tar -C /opt -xzf nvim-linux64.tar.gz
    ```
> **Note**
> - `/opt` directory is optional, other directories work fine but make sure those directories can be accessed by `bash`.
> - Ensure `curl` is installed. If not, install it by running:
>   ``` bash
>   sudo apt install curl
>   ```
  - Add this to `~/.bashrc` to enable `nvim` command:
    ```  bash
    export VIM_INSTALL="/opt/nvim-linux64"
    export PATH=$VIM_INSTALL/bin:$PATH
    ```
  - Configure neovim's plugins and key maps:
    + Clone neovim's setup:
        ``` bash
        git clone https://github.com/duykasama/nvim-config ~/.config/nvim
        cd ~/.config/nvim
        git checkout ubuntu
        ```
    + Download [`Packer`](https://github.com/wbthomason/packer.nvim):
        ``` bash
        git clone --depth 1 https://github.com/wbthomason/packer.nvim \
        ~/.local/share/nvim/site/pack/packer/start/packer.nvim
        ```
    + Install plugins:
        ``` bash
        nvim ~/.config/nvim/lua/duykasama/packer.lua
        ```
        ``` bash
        :so
        :PackerSync
        ```
## 3. Install Node.js
  - Installs `NVM` and `Node.js` version 20:
    ``` bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
    source ~/.bashrc
    nvm install 20
    ```
## 4. Install bun
  ``` bash
  npm i -g bun
  ```
## 5. Install Java
  - Download desired version [here](https://www.oracle.com/java/technologies/downloads/).
  - Extract downloaded archive:
    ``` bash
    tar -zxvf ~/Downloads/{file-name} -C ~/Environments/Java
    ```
  - Add this to `~/.bashrc`:
    ``` bash
    export JAVA_HOME="$HOME/Environments/Java/{extracted-directory}"
    export PATH=$JAVA_HOME/bin:$PATH
    ```
  - Download `maven` [here](https://maven.apache.org/download.cgi/).
  - Extract downloaded archive:
    ``` bash
    tar -zxvf ~/Downloads/{file-name} -C ~/Environments/Java
    ```
  - Add this to `~/.bashrc`:
    ``` bash
    export MAVEN_HOME="$HOME/Environments/Java/{extracted-directory}"
    export PATH=$MAVEN_HOME/bin:$PATH
    ```
## 6. Install Dotnet
  - Download installation script:
    ``` bash
    wget https://dot.net/v1/dotnet-install.sh -O ~/Environments/Dotnet/dotnet-install.sh
    ```
  - Grant permission for the script:
    ``` bash
    chmod +x ~/Environments/Dotnet/dotnet-install.sh
    ```
  - Run installation script:
    ``` bash
    ~/Environments/Dotnet/dotnet-install.sh --version latest
    ```
      > **Notes**
      > - Replace `latest` with the desired version.
  - Add this to `~/.bashrc`:
    ``` bash
    export DOTNET_HOME="$HOME/Environments/Dotnet/.dotnet"
    export PATH=$DOTNET_HOME:$PATH
    ```
## 7. Install C and C++ compiler
  ``` bash
  sudo apt install build-essential
  ```
## 8. Install Rust
  ``` bash
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
  ```
## 9. Install Android Studio
  - Download `Android Studio` [here](https://developer.android.com/studio).
  - Extract downloaded archive:
    ``` bash
    tar -zxvf ~/Downloads/{file-name} -C ~/Environments/AndroidStudio
    ```
  - After installing `Android Studio`, open `Sdk Manager` and install the following `tools`:
    + Ndk (Side by side)
    + Android SDK Command-line Tools
    + CMake
    + Android SDK Platform-Tools
  - Add this to `~/.bashrc`:
    ``` bash
    # android home
    export ANDROID_HOME="$HOME/Android/Sdk"
    export PATH=$ANDROID_HOME:$PATH

    # ndk home
    export NDK_HOME="$ANDROID_HOME/ndk/{ndk-version}"
    export PATH=$NDK_HOME:$PATH
    ```
## 10. Install Flutter
  - Install required packages:
    ``` bash
    sudo apt-get update -y && sudo apt-get upgrade -y;
    sudo apt-get install -y curl git unzip xz-utils zip libglu1-mesa
    ```
  - Install prequisite packages for Android Studio:
    ``` bash
    sudo apt-get install \
    libc6:i386 libncurses5:i386 \
    libstdc++6:i386 lib32z1 \
    libbz2-1.0:i386
    ```
  - Install `Flutter`:
    ``` bash
    sudo snap install flutter
    ```        
## 11. Install Docker
## 12. Install Tmux
## 13. Install netcoredbg
## 14. Install Postman
