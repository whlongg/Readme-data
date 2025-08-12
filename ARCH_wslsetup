# 🚀 WSL Dev Setup Guide – **Arch Linux** (Python + Node.js)
_Cho FastAPI, NestJS, Next.js – tối ưu cho WSL2 + VS Code. 

> **TL;DR**: Nếu ông ưu tiên hiệu năng dev & Docker mượt: chạy **Arch (WSL2 + systemd)**, code đặt trong **Linux FS** (`~/code`), dùng **pyenv + uv** cho Python, **nvm + pnpm** cho Node, **Docker systemd** trong WSL.


## 1️⃣ Cài WSL2 & Arch Linux
### 1.1 Bật WSL2 (một lần duy nhất)
Mở **PowerShell (Admin)** và chạy:
```powershell
wsl --install
wsl --set-default-version 2
```
Khởi động lại nếu được yêu cầu.

### 1.2 Cài **Arch Linux** cho WSL
**Cách A – Microsoft Store (dễ nhất):**
- Mở Microsoft Store → tìm **“Arch Linux”** → Install → Launch → tạo username/password.

**Cách B – Import thủ công (ArchWSL):**
- Tải file rootfs từ dự án **ArchWSL** (phổ biến trong cộng đồng).
- Tạo thư mục và import:
```powershell
mkdir C:\WSL\Arch
wsl --import Arch C:\WSL\Arch <đường-dẫn>\ArchWSL.tar.gz --version 2
wsl -d Arch
```
- Tạo user non-root theo hướng dẫn của ArchWSL (thường là chạy script `arch.exe` hoặc `setuser`).
> Lưu ý: Không chạy workload nặng trước khi hoàn tất setup ở phần 2 và bật systemd.


---

## 2️⃣ Cấu hình Windows host cho WSL2
### 2.1 `.wslconfig` (trên **Windows**)
Mở:
```powershell
notepad $env:USERPROFILE\.wslconfig
```
Dán nội dung (điều chỉnh theo máy):
```ini
[wsl2]
memory=16GB                 # Giới hạn RAM cho WSL2 (tùy cấu hình)
processors=4                # Số core WSL2 được dùng
swap=0                      # Tắt swap (khuyên dùng trên máy RAM >=16GB)
localhostForwarding=true    # Cho phép kết nối 2 chiều localhost
networkingMode=mirrored     # LAN discovery tốt hơn (yêu cầu WSL mới)
dnsTunneling=true           # DNS ổn định hơn (yêu cầu WSL mới)
autoProxy=true              # Dùng proxy hệ thống nếu có
# swapFile=C:\\WSL\\swap.vhdx  # Nếu muốn bật swap, bỏ comment và set đường dẫn
```
> Sau khi chỉnh, chạy `wsl --shutdown` để áp dụng.


---

## 3️⃣ One-time setup trong **Arch (WSL2)**
Mở phiên Arch (`wsl -d Arch`) và chạy từng bước:

### 3.1 Cập nhật & chuẩn hoá pacman
```bash
sudo pacman -Syu --noconfirm
sudo pacman -S --needed --noconfirm base-devel git curl wget unzip zip tar pkgconf ca-certificates
sudo update-ca-trust
```
(Tuỳ chọn) Cài **reflector** để chọn mirror nhanh:
```bash
sudo pacman -S --noconfirm reflector
sudo reflector --country 'Singapore,Vietnam,Japan' --age 12 --protocol https --sort rate --save /etc/pacman.d/mirrorlist
sudo pacman -Syyu --noconfirm
```

### 3.2 Bật **systemd** cho WSL (rất quan trọng)
Tạo `/etc/wsl.conf`:
```bash
sudo tee /etc/wsl.conf >/dev/null <<'EOF'
[boot]
systemd=true

[automount]
enabled=true
options = "metadata,umask=22,fmask=11"   # quyền file tốt hơn khi truy cập từ Windows

[network]
generateHosts = true
generateResolvConf = true

[interop]
enabled=true
appendWindowsPath=false
EOF
```
Áp dụng: thoát Arch → chạy bên Windows:
```powershell
wsl --shutdown
```
Mở lại Arch, kiểm tra:
```bash
systemctl is-system-running    # running hoặc degraded (degraded vẫn OK trong WSL)
```

### 3.3 Shell & tiện ích
```bash
sudo pacman -S --noconfirm zsh neovim htop jq fd ripgrep tmux tree
chsh -s "$(which zsh)"
```

