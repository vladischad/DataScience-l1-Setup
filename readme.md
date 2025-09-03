# Course Setup: Python, Miniconda, and Jupyter Notebook

What you’ll install:
- Miniconda (a lightweight distribution that manages Python versions and packages)
- A clean `conda` environment for the course
- Jupyter Notebook (and optionally JupyterLab)

Estimated time: 15–30 minutes.

Quick links:
- Miniconda downloads: https://docs.conda.io/en/latest/miniconda.html
- Jupyter docs: https://jupyter.org/

---

## 1) Install Miniconda (recommended on all platforms)

Miniconda provides Python and `conda`, which makes it easy to create isolated environments so this course doesn’t conflict with other projects on your machine.

### macOS
1) Check your Mac’s chip:
   - Apple menu → About This Mac → “Chip” says Apple M1/M2/M3/M4 (Apple Silicon) or Intel.
2) Download Miniconda for your chip from the official page (link above):
   - Choose the macOS installer for your architecture (Apple Silicon arm64 or Intel x86_64).
   - Prefer the `.pkg` (graphical) installer unless you’re comfortable with Terminal.
3) Install:
   - Open the downloaded `.pkg`(graphical) and follow the prompts. Accept defaults.
4) Open Terminal (Spotlight → “Terminal”). Verify installation:
   - `conda --version`
   - If Terminal says `conda: command not found`, run: `conda init zsh`, then close and reopen Terminal.

Alternative (advanced, Terminal-based):
- Download the `.sh` installer from the Miniconda page, then run:
  - `bash ~/Downloads/Miniconda3-latest-MacOSX-arm64.sh` (or `...-x86_64.sh` for Intel)
  - Accept the license, default path, and say “yes” to `conda init`. Then restart Terminal.

### Windows
1) Download the Miniconda installer for Windows 64-bit from the official page.
2) Run the installer:
   - When prompted, keep defaults. It’s OK to “Register Miniconda as the system Python.”
   - Do NOT check “Add Miniconda to my PATH” (default is unchecked). Use the provided prompt instead.
3) After installation, open “Anaconda Prompt (miniconda3)” from the Start Menu.
4) Verify installation in that prompt:
   - `conda --version`

### Linux (Ubuntu/Debian/Fedora/…)
1) Download the Linux `.sh` installer from the Miniconda page.
2) Open a terminal and run the installer (adjust filename as needed):
   - `bash ~/Downloads/Miniconda3-latest-Linux-x86_64.sh`
   - Accept the license and default install location.
   - Say “yes” to `conda init` when prompted.
3) Restart your shell (close and reopen terminal) or run `source ~/.bashrc` (or `source ~/.zshrc` if you use zsh).
4) Verify:
   - `conda --version`

---

## 2) Create a clean course environment

Use a dedicated `conda` environment so each student’s Python and packages are isolated for the course.

In a terminal (macOS/Linux) or Anaconda Prompt (Windows):

```
conda create -n cs233 python=3.13 -y
conda activate cs233
```

Notes:
- Replace `c233` with any environment name you prefer (optional).
- You must run `conda activate cs233` in each new terminal session before working on the class material.

PS:
- If you see "service not accepted" or "Terms of Service not found" error, run
```
# View (optional)
conda tos view --channel https://repo.anaconda.com/pkgs/main
conda tos view --channel https://repo.anaconda.com/pkgs/r

# Accept (required once per channel)
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/main
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/r
```

---

## 3) Install Jupyter Notebook (and optional JupyterLab)

With the `cs233` environment active:

```
conda install -n cs233 jupyter -y
```

Optional (JupyterLab modern UI):

```
conda install -n cs233 jupyterlab -y
```

Alternative (pip, if needed):

```
pip install notebook
```

---

## 4) Launch Jupyter Notebook

1) Open a terminal (macOS/Linux) or Anaconda Prompt (Windows).
2) Activate the environment: `conda activate cs233`.
3) Navigate to your lab folder (`cd` into the correct directory).
4) Start Notebook:

```
jupyter notebook
```

What you should see:
- Your web browser opens automatically at `http://localhost:8888` with the Jupyter file browser.
- If it doesn’t open, copy-paste the full URL with the security token from the terminal into your browser.

Test it works:
- Click “New” → “Python 3 (ipykernel)” to create a new notebook.
- In the first cell, run:

```
print("Hello, world!")
```

Stopping Jupyter:
- Go back to the terminal running Jupyter and press `Ctrl+C` (twice if asked to confirm).


---

## 6) Troubleshooting

- conda not found:
  - macOS: run `conda init zsh`, then fully close and reopen Terminal.
  - Linux: run `conda init bash` (or your shell), then `source ~/.bashrc` and reopen terminal.
  - Windows: use “Anaconda Prompt (miniconda3)” instead of cmd/PowerShell, or run `conda init powershell` and restart PowerShell.

- Notebook won’t open in browser:
  - Copy the URL with the `?token=...` from the terminal into your browser.
  - Try a different port: `jupyter notebook --port 8889`.

- Wrong Python showing in Jupyter:
  - Ensure the env is active: `conda activate course` before launching Jupyter.
  - Register the kernel explicitly:
    - `python -m ipykernel install --user --name course --display-name "Python (course)"`

- Permission issues on school laptops:
  - Choose “Just Me” during install and pick a user-writable folder (your home directory).

- Multiple Python installations:
  - Always activate your environment first: `conda activate course`, then use `python` and `pip` from there.


---

All set! Each session, remember to `conda activate cs233` before working on assignments.
