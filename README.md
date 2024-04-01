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
        ```
    + Download [`Packer`](https://github.com/wbthomason/packer.nvim):
        ``` bash
        git clone --depth 1 https://github.com/wbthomason/packer.nvim\
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

## 4. Install bun

## 5. Install Java

## 6. Install Dotnet

## 7. Install C and C++ compiler

## 8. Install Rust

## 9. Install Flutter

## 10. Install Docker
