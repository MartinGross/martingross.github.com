Install Homebrew (http://mxcl.github.io/homebrew/)
Show the directory of home-brew: echo `brew --prefix`
Usually it is /usr/local

Then to install rbenv & ruby-build

$ brew update
$ brew install rbenv
$ brew install ruby-build

To use Homebrew's directories rather than ~/.rbenv add to your profile:
  export RBENV_ROOT=/usr/local/var/rbenv

To enable shims and autocompletion add to your profile:
  if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi

rbenv specific stuff can be found in /usr/local/var/rbenv/

List all available ruby versions
$ rbenv install --list

$ rbenv rehash
Run this command after you install a new version of Ruby, or install a gem that provides commands.