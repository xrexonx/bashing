# bashing
Clouding my ~/.bash_profile for future self migration purposes. IYKWIM

```sh
# Rexon A. De los Reyes
# Feb 22, 2016
# Bashing

# Alias
# Open bash on vim
alias openbash='sudo vi ~/.bash_profile';
alias srcbash='source .bash_profile';

# Clear Screen
alias cc='clear screen';

# Directory alias
alias la='ls -lah $LS_COLOR';


# CD AND LA. I never use 'cd' anymore...
function cl(){ cd "$@" && la; }


# shorten path directory
export PS1='\u:\W \$ ';

# Shortcut to htdocs folder.
alias htdocs='cd /Applications/MAMP/htdocs/';

# Edit vhosts
alias vhosts='sudo vi /Applications/MAMP/conf/apache/extra/httpd-vhosts.conf';

# Edit hosts
alias hosts='sudo vi /etc/hosts'

# Git aliases by rexon
alias gs='git status';
alias gpl='git pull';
alias gps='git push';
alias gplo='git pull origin';
alias gpso='git push origin';
alias ga.='git add .';
alias gaa='git add --all';
alias gcm='git commit -m';
alias gc='git checkout';
alias gcb='git checkout -b';
alias gb='git branch';
alias gf='git fetch origin';
alias gl='git log';
alias gm='git merge origin';
alias gd='git diff';

# git clone and cd into it. yeah
function gclone {
    url=$1;
    reponame=$(echo $url | awk -F/ '{print $NF}' | sed -e 's/.git$//');
    git clone $url $reponame;
    cd $reponame;
}

# Boot up PHPStorm
alias ps='open -a /Applications/PHPStorm.app';

# Boot up WebStorm
alias ws='open -a /Applications/WebStorm.app';

# cd back - usage cdn n  where n is number of folder you want to traverse
function cdn(){ for i in `seq $1`; do cd ..; done;}


# Extract based upon file ext
function ex() {
     if [ -f "$1" ] ; then
         case "$1" in
             *.tar.bz2)   tar xvjf "$1"        ;;
             *.tar.gz)    tar xvzf "$1"     ;;
             *.bz2)       bunzip2 "$1"       ;;
             *.rar)       unrar x "$1"     ;;
             *.gz)        gunzip "$1"     ;;
             *.tar)       tar xvf "$1"        ;;
             *.tbz2)      tar xvjf "$1"      ;;
             *.tgz)       tar xvzf "$1"       ;;
             *.jar)       jar xf "$1"       ;;
             *.zip)       unzip "$1"     ;;
             *.Z)         uncompress "$1"  ;;
             *.7z)        7z x "$1"    ;;
             *)           echo "'$1' cannot be extracted via >extract<" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

# mkcdir : Make directory and cd into it
function mkcdir () {
    mkdir -p -- "$1" &&
      cd -P -- "$1"
}

# Use MAMP version of PHP
# PHP_VERSION=`ls /Applications/MAMP/bin/php/ | sort -n | tail -1`
# export PATH=/Applications/MAMP/bin/php/${PHP_VERSION}/bin:$PATH

# Using php5.4.42 now for Symfony 2 compatibility purpose.
export PATH=/Applications/MAMP/bin/php/php5.4.42/bin:$PATH 

# Export mongoDB
export PATH=mongodb/bin:$PATH

# Generic
export PATH="$PATH":~/.node/bin

# Install npm packages globally without sudo
NPM_PACKAGES="${HOME}/.npm-packages"

PATH="$NPM_PACKAGES/bin:$PATH"

# Unset manpath so we can inherit from /etc/manpath via the `manpath` command
unset MANPATH # delete if you already modified MANPATH elsewhere in your config
export MANPATH="$NPM_PACKAGES/share/man:$(manpath)"


# end

```
## License
MIT © [Rexon A. De los Reyes](http://xrexonx.github.io)


#### Thanks and enjoy. Godspeed!
