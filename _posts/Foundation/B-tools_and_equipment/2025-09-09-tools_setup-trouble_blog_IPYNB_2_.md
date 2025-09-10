---
toc: True
layout: post
data: tools
title: Progress and Problems in Weeks 0-4
description: Recovery guide for common issues with GitHub, cloning, virtual environments, and running your website.
permalink: /tools/setupblog
breadcrumb: /tools
breadcrumbs: True
---

## 🔧 Common Issues I've experienced

Operating the make command was one of the most common issues I experienced over the first 4 weeks. I frequently ran into errors where the server would not start, time out, or fail due to ports already being in use. These problems often required me to troubleshoot by killing stray processes, switching ports, or even bypassing the Makefile and running Jekyll directly. While frustrating, it taught me how the server was actually working behind the scenes and gave me a better understanding of the tools I was using.

## 🔧 Tool Setup Troubleshooting Guide

Use this page if something is not working.  
Each section is independent — jump directly to the area you are stuck.  

---

## GitHub Commit / Config Recovery

Use these commands if git commit is failing

✅ **Expectation**  
You have a GitHub username + email

```bash
git config --list` # shows your GitHub username + email.  
```

❌ **If not personalized, run to match your credentials:**  

```bash
git config --global user.name "jm1021"        # change to your GitHub ID
git config --global user.email "jm1021@gmail.com"  # change to your Email
```

---

## Directory + Clone Recovery

✅ Expectation
You can cd into your personal directory, and an ls shows your repo folder (ex: student).

### Navigate

```bash
cd ~/jm1021 # change jm1021 to your user directory name
```

❌ If cd fails, run:

```bash
mkdir ~/jm1021
cd ~/jm1021
```

### Check for repo folder

```bash
ls # lshould show "student"
```

❌ If missing, run:

```bash
git clone https://github.com/jm1021/student.git # change to personal location of repo
```

---

## Virtual Environment Recovery

✅ Expectation
Your terminal prompt shows (venv) prefix.

### Run Vitual Environment

```bash
source venv/bin/activate
```

❌ If it fails

```bash
./scripts/venv.sh
source venv/bin/activate
```

### VSCode Launch and Memories

✅ Satisfying the pre-requisites

- In project directory of your repo `pwd`
- Sourcing virtual environment `source venv/bin/activate`
- Ensure your terminal prompt shows the active virtual environment `(venv)`.

You are now ready to load VSCode and build a proper memory to open your project.

```bash
code .
```

✅ Verify VSCode launch

- Terminal and presence of `(venv)` prompt
- Open your Jokes IPYNB notebook and select the Python kernel with the `venv` prefix.

❌ If you fail verification

You may have opened your repo project without activating the proper `(venv)` environment.

Check the `Recent` listings. If there are entries that look incorrect or outdated (bad memories), remove them all.

- Shift-Cmd-P (Mac) or Shift-Ctl-P (Windows, KASM)
- type: Clear Recently Open -- select and confirm
- close VSCode
- Repeat VSCode Launch and Memories

---

## Version Checks

✅ Expectation

Run the bash script below
- Output is expected for each `### Command`
- Version may be slightly different, but ask if you are not sure
* Java kernels are required for CSA only

❌ If it fails

Best course of action is to run OS specific activate scripts from `pages` project directory

```bash
./scripts/activate_ubuntu.sh # windows ubuntu
./scripts/activate_macos.sh # macos
./scripts/activate.sh # help setup git config options
```



