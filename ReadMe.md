## Prerequisites

Ensure you have the following installed:

- Python 3.10+
- pip
- npm

### 1. Clone the Flask Tailwind Installer Repository

```bash
gh repo clone digitaldesaster/flask_tailwind_installer my_flask_app
cd my_flask_app
```

### 2. Create and Activate a Virtual Environment

Create and activate the virtual environment and open the project in VSCode

- **macOS and Linux:**

```bash
python3 -m venv .venv
code .
```

activate the virtual environment in VSCode

```bash
source .venv/bin/activate
```

### 3. Install the rest of the dependencies

use the install.py script to install the rest of the dependencies

```bash
python3 install.py
```

### 4. Start the Flask Server, Browser-Sync and the TailwindCSS Watcher

press cmd + shift + p and and run Start All to start the flask server, browser-sync and the tailwindcss watcher

or start them seperately:

- Start Flask
- Start Browser-Sync
- Watch CSS with TailwindCSS
