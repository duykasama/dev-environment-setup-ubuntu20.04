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

## 3. Install Node.js

## 4. Install bun

## 5. Install Java

## 6. Install Dotnet

## 7. Install C and C++ compiler

## 8. Install Rust

## 9. Install Flutter

## 10. Install Docker