```python
%%script bash

# Define an array of commands
commands=("python --version" "pip --version" "ruby -v" "bundle -v" "gem -v" "jupyter --version" "jupyter kernelspec list" "git config --global user.name" "git config --global user.email")


for cmd in "${commands[@]}"; do
  echo "### Command: $cmd"
  bash -c "$cmd"
done
```

    ### Command: python --version
    Python 3.13.7
    ### Command: pip --version
    pip 25.2 from /Users/johnmortensen/jm1021/student/venv/lib/python3.13/site-packages/pip (python 3.13)
    ### Command: ruby -v
    ruby 3.4.5 (2025-07-16 revision 20cda200d3) +PRISM [arm64-darwin24]
    ### Command: bundle -v
    Bundler version 2.6.9
    ### Command: gem -v
    3.6.9
    ### Command: jupyter --version
    Selected Jupyter core packages...
    IPython          : 9.5.0
    ipykernel        : 6.30.1
    ipywidgets       : not installed
    jupyter_client   : 8.6.3
    jupyter_core     : 5.8.1
    jupyter_server   : 2.17.0
    jupyterlab       : 4.4.6
    nbclient         : 0.10.2
    nbconvert        : 7.16.6
    nbformat         : 5.10.4
    notebook         : 7.4.5
    qtconsole        : not installed
    traitlets        : 5.14.3
    ### Command: jupyter kernelspec list
    Available kernels:
      java           /Users/johnmortensen/Library/Jupyter/kernels/java
      jbang-ijava    /Users/johnmortensen/Library/Jupyter/kernels/jbang-ijava
      python3        /Users/johnmortensen/jm1021/student/venv/share/jupyter/kernels/python3
    ### Command: git config --global user.name
    jm1021
    ### Command: git config --global user.email
    jmort1021@gmail.com

---

## 🔧 Makefile Issues I've Experienced

Here are some common problems and solutions when working with Makefiles:

- **Command not found:**
  - The Makefile references a command (like `python`, `pip`, or `bundle`) that isn't installed or isn't in your PATH.
  - Solution: Install the missing tool or check your PATH variable.

- **Permission denied:**
  - You get a permission error running `make` or a command inside the Makefile.
  - Solution: Use `chmod +x <script>` to make scripts executable, or run with `sudo` if appropriate (be careful with sudo).

- **Target not found / No rule to make target:**
  - You run `make <target>` and get an error that the target doesn't exist.
  - Solution: Check the spelling of your target, and ensure the Makefile defines it.

- **Environment not activated:**
  - Makefile commands fail because your Python virtual environment isn't activated.
  - Solution: Activate your environment before running `make`, or add activation steps to the Makefile.

- **File not found errors:**
  - The Makefile tries to run or build a file that doesn't exist (like a missing script or notebook).
  - Solution: Check file paths and ensure all required files are present.

- **Dependency errors:**
  - `make` fails because required packages aren't installed.
  - Solution: Run `pip install -r requirements.txt` or the equivalent for your language.

- **Output not updating:**
  - You run `make` but changes aren't reflected, possibly due to caching or missing dependencies.
  - Solution: Use `make clean` if available, or manually remove build/output files.

## Conclusions and Resolutions 

I am still new to CSP, and many of the challenges I faced with the make command and setup were part of the learning process. During the first four weeks of class, I spent time getting familiar with the structure of projects, understanding how files interact, and learning the basics of version control and debugging. These initial weeks involved a lot of trial and error—figuring out how to run programs correctly, navigating errors, and understanding the workflow of assignments.

Experimenting with solutions and fixing problems on my own has taught me a great deal. Each error I encountered, from setup issues to code bugs, helped me understand more about how things work behind the scenes. I am gaining confidence in reading error messages, searching for solutions, and applying fixes effectively. Reflecting on these first weeks, I see clear progress in both my technical skills and my problem-solving approach, and I feel more prepared to tackle upcoming projects as I continue to practice.


## My Progress & Achievements

Here are some milestones I've accomplished while working on this project:

- **Added an About Page:**
  - Created an `about.md` page to introduce myself and the project, helping visitors understand the purpose and background.

- **Cloned a Repository:**
  - Successfully cloned the project repository from GitHub to my local machine, setting up my workspace for development.
  - git clone

- **Collaborated with My Team:**
  - Worked together with my teammates on code, documentation, and troubleshooting. Used git for version control and communication to resolve issues and share progress.

- **Jupyter Notebooks and Jokes**
  - Opened and ran Jupyter Notebooks in VS Code
  - Practiced with the Jokes.ipynb notebook and converted results into HTML format
  - Added my own lawyer jokes

- **Changing Background**
  - Made changes to the background.md file
  - Learned how to use Make and local host server
  - By editing frontmatter, we can change the background image for our website

These steps helped me build confidence in using git, GitHub, and project management tools. Collaboration and documentation are key parts of my workflow!


