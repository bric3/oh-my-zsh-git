oh-my-git _for_ oh-my-zsh
=========================

This plugin is an opinionated git prompt status, tailored for [**oh-my-zsh**](https://github.com/robbyrussell/oh-my-zsh). It is based on the work of [fabulous work](https://github.com/arialdomartini/oh-my-git/) of Arialdo Martini. 

This derivative fork is taken from my pull request on his project [there](https://github.com/arialdomartini/oh-my-git/pull/22).


## Abstract

This new git information script (`oh-my-git.plugin.zsh`)
   * is not rely on a prompt shell anymore
   * is using configurable color codes
   * doesn't leak variables
   * does not depend on external configuration
   * offers configurable color codes per symbol
   * has a more understandable name, that can be easily used in another context (I'm using it in my own crafted oh-my-zsh theme, though it's named `oh-my-git.plugin.zsh`)
   * offers suffix and prefix config
   * enables toggling of the display of the git repository symbol (`display_git_symbol`)
   * enables to toggle if empty spaces for _off_ flags will be displayed (`use_color_off=false` and flag is off, toggable with `print_unactive_flags_space`)
   * enables toggling per git repository config `git config --get oh-my-zsh.hide-status`
   * displays current git action (`REBASE-i`, `REBASE-m`, `REBASE`, `AM/REBASE`, `MERGING`, `BISECTING`, `CHERRY-PICKING`)

## Install

This install assume the current shell is **ZSH** with [**oh-my-zsh**](https://github.com/robbyrussell/oh-my-zsh) already installed.

Install a clone of this repository in oh-my-zsh plugin [custom folder](https://github.com/robbyrussell/oh-my-zsh/wiki/Customization). *Note it is possible to change the default custom directory of oh-my-zsh by redefining the `$ZSH_CUSTOM` in the `.zshrc` *

```bash
git clone git@github.com:bric3/oh-my-git-4-oh-my-zsh.git $ZSH_CUSTOM/oh-my-git
```

This will make _oh-my-git_ available as a plugin for _oh-my-zsh_. Now you still need to activate it. In your `.zshrc` just activate the plugin by adding `oh-my-git` to the `plugins` variable :

```
plugins=(
 # custom plugins
 git2
 oh-my-git

 # bundled plugins
 github
 osx
 mosh
 ...
```

And finally use the main function in your theme. For example to place it in the right part of your theme use the `RPROMPT` environment variable : 

```
RPROMPT='$(oh_my_git_info)'
```

## Demo

A rather long demo with [asciinema](https://asciinema.org/a/10426)

