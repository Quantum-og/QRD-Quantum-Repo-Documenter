# RepoDoc Pro

> **Convert any software project into professional PDF documentation — automatically.**

RepoDoc Pro is a production-grade desktop application that recursively scans a code repository and generates beautifully formatted, syntax-highlighted PDF documentation with optional AI-powered summaries, data visualizations, petroleum well log plots, and a clickable table of contents.

**No API key required to use it.** AI summaries are an optional add-on — everything else works out of the box.

---

## 📥 Installing the App (End Users)

> **You do not need Python, Node.js, or Docker to install and run RepoDoc Pro.**
> Everything is bundled inside the installer.

Download the latest release from the [**Releases page**](../../releases/latest).

---

### 🪟 Windows

**Requirements:** Windows 10 or later (64-bit)

1. Download **`RepoDoc-Pro-x.x.x-Setup.exe`** from the Releases page
2. Double-click the installer
3. Follow the on-screen steps (Next → Next → Install → Finish)
4. Launch **RepoDoc Pro** from the Start Menu or Desktop shortcut

**First launch — Python setup:**

If Python is not already installed, you will see a red screen saying **"Python Not Found"** with step-by-step instructions. Here is what to do:

1. Click **Download Python** inside the app (or go to [python.org/downloads](https://www.python.org/downloads/))
2. Download **Python 3.11** or newer
3. Run the installer
4. ⚠️ **Check "Add Python to PATH"** before clicking Install — this is critical
5. Click **Retry** inside RepoDoc Pro — it will set itself up automatically (1–3 minutes)
6. Do not close the app while it says "Setting up…"

**Windows SmartScreen warning?**
Click **More info → Run anyway**. This appears because the app is not yet code-signed — it is safe.

---

### 🍎 macOS

**Requirements:** macOS 12 Monterey or later (Intel or Apple Silicon)

1. Download **`RepoDoc-Pro-x.x.x.dmg`** (Intel) or **`RepoDoc-Pro-x.x.x-arm64.dmg`** (Apple Silicon / M1/M2/M3) from the Releases page
2. Open the `.dmg` file
3. Drag **RepoDoc Pro** into the **Applications** folder
4. Open **Launchpad** or **Finder → Applications** and launch RepoDoc Pro

> **"RepoDoc Pro cannot be opened because it is from an unidentified developer"?**
> Right-click (or Control-click) the app → **Open** → **Open** again in the dialog.
> This is a macOS Gatekeeper warning for unsigned apps — it only appears once.

> **First launch only:** Same as Windows — a setup screen may appear briefly while Python packages are installed.

---

### 🐧 Linux

**Requirements:** Ubuntu 20.04+ / Debian 11+ or any modern distro with glibc 2.31+

#### Option A — AppImage (recommended, works on any distro)

1. Download **`RepoDoc-Pro-x.x.x.AppImage`** from the Releases page
2. Open a terminal and make it executable:
   ```bash
   chmod +x RepoDoc-Pro-x.x.x.AppImage
   ```
3. Run it:
   ```bash
   ./RepoDoc-Pro-x.x.x.AppImage
   ```
4. *(Optional)* Double-click to run from your file manager — you may need to enable **"Allow executing file as program"** in file properties first

#### Option B — Debian/Ubuntu `.deb` package

1. Download **`repodoc-pro_x.x.x_amd64.deb`** from the Releases page
2. Install it:
   ```bash
   sudo dpkg -i repodoc-pro_x.x.x_amd64.deb
   ```
3. Launch from your application menu or run:
   ```bash
   repodoc-pro
   ```

> **First launch only:** A setup screen may appear while Python packages are installed. If it fails, make sure Python 3.10+ is installed:
> ```bash
> # Ubuntu/Debian
> sudo apt install python3 python3-venv
>
> # Fedora/RHEL
> sudo dnf install python3
>
> # Arch
> sudo pacman -S python
> ```
> Then restart RepoDoc Pro.

---

## ✨ Features

### 📁 Project Scanner
- Full recursive folder tree with file inventory
- Language and file type detection (15+ source types)
- Line counts, file sizes, last-modified dates
- Real-time progress via WebSocket
- Handles repositories with 100,000+ files

### 📄 Table of Contents
Auto-generated clickable TOC with folder → file → page number hierarchy.

### 💻 Source Code Export
For `.py`, `.ts`, `.tsx`, `.js`, `.sh`, `.sql`, `.yaml`, `.json`, `.toml`, `.html`, `.css`, `.md` and more:
- Syntax highlighting (4 themes)
- Line numbering
- Wrapped long lines
- File metadata header card

### 📊 Data File Support
- **CSV** — schema, statistics, preview of first N rows
- **Excel (.xlsx/.xls)** — workbook info, sheet list, sheet previews
- **Parquet** — column types and sample rows

### 🖼️ Image & SVG Export
- PNG, JPG, JPEG, WEBP embedded as gallery pages
- SVG rendered directly into PDF at full resolution

### 🛢️ Petroleum Data (Industry-Grade)

| Format | Features |
|--------|----------|
| **LAS** | Header, well info, curve list, quick-look wireline plot |
| **Production CSV** | Oil/gas/water rate vs time plots |
| **Pressure CSV** | Pressure trend charts |

### 🤖 AI Documentation — *Optional*
Per-file AI summaries powered by **Anthropic Claude** (or OpenAI as fallback). Skipped automatically if no API key is set — exports still complete normally:
- Summary & Purpose
- Key Functions / Classes
- Inputs & Outputs
- External Dependencies
- Complexity rating (Low → Very High)

### 📈 Project Statistics
- Total files, LOC, size
- Language distribution bar charts
- Largest file leaderboard
- Folder depth distribution

### 🔍 Search
Search by filename, extension, or file content across the project.

### 📦 Export Modes

| Mode | Output | Best For |
|------|--------|----------|
| **A — Single PDF** | `Project.pdf` | Client handoffs, code reviews |
| **B — Folder PDFs** | One PDF per folder | Modular large projects |
| **C — Per-File PDFs** | One PDF per file | Audit trails |
| **D — Documentation Package** | Full suite | Portfolio, technical due diligence |

### 🎨 Themes

| Theme | Style |
|-------|-------|
| `default` | GitHub Light |
| `dark` | GitHub Dark |
| `github` | GitHub Neutral |
| `monokai` | Classic Monokai |

---

## 🖥️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Desktop Shell** | Electron 28 |
| **Frontend** | React 18, TypeScript, Material UI v5 |
| **State Management** | Redux Toolkit |
| **Backend** | Python 3.11, FastAPI, uvicorn |
| **PDF Engine** | ReportLab 4 (custom Flowables) |
| **Data Processing** | Pandas, OpenPyXL, PyArrow |
| **Code Analysis** | Python AST, Pygments, regex |
| **Visualization** | Matplotlib, Plotly |
| **Petroleum** | lasio |
| **AI (optional)** | Anthropic Claude API, OpenAI API |
| **Architecture** | Clean Architecture, DDD, SOLID |

---

## 🚀 Developer Quick Start

> This section is for contributors and developers. End users should use the [installer](#-installing-the-app-end-users) above.

### Requirements

- **Python** 3.10 or higher
- **Node.js** 18 or higher

### 1. Clone & Setup

```bash
git clone https://github.com/your-org/repodoc-pro.git
cd repodoc-pro
```

**Linux / macOS:**

```bash
bash scripts/setup_dev.sh
```

**Windows (PowerShell):**

```powershell
powershell -ExecutionPolicy Bypass -File scripts\setup_dev.ps1
```

The script creates a Python virtual environment, installs all backend dependencies, sets up `backend/.env`, and optionally installs the Electron frontend dependencies and runs the test suite.

> **Manual setup instead?** See [Manual Installation](#manual-installation) below.

### 2. (Optional) Add AI API Keys

AI documentation is **disabled by default and not required**. To enable it, edit `backend/.env`:

```bash
# backend/.env
ANTHROPIC_API_KEY=sk-ant-...
# or
OPENAI_API_KEY=sk-...
```

### 3. Start the Backend

```bash
cd backend
source .venv/bin/activate        # Windows: .venv\Scripts\activate
python src/main.py --port 8765 --reload
```

Verify it's running:

```bash
curl http://localhost:8765/health
```

Expected response:
```json
{"status":"ok","version":"1.0.0","timestamp":"...","python":"..."}
```

> Interactive API docs (development mode only): **http://localhost:8765/docs**

### 4. Start the Frontend (Desktop App)

```bash
# Terminal 2
cd electron
npm run dev:renderer

# Terminal 3
cd electron
npx wait-on http://localhost:5173 && npx electron .
```

---

## 🐙 Running in GitHub Codespaces

```bash
cd backend
REPODOC_ENV=development python src/main.py --port 8765 --reload
```

Then open the forwarded port URL (shown in the **Ports** tab):

```
https://<your-codespace-name>-8765.app.github.dev/health
https://<your-codespace-name>-8765.app.github.dev/docs
```

---

## 🛠️ Manual Installation

```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate

pip install -r requirements.txt    # Note the -r flag — required

cp .env.example .env               # edit .env as needed

python src/main.py --port 8765 --reload
```

> **Common mistake:** running `pip install requirements.txt` (without `-r`) will fail. Always use `pip install -r requirements.txt`.

For the frontend:

```bash
cd electron
npm install
npm run dev:renderer
```

---

## 📁 Project Structure

```
repodoc-pro/
├── electron/                    # Desktop frontend
│   ├── src/
│   │   ├── main/main.ts         # Electron main: lifecycle, IPC, backend mgmt
│   │   ├── preload/preload.ts   # Secure contextBridge IPC API
│   │   └── renderer/            # React application
│   │       ├── App.tsx
│   │       ├── components/
│   │       │   ├── layout/      # MainLayout, sidebar
│   │       │   ├── features/    # Dashboard, Scanner, Export, Settings
│   │       │   └── shared/      # BackendStatus, UpdateBanner
│   │       ├── store/           # Redux slices (ui, project, export, scanner)
│   │       ├── hooks/           # useAppTheme, useElectronEvents, etc.
│   │       └── utils/           # apiClient (axios)
│   ├── package.json
│   ├── tsconfig.json
│   └── vite.renderer.config.ts
│
├── backend/                     # Python FastAPI backend
│   ├── src/
│   │   ├── main.py              # FastAPI app + uvicorn entrypoint
│   │   ├── api/routes/          # scanner, export, ai, search, petroleum
│   │   ├── core/
│   │   │   ├── domain/entities/ # FileInfo, ProjectScan, ExportJob, ...
│   │   │   ├── services/        # ProjectScannerService, ExportOrchestrator
│   │   │   └── infrastructure/
│   │   │       ├── pdf/         # PDFBuilder, SyntaxCodeBlock, FileHeaderBlock
│   │   │       ├── parsers/     # CSVParser, ExcelParser, CodeParser, ImageParser
│   │   │       ├── petroleum/   # LASParser, ProductionCSVParser
│   │   │       ├── ai/          # AIDocumenter (Claude/OpenAI/Stub)
│   │   │       └── storage/     # TempManager
│   │   └── utils/               # Settings (pydantic), logging
│   ├── tests/
│   │   ├── unit/
│   │   └── integration/
│   ├── requirements.txt
│   ├── .env.example
│   └── pytest.ini
│
├── docker/
│   ├── Dockerfile.backend
│   └── docker-compose.yml
│
├── docs/
│   ├── architecture/ARCHITECTURE.md
│   ├── developer-guide/DEVELOPER_GUIDE.md
│   ├── user-guide/USER_GUIDE.md
│   └── DEPLOYMENT.md
│
├── scripts/
│   ├── setup_dev.sh             # Universal Linux/macOS setup
│   └── setup_dev.ps1            # Windows PowerShell setup
│
└── .github/workflows/ci.yml     # CI/CD: test → build → release → Docker
```

---

## 🔌 API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/health` | Health check |
| `POST` | `/scanner/scan` | Scan a project directory |
| `WS` | `/scanner/ws` | Real-time scan progress |
| `GET` | `/scanner/file-content` | Fetch file content for preview |
| `POST` | `/export/start` | Start an export job |
| `GET` | `/export/{id}/status` | Poll job status |
| `POST` | `/export/{id}/cancel` | Cancel a running job |
| `WS` | `/export/ws/{id}` | Real-time export progress |
| `POST` | `/ai/document` | Generate AI docs for a file |
| `GET` | `/ai/status` | Check AI provider configuration |
| `GET` | `/search/` | Search files by name/extension/content |
| `GET` | `/petroleum/las/parse` | Parse a LAS well log file |
| `GET` | `/petroleum/las/quicklook` | Generate quick-look plot |
| `GET` | `/petroleum/production/parse` | Parse production CSV |
| `GET` | `/petroleum/production/plot` | Generate rate plots |

> Full interactive docs at `http://localhost:8765/docs` (set `REPODOC_ENV=development`)

---

## 🧪 Testing

```bash
# Backend — all tests with coverage
cd backend
pytest

# Backend — specific suites
pytest tests/unit/
pytest tests/integration/

# Frontend — Redux slices
cd electron
npm test
npm run test:coverage
```

Target: **80%+ backend coverage**, **unit tests for all Redux slices**.

---

## 🏗️ Building for Distribution

```bash
cd electron

npm run dist:win      # → release/*.exe
npm run dist:mac      # → release/*.dmg
npm run dist:linux    # → release/*.AppImage + *.deb
```

Releases are built automatically via CI when a GitHub Release is published. See [DEPLOYMENT.md](docs/DEPLOYMENT.md) for code signing and Docker deployment.

---

## ⚙️ Configuration

### Backend Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `REPODOC_ENV` | `production` | Set to `development` to enable `/docs` |
| `REPODOC_PORT` | `8765` | Backend port |
| `REPODOC_LOG_LEVEL` | `INFO` | Logging verbosity |
| `REPODOC_TEMP_DIR` | `~/.repodoc/temp` | Temp directory |
| `REPODOC_MAX_FILE_SIZE_MB` | `50` | Max file size to process |
| `ANTHROPIC_API_KEY` | *(none)* | **Optional** — enables Claude AI summaries |
| `OPENAI_API_KEY` | *(none)* | **Optional** — OpenAI fallback |
| `REPODOC_AI_MODEL` | `claude-3-5-haiku-20241022` | AI model (only used if a key is set) |

### Default Exclude Patterns

The scanner automatically skips:
`__pycache__`, `node_modules`, `.git`, `.venv`, `dist`, `build`, `.next`, `coverage`, `*.pyc`, `*.egg-info`

Add custom patterns in **Settings → Scanner Exclude Patterns**.

---

## 🐧 Linux Distro Support

| Distro Family | Package Manager |
|---|---|
| Arch, Manjaro, EndeavourOS | `pacman` |
| Debian, Ubuntu, Mint, Pop!_OS | `apt` |
| Fedora, RHEL, CentOS Stream | `dnf` |
| Older RHEL/CentOS | `yum` |
| openSUSE | `zypper` |
| Alpine | `apk` |
| Void Linux | `xbps` |
| Gentoo | `emerge` |
| Solus | `eopkg` |
| NixOS / Nix | `nix` |

---

## 🗺️ Roadmap

- [ ] DLIS/LIS petroleum format support
- [ ] Dependency graph export (NetworkX → PDF diagram)
- [ ] Architecture diagram auto-generation
- [ ] Git history integration (commit log, blame)
- [ ] Custom PDF templates / branding
- [ ] Team/cloud mode (share scans)
- [ ] VS Code extension integration

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Write tests for your changes
4. Ensure all tests pass: `pytest` + `npm test`
5. Submit a pull request

See [DEVELOPER_GUIDE.md](docs/developer-guide/DEVELOPER_GUIDE.md) for architecture details.

---

## 🧯 Troubleshooting

| Symptom | Fix |
|---|---|
| Windows SmartScreen blocks installer | Click **More info → Run anyway** |
| macOS "unidentified developer" error | Right-click the app → **Open** → **Open** |
| Linux AppImage won't run | Run `chmod +x RepoDoc-Pro-*.AppImage` first |
| "Backend unavailable" on first launch | Wait for the setup screen to finish, or install Python 3.10+ and restart |
| `pip install requirements.txt` fails | Use `pip install -r requirements.txt` (missing `-r` flag) |
| `{"detail":"Not Found"}` at root URL | Expected — use `/health` or `/docs` instead |
| `/ai/status` shows `available: false` | Normal without an API key — add one to `backend/.env` to enable |
| Backend won't start — missing pango/cairo | Re-run `scripts/setup_dev.sh` |

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

## 🙏 Credits

Built with:
- [Electron](https://electronjs.org) · [React](https://react.dev) · [Material UI](https://mui.com)
- [FastAPI](https://fastapi.tiangolo.com) · [ReportLab](https://reportlab.com)
- [Pandas](https://pandas.pydata.org) · [lasio](https://lasio.readthedocs.io) · [Matplotlib](https://matplotlib.org)
- [Anthropic Claude](https://anthropic.com) · [Pygments](https://pygments.org)

---

<div align="center">

**RepoDoc Pro** — *Professional documentation, automatically.*

</div>
