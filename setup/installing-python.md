# Setting up Python for this course

Do this **before** the first lab. If you get stuck, post in Issues with the exact
error message copy-pasted as text — screenshots of the whole screen are harder to
help with.

## 1. Check whether you already have Python

Open a terminal (macOS: Terminal; Windows: PowerShell) and run:

```bash
python3 --version
```

On Windows, if that does nothing, try `python --version`.

This course needs **Python 3.12 or later**. If you see that, skip to step 2.

macOS users: the version macOS comes with is old (3.9) and cannot be upgraded.
You will see 3.9 here even though you have done nothing wrong. Install a current
version anyway, following the instructions below, and leave the system one alone.

If you need to install:
- **Windows:** install from [python.org](https://www.python.org/downloads/).
  On the first installer screen, tick **"Add python.exe to PATH"**. This is easy to
  miss and everything fails later without it.
- **macOS:** install from [python.org](https://www.python.org/downloads/) and run
  the installer with the defaults.
- **Linux:** `sudo apt install python3 python3-venv`

## 2. Get the course materials

```bash
git clone https://github.com/YOUR-ORG/course-materials.git
cd course-materials
```

Everything below assumes you are inside this folder. If a command says it cannot
find `requirements.txt`, you are in the wrong directory — check with `pwd` (macOS,
Linux) or `cd` (Windows).

## 3. Create a virtual environment

A virtual environment is a private folder of packages for this course, so that
installing something here cannot break anything else on your machine. You create it
once:

```bash
python3.14 -m venv .venv
```

Name the version explicitly, as above, rather than typing plain `python3`. On macOS
both exist and `python3` may still point at the old system copy; naming the version
removes the ambiguity. Substitute whichever version you installed.

Then activate it — **every time you open a new terminal**:

```bash
source .venv/bin/activate        # macOS and Linux
```

```powershell
.venv\Scripts\Activate.ps1       # Windows PowerShell
```

Your prompt should now start with `(.venv)`. If it does not, the environment is not
active and nothing below will work as expected.

*Windows note:* if PowerShell refuses to run the activation script, run
`Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` once, answer yes, and try again.

## 4. Install the packages

```bash
pip install -r requirements.txt
```

Inside an active environment, `pip` is the right command. Outside one on macOS you
would need `pip3` — another reason to check for `(.venv)` first.

## 5. Install and configure VS Code

Install [Visual Studio Code](https://code.visualstudio.com/) and, from the
Extensions panel, the **Python** and **Jupyter** extensions.

Then **File → Open Folder** and select `course-materials`. Press
**Cmd+Shift+P** (macOS) or **Ctrl+Shift+P** (Windows), type
`Python: Select Interpreter`, and choose the one inside `.venv`.

VS Code remembers this per folder and will activate the environment automatically in
its built-in terminal from then on.

## 6. Install Git

- **Windows:** [Git for Windows](https://gitforwindows.org/)
- **macOS:** included with the command line tools from step 1
- **Linux:** `sudo apt install git`

Tell Git who you are, using the same email as your GitHub account:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email"
```

## 7. Check that everything works

With `(.venv)` showing in your prompt:

```bash
python -c "import pandas, numpy, statsmodels; print('ok')"
```

If this prints `ok`, you are ready for the first lab.

---

### If you already use Anaconda or Miniforge

Nothing here conflicts with it, but do not mix the two. Use
`conda create -n econ python=3.12`, `conda activate econ`, then step 4 onwards as
written, and select the `econ` interpreter in VS Code instead of `.venv`.
