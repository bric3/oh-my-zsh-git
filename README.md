oh-my-git-4-oh-my-zsh
=====================

An opinionated git prompt status, tailored for oh-my-zsh

Based on the work of fabulous work of Arialdo Martini
https://github.com/arialdomartini/oh-my-git/

This derivative fork is taken from my pull request on his project here : https://github.com/arialdomartini/oh-my-git/pull/22

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
