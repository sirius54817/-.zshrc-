#
# ~/.bashrc
#

# If not running interactively, don't do anything
[[ $- != *i* ]] && return

alias ls='ls --color=auto'
alias grep='grep --color=auto'
PS1='[\u@\h \W]\$ '
export PATH=$PATH:/opt/android-sdk/platform-tools


export PATH=$PATH:/home/sirius/.spicetify

# pnpm
export PNPM_HOME="/home/sirius/.local/share/pnpm"
case ":$PATH:" in
  *":$PNPM_HOME:"*) ;;
  *) export PATH="$PNPM_HOME:$PATH" ;;
esac
# pnpm end

PATH=~/.console-ninja/.bin:$PATH
#
#
# ~/.zshrc
#

# If not running interactively, don't do anything
[[ $- != *i* ]] && return

alias ls='ls --color=auto'
alias grep='grep --color=auto'

# --- Random color "~" prompt ---
random_color_prompt() {
    local colors=("red" "green" "yellow" "blue" "magenta" "cyan" "white")
    local index=$(( RANDOM % ${#colors[@]} ))
    PROMPT="%F{${colors[$index]}}~%f "
}
random_color_prompt

autoload -Uz add-zsh-hook
add-zsh-hook precmd random_color_prompt
# --- End prompt section ---

# --- Fastfetch ---
if command -v fastfetch >/dev/null 2>&1; then
    fastfetch
fi
# --- End Fastfetch ---

# --- Rainbow Output Wrapper (safe check for lolcat) ---
rainbow() {
    if command -v lolcat >/dev/null 2>&1; then
        "$@" | lolcat
    else
        "$@"
    fi
}
# Example aliases with rainbow
alias cat='rainbow cat'
alias dmesg='rainbow dmesg'
alias figlet='rainbow figlet'
# --- End Rainbow ---

export PATH=$PATH:/opt/android-sdk/platform-tools
export PATH=$PATH:/home/sirius/.spicetify

# pnpm
export PNPM_HOME="/home/sirius/.local/share/pnpm"
case ":$PATH:" in
  *":$PNPM_HOME:"*) ;;
  *) export PATH="$PNPM_HOME:$PATH" ;;
esac
# pnpm end

PATH=~/.console-ninja/.bin:$PATH
