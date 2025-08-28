# ✅ Flatiron Git Setup Walkthrough

![Status](https://img.shields.io/badge/Status-Ready%20to%20Use-brightgreen)
![Scope](https://img.shields.io/badge/Scope-Flatiron%20DS%20Cohort-blue)
![OS](https://img.shields.io/badge/Windows-10%2F11-informational)
![Shell](https://img.shields.io/badge/Shell-Git%20Bash-ff69b4)
![PRs](https://img.shields.io/badge/PRs-welcome-orange)
![License](https://img.shields.io/badge/License-MIT-purple)

> A friendly guide to align your local **Git** configuration with **Flatiron School’s** recommended defaults.  
> Even if you’ve already installed Git, run these steps to avoid “works on my machine” headaches during the bootcamp.

---

## 🧭 Quick Start (copy–paste in **Git Bash**)

```bash
# Step 1: Confirm version
git --version

# Step 2: Apply Flatiron-aligned settings
git config --global init.defaultBranch main
git config --global core.editor "vim"
git config --global core.autocrlf true
git config --global pull.ff true
git config --global credential.helper manager
git config --global core.fscache true

# Step 3: Verify everything
git config --list --show-origin
````

> Notes:
>
> * Using **Git Bash** on Windows implies **MinTTY** terminal, **OpenSSL** HTTPS backend, and bundled **OpenSSH**—all aligned with course defaults.
> * Editor `vim` is recommended; you can switch (see **Editor Options** below).

---

## 🧩 Why These Settings?

* **Consistent branches** → New repos start as `main` for everyone.
* **Cross-platform line endings** → `autocrlf=true` checks out Windows-style, commits Unix-style to keep diffs clean.
* **Predictable pulls** → `pull.ff=true` prefers fast-forwards, keeping history tidy.
* **Credential Manager** → Fewer re-auth prompts.
* **File system cache** → Snappier Git ops on Windows.

---

## 🔍 Full Walkthrough

### 1) Confirm Git is installed

```bash
git --version
# example: git version 2.50.1.windows.1
```

### 2) Apply Flatiron defaults

```bash
# Default branch name for new repos
git config --global init.defaultBranch main

# Default editor (Flatiron default: vim)
git config --global core.editor "vim"

# Line endings: Checkout Windows-style, commit Unix-style
git config --global core.autocrlf true

# Pull behavior: fast-forward (or merge if needed)
git config --global pull.ff true

# Credential Manager (Windows)
git config --global credential.helper manager

# Performance: file system caching
git config --global core.fscache true
```

### 3) Verify your config

```bash
git config --list --show-origin
```

Look for the values you just set under your **global** config file (usually `~/.gitconfig`).

---

## ✍️ Editor Options (choose one)

If you don’t want `vim`, pick your favorite:

```bash
# VS Code
git config --global core.editor "code --wait"

# Notepad (simple & installed by default)
git config --global core.editor "notepad"

# Notepad++
git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```

> Tip: Re-run `git config --list --show-origin` to confirm the change.

---

## 🧰 Troubleshooting

**Q: `git` not found in Command Prompt/PowerShell?**
A: Use **Git Bash** (preferred), or reinstall Git for Windows and choose **“Git from the command line and also from 3rd-party software”** for PATH.

**Q: Line endings still look weird in diffs?**
A:

```bash
git config --global core.autocrlf true
# For an existing repo, normalize once:
git rm --cached -r .
git reset --hard
```

**Q: Credential prompts keep popping up?**
A:

```bash
git config --global credential.helper manager
```

Then run an authenticated Git command (e.g., `git fetch`) and save credentials once.

**Q: Which file set my value?**
A:

```bash
git config --list --show-origin
```

You’ll see `system`, `global`, or `local` paths for each setting.

---

## 🧪 Optional: Test Drive

```bash
mkdir flatiron-git-check && cd flatiron-git-check
git init
git config --get init.defaultBranch   # should print 'main'
```

Create a file, commit, and confirm behavior:

```bash
echo "hello" > hello.txt
git add hello.txt
git commit -m "test: initial commit on main"
```

---

## 🤝 Contributing

Spotted something to improve for classmates (macOS notes, screenshots, etc.)?
PRs are welcome! Keep changes beginner-friendly and tested on **Git Bash (Windows)**.

---

## 📝 License

This project is licensed under the **MIT License**.

---
