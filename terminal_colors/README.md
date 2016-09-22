```bash
function find_git_branch {
    local git_branch='';
    until [ $PWD -ef /  ]; do
        if [ -d '.git' ]; then
            git_branch=`git describe --contains --all HEAD|tr -s '\n'`
            if [ -z '$git_branch' ]; then
                branch='✔ unknow'
            fi
            echo "✔ $git_branch"
            return
        fi
        cd ../
    done
}

export CLICOLO=1
LSCOLORS=gxfxcxdxbxegedabagacad
export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;36m\]\w\[\033[00m\]\[\033[01;31m\] $(find_git_branch)\[\033[00m\]\n>> '
export TERM=xterm-color
```
