# Cebola-devdocs
Developer documentation for Cebola Project

## How to run the site localy?

### 1. Install all dependences

1.0 Clone the repo:
  ```bash
  git clone https://github.com/novAIcariusQ/Cebola-devdocs
  ```

#### Option A: use [devbox](https://github.com/jetify-com/devbox)

1.1 [Install devbox](https://www.jetify.com/docs/devbox/installing-devbox#linux):
  - If you are on NixOS:
  ```bash
  nix-shell -p devbox
  ```
  - If you are on any other Linux distro:
  ```bash
  curl -fsSL https://get.jetify.com/devbox | bash
  ```
  - If you are on Windows:
  Install WSL and then run the script above.

1.2 Enter environment:
  ```bash
  devbox shell
  ```

1.3 Install gems:
  ```bash
  bundle install
  ```

#### Option B: manual install

1.1 Install all jekyll [prerequisites](https://jekyllrb.com/docs/installation/#requirements) for your system

1.2 Install gems:
  ```bash
  bundle install
  ```

### 2. Start the server

```bash
bundle exec jekyll serve
```
