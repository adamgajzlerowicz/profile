export PATH="$PATH:$HOME/.rvm/bin" # Add RVM to PATH for scripting
[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*

set_prompt () {
    ExitCode=$?

    Red='\[\e[01;31m\]'
    Green='\[\e[01;32m\]'

    Accent="$Green"
    if [[ $EUID == 0 ]]; then
        Accent="$Red"
    fi

    Blue='\[\e[01;34m\]'
    White='\[\e[01;37m\]'
    Reset='\[\e[00m\]'

    PS1=""


    #prompt
    PS1+="$Accent["
    if [[ $EUID != 0 ]]; then
        PS1+="$White\\u$Blue@"
    fi

    PS1+="$White\\h$Blue:$White\\w$Accent] \\\$$Reset "
}
PROMPT_COMMAND='set_prompt'
