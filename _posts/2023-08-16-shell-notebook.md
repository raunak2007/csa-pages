---
layout: post
title: Linux Shell and Bash (Student View)
description: A Tech Talk on Linux and the Bash shell.
toc: true
comments: true
categories: [5.A, C4.1]
courses: { csse: {week: 1}, csp: {week: 1, categories: [6.B]}, csa: {week: 1} }
type: devops
---

::: {.cell .markdown}

------------------------------------------------------------------------

layout: post title: Linux Shell and Bash (Student View) description: A
Tech Talk on Linux and the Bash shell. toc: true comments: true
categories: \[5.A, C4.1\] courses: { csse: {week: 1}, csp: {week: 1,
categories: \[6.B\]}, csa: {week: 1} } type: devops \-\--
:::

::: {.cell .markdown}
## Bash Tutorial

> A brief overview of Bash, on your way to becoming a Linux expert.
> `<mark>`{=html}When a computer boots up, a kernel (MacOS, Windows,
> Linux) is started`</mark>`{=html}. This kernel provides a shell, or
> `<mark>`{=html}terminal`</mark>`{=html}, that allows user to interact
> with a most basic set of commands. Typically, the casual user will not
> interact with the shell/terminal as a Desktop User Interface is
> started by the computer boot up process. To activate a shell directly,
> users will run a \"terminal\" through the Desktop. `<mark>`{=html}VS
> Code provides ability to activate \"terminal\"`</mark>`{=html} while
> in the IDE.
:::

::: {.cell .markdown}
## Variable Prerequisites

> Setup bash shell dependency variables for this page. Variables are one
> of the first aspects of programming. `<mark>`{=html}Variables have
> \"name\" and a \"value\"`</mark>`{=html}.

-   Hack Note: Change variables to match your student project.
:::

::: {.cell .markdown}
### Define variable

The following code cell `<mark>`{=html}defines 3 variables and assigns
each a value`</mark>`{=html}. There are some extra command, called a
HERE document, that write these variables to a file. This is so we can
use these variables over and over below.
:::