### 3.4 Python toolchain: **pyenv + uv**
Cài deps build Python:
```bash
sudo pacman -S --noconfirm openssl zlib bzip2 readline sqlite xz tk libffi
```
Cài **pyenv** (script chính thức):
```bash
curl https://pyenv.run | bash
```
Thêm vào `~/.zshrc`:
```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init --path)"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```
Cài **uv** (quản lý venv + deps cực nhanh):
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
```

### 3.5 Node.js: **nvm + corepack (pnpm)**
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.zshrc
echo '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"' >> ~/.zshrc
echo 'corepack enable >/dev/null 2>&1 || true' >> ~/.zshrc
```
**Sau khi mở shell mới:**
```bash
nvm install --lts
nvm use --lts
corepack prepare pnpm@latest --activate
```

### 3.6 Tăng file watcher (hot reload mượt)
```bash
echo 'fs.inotify.max_user_watches=524288' | sudo tee /etc/sysctl.d/99-inotify.conf
echo 'fs.inotify.max_user_instances=1024' | sudo tee -a /etc/sysctl.d/99-inotify.conf
sudo sysctl --system
```

### 3.7 Git config cơ bản
```bash
git config --global user.name "Nguyen Hoang Long"
git config --global user.email "nhl08.contact@gmail.com"
git config --global core.autocrlf input
git config --global init.defaultBranch main
git config --global pull.rebase false
```

### 3.8 Docker (native trong WSL với systemd)
```bash
sudo pacman -S --noconfirm docker docker-compose-plugin
sudo usermod -aG docker $USER
sudo systemctl enable --now docker
# mở shell mới hoặc chạy:
newgrp docker
docker run --rm hello-world
```
> Nếu dùng Docker Desktop trên Windows, có thể bỏ phần này và bật **WSL integration** cho distro Arch.


---

## 4️⃣ Per-project setup

### 4.1 Python + FastAPI
```bash
pyenv install 3.11.9
pyenv local 3.11.9

uv venv
uv add fastapi "uvicorn[standard]" pydantic python-dotenv

uv run uvicorn app:app --reload --host 0.0.0.0 --port 8000
# Truy cập từ Windows: http://localhost:8000
```

### 4.2 Node + NestJS
```bash
nvm use --lts
corepack enable
corepack prepare pnpm@latest --activate

pnpm dlx @nestjs/cli new server
cd server
pnpm start:dev   # bind 0.0.0.0 nếu muốn Windows truy cập qua localhost
```

### 4.3 Node + Next.js
```bash
nvm use --lts
corepack enable
corepack prepare pnpm@latest --activate

pnpm dlx create-next-app@latest web
cd web
pnpm dev -- --host 0.0.0.0 --port 3000
# Truy cập: http://localhost:3000
```


---

## 5️⃣ VS Code Setup

### 5.1 Extensions nên cài
- **Remote – WSL**
- Python, Pylance
- Ruff hoặc Black (Python)
- ESLint, Prettier (JS/TS)
- Docker, GitLens, Thunder Client, Error Lens

### 5.2 `settings.json` (WSL workspace)
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

## 6️⃣ Performance tips (WSL2 x Arch)

- **Đặt code trong Linux FS**: `~/code/...` thay vì `/mnt/c/...` → I/O nhanh hơn rất nhiều.
- **Docker**: chạy native trong WSL (systemd) hoặc bật integration của Docker Desktop.
- **Networking**: `networkingMode=mirrored` + `localhostForwarding=true` giúp service trong WSL expose ra Windows mượt.
- **Antivirus Windows**: exclude thư mục `\\wsl$\<Arch>\home\<you>\code` nếu thấy I/O chậm.
- **Restart WSL nhanh**: `wsl --shutdown` rồi mở lại khi đổi config.
- **Disk space**: thi thoảng dọn `~/.cache`, `pnpm store prune`, `uv cache clean`.


---

## 7️⃣ Checklist tạo project mới

- [ ] `pyenv local 3.11.x` + `uv venv` + `uv add ...`
- [ ] `nvm use --lts` + `corepack enable` + `pnpm i`
- [ ] Dev server bind `0.0.0.0` (để Windows truy cập `localhost:<port>`)
- [ ] VS Code chọn đúng interpreter / Node
- [ ] ESLint / Prettier / Ruff hoạt động
- [ ] Docker build/run OK (nếu dự án có container)


---

## 8️⃣ Sự cố hay gặp & cách xử lý nhanh
- **Không có systemd**: kiểm tra `/etc/wsl.conf` có `systemd=true` → `wsl --shutdown` → mở lại.
- **Docker không start**: `sudo usermod -aG docker $USER` → mở shell mới hoặc `newgrp docker`.
- **Hot reload không chạy**: tăng inotify watchers (mục 3.6) và đảm bảo project không nằm ở `/mnt/*`.
- **WSL không vào mạng**: thử `networkingMode=mirrored`, `dnsTunneling=true` trong `.wslconfig` rồi `wsl --shutdown`.
- **Nặng RAM**: giảm `memory=` trong `.wslconfig`, hoặc tắt bớt service không cần (tmux, compilers…).
