# 🚀 WSL Dev Setup Guide (Python + Node.js)  
_Cho FastAPI, NestJS, Next.js – optimized cho WSL2 + VS Code_

## 1️⃣ Cài đặt WSL & Ubuntu
1. Mở PowerShell (Admin):
   ```powershell
   wsl --install -d Ubuntu
   ```

2. Khởi động lại máy → mở Ubuntu lần đầu, đặt username & password.

---

## 2️⃣ One-time setup trong Ubuntu

### 2.1 Cập nhật hệ thống

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential git curl wget unzip pkg-config
```

### 2.2 Zsh + tiện ích

```bash
sudo apt install -y zsh
chsh -s $(which zsh)
```

### 2.3 Pyenv (Linux version, không dính pyenv-win)

```bash
sudo apt install -y \
  libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev \
  libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

curl https://pyenv.run | bash

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init --path)"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

### 2.4 UV (quản lý venv + deps Python)

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
```

### 2.5 Node (nvm + corepack)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.zshrc
echo '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"' >> ~/.zshrc
echo 'corepack enable >/dev/null 2>&1 || true' >> ~/.zshrc
```

### 2.6 Tăng file watcher cho hot reload

```bash
echo 'fs.inotify.max_user_watches=524288' | sudo tee /etc/sysctl.d/99-inotify.conf
echo 'fs.inotify.max_user_instances=1024' | sudo tee -a /etc/sysctl.d/99-inotify.conf
sudo sysctl --system
```

### 2.7 Git config

```bash
git config --global user.name "Nguyen Hoang Long"
git config --global user.email "nhl08.contact@gmail.com"
git config --global core.autocrlf input
git config --global init.defaultBranch main
```

---

## 3️⃣ Per-project setup

### 3.1 Python + FastAPI

```bash
pyenv install 3.11.9
pyenv local 3.11.9

uv venv
uv add fastapi "uvicorn[standard]" pydantic python-dotenv

uv run uvicorn app:app --reload --host 0.0.0.0 --port 8000
# Mở: http://localhost:8000
```

### 3.2 Node + NestJS

```bash
nvm install --lts
nvm use --lts
corepack enable
corepack prepare pnpm@latest --activate

pnpm dlx @nestjs/cli new server
cd server
pnpm start:dev   # bind 0.0.0.0 nếu muốn truy cập từ Windows
```

### 3.3 Node + Next.js

```bash
nvm use --lts
corepack enable
corepack prepare pnpm@latest --activate

pnpm dlx create-next-app@latest web
cd web
pnpm dev -- --host 0.0.0.0 --port 3000
# Mở: http://localhost:3000
```

---

## 4️⃣ VS Code Setup

### 4.1 Extensions

* Remote – WSL
* Python, Pylance
* Ruff hoặc Black (Python)
* ESLint, Prettier (JS/TS)
* Docker, GitLens, Thunder Client, Error Lens

### 4.2 settings.json (WSL workspace)

```json
{
  "terminal.integrated.defaultProfile.linux": "zsh",
  "files.eol": "\n",
  "editor.formatOnSave": true,
  "[python]": {
    "python.analysis.autoImportCompletions": true
  },
  "python.defaultInterpreterPath": "${workspaceFolder}/.venv/bin/python",
  "python.terminal.activateEnvironment": true,
  "eslint.validate": ["javascript","javascriptreact","typescript","typescriptreact"],
  "prettier.useTabs": false
}
```

---

## 5️⃣ Performance tips

* Luôn để project ở `~/code/...` trong WSL → nhanh hơn nhiều so với `/mnt/d/...`.
* Postgres chạy trên Windows vẫn connect từ WSL bằng `localhost:5432` (kiểm tra firewall + listen\_addresses).
* Dev server trong WSL nên bind `0.0.0.0` để Windows browser truy cập `localhost:<port>`.

---

## 6️⃣ Checklist khi tạo project mới

* [ ] `pyenv local 3.11.9` + `uv venv` + `uv add ...`
* [ ] `nvm use --lts` + `corepack enable` + `pnpm i`
* [ ] Bind `0.0.0.0` khi chạy dev server
* [ ] VS Code chọn đúng interpreter / Node
* [ ] ESLint / Prettier / Ruff hoạt động