::: {.cell .code execution_count="1" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Dependency Variables, set to match your project directories

cat <<EOF > /tmp/variables.sh
export project_dir=$HOME/vscode  # change vscode to different name to test git clone
export project=\$project_dir/csa-pages  # change teacher to name of project from git clone
export project_repo="https://github.com/raunak2007/csa-pages.git"  # change to project of choice
EOF
```
:::

::: {.cell .markdown}
### Output the value of a variable

The following code cell `<mark>`{=html}outputs the value of the
variables`</mark>`{=html}, using the echo command. For visual
understanding in the output, each echo command provide a title before
the \$variable
:::

::: {.cell .code execution_count="2" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

# Output shown title and value variables
echo "Project dir: $project_dir"
echo "Project: $project"
echo "Repo: $project_repo"
```

::: {.output .stream .stdout}
    Project dir: /home/rumelaroy/vscode
    Project: /home/rumelaroy/vscode/csa-pages
    Repo: https://github.com/raunak2007/csa-pages.git
:::
:::

::: {.cell .markdown}
## Project Setup and Analysis with Bash Scripts

The bash scripts that follow automate what was done in the setup
procedures. The purpose of this is to show that many of the commands we
performed can be added to a script, then performed automatically.
:::

::: {.cell .markdown}
### Pull Code

> Pull code from GitHub to your machine. This is a `<mark>`{=html}bash
> script`</mark>`{=html}, a sequence of commands, that will create a
> project directory and add the \"project\" from GitHub to the vscode
> directory. There is conditional logic to make sure that clone only
> happen if it does not (!) exist. Here are some key elements in this
> code\...

-   cd command (change directory), remember this from terminal session
-   if statements (conditional statement, called selection statement by
    College Board), code inside only happens if condition is met
:::

::: {.cell .code execution_count="3" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

echo "Using conditional statement to create a project directory and project"

cd ~    # start in home directory

# Conditional block to make a project directory
if [ ! -d $project_dir ]
then 
    echo "Directory $project_dir does not exists... makinng directory $project_dir"
    mkdir -p $project_dir
fi
echo "Directory $project_dir exists." 

# Conditional block to git clone a project from project_repo
if [ ! -d $project ]
then
    echo "Directory $project does not exists... cloning $project_repo"
    cd $project_dir
    git clone $project_repo
    cd ~
fi
echo "Directory $project exists." 
```

::: {.output .stream .stdout}
    Using conditional statement to create a project directory and project
    Directory /home/rumelaroy/vscode exists.
    Directory /home/rumelaroy/vscode/csa-pages exists.
:::
:::

::: {.cell .markdown}
### Look at files Github project

> All computers contain files and directories. The clone brought more
> files from cloud to your machine. Review the bash shell script,
> observe the commands that show and interact with files and
> directories. These were used during setup.

-   \"ls\" lists computer files in Unix and Unix-like operating systems
-   \"cd\" offers way to navigate and change working directory
-   \"pwd\" print working directory
-   \"echo\" used to display line of text/string that are passed as an
    argument
:::

::: {.cell .code execution_count="4" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

echo "Navigate to project, then navigate to area wwhere files were cloned"
cd $project
pwd

echo ""
echo "list top level or root of files with project pulled from github"
ls
```

::: {.output .stream .stdout}
    Navigate to project, then navigate to area wwhere files were cloned
    /home/rumelaroy/vscode/csa-pages

    list top level or root of files with project pulled from github
    Gemfile
    Gemfile.lock
    LICENSE
    Makefile
    README.md
    _config.yml
    _data
    _includes
    _layouts
    _notebooks
    _posts
    _site
    aboutme.md
    activate.sh
    hangman.md
    images
    index.md
    indexBlogs.md
    scripts
    styles.css
    theme-changer.md
    timebox.md
:::
:::

::: {.cell .markdown}
### Look at file list with hidden and long attributes

> Most linux commands have options to enhance behavior. The enhanced
> listing below shows permission bits, owner of file, size and date.

[ls reference](https://www.rapidtables.com/code/linux/ls.html)
:::

::: {.cell .code execution_count="5" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

echo "Navigate to project, then navigate to area wwhere files were cloned"
cd $project
pwd

echo ""
echo "list all files in long format"
ls -al   # all files -a (hidden) in -l long listing
```

::: {.output .stream .stdout}
    Navigate to project, then navigate to area wwhere files were cloned
    /home/rumelaroy/vscode/csa-pages

    list all files in long format
    total 116
    drwxr-xr-x 12 rumelaroy rumelaroy 4096 Aug 19 13:42 .
    drwxr-xr-x 30 rumelaroy rumelaroy 4096 Aug 17 08:49 ..
    drwxr-xr-x  8 rumelaroy rumelaroy 4096 Aug 19 15:18 .git
    drwxr-xr-x  3 rumelaroy rumelaroy 4096 Aug 17 08:49 .github
    -rw-r--r--  1 rumelaroy rumelaroy  104 Aug 17 08:49 .gitignore
    -rw-r--r--  1 rumelaroy rumelaroy  122 Aug 18 08:58 Gemfile
    -rw-r--r--  1 rumelaroy rumelaroy 7294 Aug 17 08:51 Gemfile.lock
    -rw-r--r--  1 rumelaroy rumelaroy 1081 Aug 17 08:49 LICENSE
    -rw-r--r--  1 rumelaroy rumelaroy 3115 Aug 17 18:03 Makefile
    -rw-r--r--  1 rumelaroy rumelaroy 5798 Aug 17 08:49 README.md
    -rw-r--r--  1 rumelaroy rumelaroy 1388 Aug 19 11:03 _config.yml
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 17 08:49 _data
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 19 13:47 _includes
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 17 08:49 _layouts
    drwxr-xr-x  3 rumelaroy rumelaroy 4096 Aug 19 15:07 _notebooks
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 17 17:26 _posts
    drwxr-xr-x  8 rumelaroy rumelaroy 4096 Aug 19 15:14 _site
    -rw-r--r--  1 rumelaroy rumelaroy  511 Aug 19 13:48 aboutme.md
    -rwxr-xr-x  1 rumelaroy rumelaroy 1291 Aug 17 08:49 activate.sh
    -rw-r--r--  1 rumelaroy rumelaroy   66 Aug 18 09:28 hangman.md
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 19 13:42 images
    -rw-r--r--  1 rumelaroy rumelaroy  239 Aug 19 12:41 index.md
    -rw-r--r--  1 rumelaroy rumelaroy  141 Aug 17 09:31 indexBlogs.md
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 17 08:49 scripts
    -rw-r--r--  1 rumelaroy rumelaroy 1270 Aug 19 12:53 styles.css
    -rw-r--r--  1 rumelaroy rumelaroy   69 Aug 19 12:45 theme-changer.md
    -rw-r--r--  1 rumelaroy rumelaroy   67 Aug 18 09:12 timebox.md
:::
:::

::: {.cell .code execution_count="6" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

echo "Look for posts"
export posts=$project/_posts  # _posts inside project
cd $posts  # this should exist per fastpages
pwd  # present working directory
ls -l  # list posts
```

::: {.output .stream .stdout}
    Look for posts
    /home/rumelaroy/vscode/csa-pages/_posts
    total 20
    -rw-r--r-- 1 rumelaroy rumelaroy 1812 Aug 17 08:49 2023-08-15-Tools_Sprint.md
    -rw-r--r-- 1 rumelaroy rumelaroy 4397 Aug 17 08:49 2023-08-16-Tools_Equipment.md
    -rw-r--r-- 1 rumelaroy rumelaroy 1853 Aug 18 08:41 2023-08-17-Freeform-Pic.md
    -rw-r--r-- 1 rumelaroy rumelaroy  468 Aug 17 08:49 2023-08-21-GitHub_Pages.md
:::
:::

::: {.cell .code execution_count="7" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

echo "Look for notebooks"
export notebooks=$project/_notebooks  # _notebooks is inside project
cd $notebooks   # this should exist per fastpages
pwd  # present working directory
ls -l  # list notebooks
```

::: {.output .stream .stdout}
    Look for notebooks
    /home/rumelaroy/vscode/csa-pages/_notebooks
    total 36
    -rw-r--r-- 1 rumelaroy rumelaroy 16320 Aug 19 15:18 2023-08-16-linux_shell.ipynb
    -rw-r--r-- 1 rumelaroy rumelaroy  5415 Aug 17 08:49 2023-08-17-AP-pseudo-vs-python.ipynb
    -rw-r--r-- 1 rumelaroy rumelaroy  8615 Aug 17 08:49 2023-08-21-VSCode-GitHub_Pages.ipynb
:::
:::

::: {.cell .code execution_count="8" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

echo "Look for images in notebooks, print working directory, list files"
cd $notebooks/images  # this should exist per fastpages
pwd
ls -l
```

::: {.output .stream .stdout}
    Look for images in notebooks, print working directory, list files
:::

::: {.output .stream .stderr}
    bash: line 6: cd: /images: No such file or directory
:::

::: {.output .stream .stdout}
    /home/rumelaroy/vscode/csa-pages/_notebooks
    total 36
    -rw-r--r-- 1 rumelaroy rumelaroy 16320 Aug 19 15:18 2023-08-16-linux_shell.ipynb
    -rw-r--r-- 1 rumelaroy rumelaroy  5415 Aug 17 08:49 2023-08-17-AP-pseudo-vs-python.ipynb
    -rw-r--r-- 1 rumelaroy rumelaroy  8615 Aug 17 08:49 2023-08-21-VSCode-GitHub_Pages.ipynb
:::
:::

::: {.cell .markdown}
### Look inside a Markdown File

> \"cat\" reads data from the file and gives its content as output
:::

::: {.cell .code execution_count="9" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

echo "Navigate to project, then navigate to area wwhere files were cloned"

cd $project
echo "show the contents of README.md"
echo ""

cat README.md  # show contents of file, in this case markdown
echo ""
echo "end of README.md"
```

::: {.output .stream .stdout}
    Navigate to project, then navigate to area wwhere files were cloned
    show the contents of README.md

    ## Blog site using GitHub Pages and Jekyll
    > This site is intended for Students.   This is to record plans, complete hacks, and do work for your learnings.
    - This can be customized to support computer science as you work through pathway (JavaScript, Python/Flask, Java/Spring)
    - All tangible artifact work is in a _posts or in a _notebooks.  
    - Front matter (aka meta data) in ipynb and md files is used to organize information according to week and column in running web site.

    ## GitHub Pages
    All `GitHub Pages` websites are managed on GitHub infrastructure. GitHub uses `Jekyll` to tranform your content into static websites and blogs. Each time we change files in GitHub it initiates a GitHub Action that rebuilds and publishes the site with Jekyll.  
    - GitHub Pages is powered by: [Jekyll](https://jekyllrb.com/).
    - Publised teacher website: [nighthawkcoders.github.io/teacher](https://nighthawkcoders.github.io/teacher/)

    ## Preparing a Preview Site 
    In all development, it is recommended to test your code before deployment.  The GitHub Pages development process is optimized by testing your development on your local machine, prior to files on GitHub

    Development Cycle. For GitHub pages, the tooling described below will create a development cycle  `make-code-save-preview`.  In the development cycle, it is a requirement to preview work locally, prior to doing a VSCode `commit` to git.

    Deployment Cycle.  In the deplopyment cycle, `sync-github-action-review`, it is a requirement to complete the development cycle prior to doing a VSCode `sync`.  The sync triggers github repository update.  The action starts the jekyll build to publish the website.  Any step can have errors and will require you to do a review.

    ### WSL and/or Ubuntu installation requirements
    - The result of these step is Ubuntu tools to run preview server.  These procedures were created using [jekyllrb.com](https://jekyllrb.com/docs/installation/ubuntu/)
    - Run scripts in scripts directory of teacher repo: setup_ubuntu.sh and activate.sh.  Or, follow commands below.
    ```bash
    ## WSL/Ubuntu commands
    # sudo apt install, installs packages for Ubuntu
    echo "=== Ugrade Packages ==="
    sudo apt update
    sudo apt upgrade -y
    #
    echo "=== Install Ruby ==="
    sudo apt install -y ruby-full build-essential zlib1g-dev
    # 
    echo "=== Install Python ==="
    sudo apt-get install -y python3 python3-pip python-is-python3
    #    
    echo "=== Install Jupyter Notebook ==="
    sudo apt-get install -y jupyter-notebook

    # bash commands, install user requirements.
    echo "=== GitHub pages build tools  ==="
    export GEM_HOME="$HOME/gems"
    export PATH="$HOME/gems/bin:$PATH"
    echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
    echo "=== Gem install starting, thinking... ==="
    gem install jekyll bundler
    head -30 ./teacher/scripts/activate.sh
    echo "=== !!!Start a new Terminal!!! ==="
    ```

    ### MacOs installation requirements 
    - Ihe result of these step are MacOS tools to run preview server.  These procedures were created using [jekyllrb.com](https://jekyllrb.com/docs/installation/macos/). Run scripts in scripts directory of teacher repo: setup_macos.sh and activate_macos.sh.  Or, follow commands below.
    ```bash
    # MacOS commands
    # brew install, installs packages for MacOS
    echo "=== Ugrade Packages ==="
    brew update
    brew upgrade
    #
    echo "=== Install Ruby ==="
    brew install chruby ruby-install xz
    ruby-install ruby 3.1.3
    #
    echo "=== Install Python ==="
    brew install python
    #    
    echo "=== Install Jupyter Notebook ==="
    brew install jupyter

    # bash commands, install user requirements.
    export GEM_HOME="$HOME/gems"
    export PATH="$HOME/gems/bin:$PATH"
    echo '# Install Ruby Gems to ~/gems' >> ~/.zshrc
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.zshrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.zshrc
    echo "=== Gem install starting, thinking... ==="
    gem install jekyll bundler
    head -30 ./teacher/scripts/activate.sh
    echo "=== !!!Start a new Terminal!!! ==="
    ```

    ### Preview
    - The result of these step is server running on: http://0.0.0.0:4100/teacher/.  Regeneration messages will run in terminal on any save.  Press the Enter or Return key in the terminal at any time to enter commands.

    - Complete installation
    ```bash
    bundle install
    ```
    - Run Server.  This requires running terminal commands `make`, `make stop`, `make clean`, or `make convert` to manage the running server.  Logging of details will appear in terminal.   A `Makefile` has been created in project to support commands and start processes.

        - Start preview server in terminal
        ```bash
        cd ~/vscode/teacher  # my project location, adapt as necessary
        make
        ```

        - Terminal output of shows server address. Cmd or Ctl click http location to open preview server in browser. Example Server address message... 
        ```
        Server address: http://0.0.0.0:4100/teacher/
        ```

        - Save on ipynb or md activiates "regeneration". Refresh browser to see updates. Example terminal message...
        ```
        Regenerating: 1 file(s) changed at 2023-07-31 06:54:32
            _notebooks/2024-01-04-cockpit-setup.ipynb
        ```

        - Terminal message are generated from background processes.  Click return or enter to obtain prompt and use terminal as needed for other tasks.  Alway return to root of project `cd ~/vscode/teacher` for all "make" actions. 
            

        - Stop preview server, but leave constructed files in project for your review.
        ```bash
        make stop
        ```

        - Stop server and "clean" constructed files, best choice when renaming files to eliminate potential duplicates in constructed files.
        ```bash
        make clean
        ```

        - Test notebook conversions, best choice to see if IPYNB conversion is acting up.
        ```bash
        make convert
        ```

    end of README.md
:::
:::

::: {.cell .markdown}
## Env, Git and GitHub

> Env(ironment) is used to capture things like path to Code or Home
> directory. Git and GitHub is NOT Only used to exchange code between
> individuals, it is often used to exchange code through servers, in our
> case deployment for Website. All tools we use have a behind the scenes
> relationships with the system they run on (MacOS, Windows, Linus) or a
> relationship with servers which they are connected to (ie GitHub).
> There is an \"env\" command in bash. There are environment files and
> setting files (.git/config) for Git. They both use a key/value
> concept.

-   \"env\" show setting for your shell
-   \"git clone\" sets up a director of files
-   \"cd \$project\" allows user to move inside that directory of files
-   \".git\" is a hidden directory that is used by git to establish
    relationship between machine and the git server on GitHub.
:::

::: {.cell .code execution_count="10" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# This command has no dependencies

echo "Show the shell environment variables, key on left of equal value on right"
echo ""

env
```

::: {.output .stream .stdout}
    Show the shell environment variables, key on left of equal value on right

    SHELL=/bin/bash
    PYTHONUNBUFFERED=1
    NVM_INC=/home/rumelaroy/.nvm/versions/node/v18.16.0/include/node
    WSL2_GUI_APPS_ENABLED=1
    CONDA_EXE=/home/rumelaroy/anaconda3/bin/conda
    _CE_M=
    APPLICATION_INSIGHTS_NO_DIAGNOSTIC_CHANNEL=1
    WSL_DISTRO_NAME=Ubuntu
    ELECTRON_RUN_AS_NODE=1
    VSCODE_AMD_ENTRYPOINT=vs/workbench/api/node/extensionHostProcess
    NAME=raunak2007
    PWD=/home/rumelaroy/vscode/csa-pages/_notebooks
    NIX_PROFILES=/nix/var/nix/profiles/default /home/rumelaroy/.nix-profile
    LOGNAME=rumelaroy
    CONDA_ROOT=/home/rumelaroy/anaconda3
    CONDA_PREFIX=/home/rumelaroy/anaconda3
    PYDEVD_IPYTHON_COMPATIBLE_DEBUGGING=1
    HOME=/home/rumelaroy
    LANG=C.UTF-8
    WSL_INTEROP=/run/WSL/30221_interop
    LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
    WAYLAND_DISPLAY=wayland-0
    NIX_SSL_CERT_FILE=/etc/ssl/certs/ca-certificates.crt
    CONDA_PROMPT_MODIFIER=(base) 
    PYDEVD_USE_FRAME_EVAL=NO
    CLICOLOR=1
    VSCODE_L10N_BUNDLE_LOCATION=
    NVM_DIR=/home/rumelaroy/.nvm
    GEM_HOME=/home/rumelaroy/gems
    LESSCLOSE=/usr/bin/lesspipe %s %s
    VSCODE_HANDLES_SIGPIPE=true
    TERM=xterm-color
    _CE_CONDA=
    LESSOPEN=| /usr/bin/lesspipe %s
    USER=rumelaroy
    GIT_PAGER=cat
    PYTHONIOENCODING=utf-8
    CONDA_SHLVL=1
    DISPLAY=:0
    SHLVL=2
    NVM_CD_FLAGS=
    PAGER=cat
    VSCODE_CWD=/mnt/c/Users/rumelaroy/AppData/Local/Programs/Microsoft VS Code
    MPLBACKEND=module://matplotlib_inline.backend_inline
    CONDA_PYTHON_EXE=/home/rumelaroy/anaconda3/bin/python
    XDG_RUNTIME_DIR=/mnt/wslg/runtime-dir
    CONDA_DEFAULT_ENV=base
    WSLENV=VSCODE_WSL_EXT_LOCATION/up
    VSCODE_WSL_EXT_LOCATION=/mnt/c/Users/rumelaroy/.vscode/extensions/ms-vscode-remote.remote-wsl-0.81.0
    XDG_DATA_DIRS=/usr/local/share:/usr/share:/var/lib/snapd/desktop
    PATH=/home/rumelaroy/anaconda3/bin:/home/rumelaroy/.vscode-server/bin/6c3e3dba23e8fadc360aed75ce363ba185c49794/bin/remote-cli:/home/rumelaroy/.nix-profile/bin:/home/rumelaroy/.local/bin:/home/rumelaroy/.nvm/versions/node/v18.16.0/bin:/home/rumelaroy/gems/bin:/home/rumelaroy/gems/bin:/home/rumelaroy/gems/bin:/home/rumelaroy/gems/bin:/home/rumelaroy/gems/bin:/home/rumelaroy/gems/bin:/home/rumelaroy/anaconda3/bin:/home/rumelaroy/anaconda3/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/lib/wsl/lib:/mnt/c/Program Files/Eclipse Adoptium/jdk-17.0.7.7-hotspot/bin:/mnt/c/Program Files/Common Files/Oracle/Java/javapath:/mnt/c/Program Files (x86)/Common Files/Oracle/Java/javapath:/mnt/c/Python311/Scripts:/mnt/c/Python311:/mnt/c/Windows/system32:/mnt/c/Windows:/mnt/c/Windows/System32/Wbem:/mnt/c/Windows/System32/WindowsPowerShell/v1.0:/mnt/c/Windows/System32/OpenSSH:/mnt/c/Program Files (x86)/NVIDIA Corporation/PhysX/Common:/mnt/c/Program Files/NVIDIA Corporation/NVIDIA NvDLISR:/mnt/c/WINDOWS/system32:/mnt/c/WINDOWS:/mnt/c/WINDOWS/System32/Wbem:/mnt/c/WINDOWS/System32/WindowsPowerShell/v1.0:/mnt/c/WINDOWS/System32/OpenSSH:/Docker/host/bin:/mnt/c/ProgramData/chocolatey/bin:/mnt/c/Program Files/nodejs/node_modules:/mnt/c/Users/rumelaroy/AppData/Local/Microsoft/WindowsApps:/mnt/c/Users/rumelaroy/AppData/Local/Programs/Microsoft VS Code/bin:/mnt/c/Users/rumelaroy/AppData/Roaming/npm:/snap/bin
    VSCODE_NLS_CONFIG={"locale":"en","osLocale":"en","availableLanguages":{}}
    NVM_BIN=/home/rumelaroy/.nvm/versions/node/v18.16.0/bin
    HOSTTYPE=x86_64
    PULSE_SERVER=unix:/mnt/wslg/PulseServer
    VSCODE_HANDLES_UNCAUGHT_ERRORS=true
    VSCODE_IPC_HOOK_CLI=/mnt/wslg/runtime-dir/vscode-ipc-7732a6b2-be79-4316-b9a4-ed6ad6767933.sock
    _=/usr/bin/env
:::
:::

::: {.cell .code execution_count="11" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# Extract saved variables
source /tmp/variables.sh

cd $project

echo ""
echo "show the secrets of .git"
cd .git
ls -l

echo ""
echo "look at config file"
cat config
```

::: {.output .stream .stdout}

    show the secrets of .git
    total 56
    -rw-r--r--  1 rumelaroy rumelaroy   19 Aug 19 15:18 COMMIT_EDITMSG
    -rw-r--r--  1 rumelaroy rumelaroy  108 Aug 19 15:20 FETCH_HEAD
    -rw-r--r--  1 rumelaroy rumelaroy   21 Aug 17 08:49 HEAD
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 17 08:49 branches
    -rw-r--r--  1 rumelaroy rumelaroy  273 Aug 17 08:49 config
    -rw-r--r--  1 rumelaroy rumelaroy   73 Aug 17 08:49 description
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 17 08:49 hooks
    -rw-r--r--  1 rumelaroy rumelaroy 4703 Aug 19 15:18 index
    drwxr-xr-x  2 rumelaroy rumelaroy 4096 Aug 17 08:49 info
    drwxr-xr-x  3 rumelaroy rumelaroy 4096 Aug 17 08:49 logs
    drwxr-xr-x 71 rumelaroy rumelaroy 4096 Aug 19 15:20 objects
    -rw-r--r--  1 rumelaroy rumelaroy  112 Aug 17 08:49 packed-refs
    drwxr-xr-x  5 rumelaroy rumelaroy 4096 Aug 17 08:49 refs

    look at config file
    [core]
    	repositoryformatversion = 0
    	filemode = true
    	bare = false
    	logallrefupdates = true
    [remote "origin"]
    	url = https://github.com/raunak2007/csa-pages.git
    	fetch = +refs/heads/*:refs/remotes/origin/*
    [branch "main"]
    	remote = origin
    	merge = refs/heads/main
:::
:::

::: {.cell .markdown}
## Advanced Student Request - Make a file in Bash

> This example was requested by a student (Jun Lim, CSA). The request
> was to make jupyer file using bash, I adapted the request to markdown.
> This type of thought will have great extrapolation to coding and
> possibilities of using List, Arrays, or APIs to build user interfaces.
> JavaScript is a language where building HTML is very common.

> To get more interesting output from terminal, this will require using
> something like mdless (<https://github.com/ttscoff/mdless>). This
> enables see markdown in rendered format.

-   On Desktop [Install PKG from
    MacPorts](https://www.macports.org/install.php)
-   In Terminal on MacOS
    -   [Install ncurses](https://ports.macports.org/port/ncurses/)
    -   `gem install mdless`

> Output of the example is much nicer in \"jupyter\"
:::

::: {.cell .code execution_count="12" vscode="{\"languageId\":\"shellscript\"}"}
``` python
%%script bash

# This example has error in VSCode, it run best on Jupyter
cd /tmp

file="sample.md"
if [ -f "$file" ]; then
    rm $file
fi

tee -a $file >/dev/null <<EOF
# Show Generated Markdown
This introductory paragraph and this line and the title above are generated using tee with the standard input (<<) redirection operator.
- This bulleted element is still part of the tee body.
EOF

echo "- This bulleted element and lines below are generated using echo with standard output (>>) redirection operator." >> $file
echo "- The list definition, as is, is using space to seperate lines.  Thus the use of commas and hyphens in output." >> $file
actions=("ls,list-directory" "cd,change-directory" "pwd,present-working-directory" "if-then-fi,test-condition" "env,bash-environment-variables" "cat,view-file-contents" "tee,write-to-output" "echo,display-content-of-string" "echo_text_>\$file,write-content-to-file" "echo_text_>>\$file,append-content-to-file")
for action in ${actions[@]}; do  # for loop is very similar to other language, though [@], semi-colon, do are new
  action=${action//-/ }  # convert dash to space
  action=${action//,/: } # convert comma to colon
  action=${action//_text_/ \"sample text\" } # convert _text_ to sample text, note escape character \ to avoid "" having meaning
  echo "    - ${action//-/ }" >> $file  # echo is redirected to file with >>
done

echo ""
echo "File listing and status"
ls -l $file # list file
wc $file   # show words
mdless $file  # this requires installation, but renders markown from terminal

rm $file  # clean up termporary file
```

::: {.output .stream .stdout}

    File listing and status
    -rw-r--r-- 1 rumelaroy rumelaroy 809 Aug 19 15:20 sample.md
     15 132 809 sample.md

    Show Generated Markdown ========================================================

    This introductory paragraph and this line and the title above are generated
    using tee with the standard input (<<) redirection operator.
    - This bulleted element is still part of the tee body.
    - This bulleted element and lines below are generated using echo with standard
    output (>>) redirection operator.
    - The list definition, as is, is using space to seperate lines. Thus the use of
    commas and hyphens in output.
          - ls: list directory
          - cd: change directory
          - pwd: present working directory
          - if then fi: test condition
          - env: bash environment variables
          - cat: view file contents
          - tee: write to output
          - echo: display content of string
          - echo "sample text" >$file: write content to file
          - echo "sample text" >>$file: append content to file
:::
:::

::: {.cell .markdown}
## Hack Preparation. {#hack-preparation}

> Review Tool Setup Procedures and think about some thing you could
> verify through a Shell notebook.

-   Come up with your own student view of this procedure to show your
    tools are installed. It is best that you keep the few things you
    understand, add things later as you start to understand them.
-   Name and create blog notes on some Linux commands you will use
    frequently.
-   Is there anything we use to verify tools we installed? Review
    versions?
-   How would you update a repository? Use the git command line?
:::

::: {.cell .markdown vscode="{\"languageId\":\"shellscript\"}"}
:::
