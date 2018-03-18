oh-my-zsh-git
=============

This plugin is an opinionated git prompt status, tailored for [**oh-my-zsh**](https://github.com/robbyrussell/oh-my-zsh). It is based on the work of [fabulous work](https://github.com/arialdomartini/oh-my-git/) of Arialdo Martini, but has been completely rewritten to avoid shortcoming and enable more features na despecially a nice oh-my-zsh integration.

In other word it is _oh_my_git_ for _oh_my_zsh_.

This derivative fork is taken from my pull request on his project [there](https://github.com/arialdomartini/oh-my-git/pull/22).

![oh-my-git in action](http://bric3.github.io/oh-my-zsh-git/images/oh-my-git.in.action.png)

## Reading the abstract

This new git information script (`oh-my-git.plugin.zsh`) has a few bullet points

   * Show more information than usual git prompt status function here and there, thanks to Arialdo Martini for that
   * Configurable color and symbols (or string)
   * Configurable suffix and prefix
   * Toggleable per git repository (`git config --get oh-my-zsh.hide-status`)
   * Toggleable git repository symbol (`display_git_symbol`)
   * Git _off_ flags (like content in stash or untracked files) can be either displayed or not (`use_color_off`) Toggleable empty spaces when git flag is on or off  (`print_unactive_flags_space`)
   * Git _off_ flags can be ommited in the status (with both `use_color_off=false` and `print_unactive_flags_space=false`)
   * Showing current git action (`REBASE-i`, `REBASE-m`, `REBASE`, `AM/REBASE`, `MERGING`, `BISECTING`, `CHERRY-PICKING`)
   * External configuration is optional, defaults are already configured

On a technical ground 

   * The shell script file and function are more human compatible. And this layout is directly working with oh-my-zsh plugins layout.
   * While designed with oh-my-zsh in mind it is does not depend on a specific shell
   * Doesn't leak variables


## Install the git prompt status

This install assume the current shell is **ZSH** with [**oh-my-zsh**](https://github.com/robbyrussell/oh-my-zsh) already installed.

Install a clone of this repository in oh-my-zsh plugin [custom folder](https://github.com/robbyrussell/oh-my-zsh/wiki/Customization). *Note it is possible to change the default custom directory of oh-my-zsh by redefining the `$ZSH_CUSTOM` in the `.zshrc` *

```bash
mkdir -p $ZSH_CUSTOM/plugins
git clone git@github.com:bric3/oh-my-git-4-oh-my-zsh.git $ZSH_CUSTOM/plugins/oh-my-git
```

This will make _oh-my-git_ available as a plugin for _oh-my-zsh_. Now you still need to activate it. In your `.zshrc` just activate the plugin by adding `oh-my-git` to the `plugins` variable :

```bash
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

Finally use the main function of the plugin `oh_my_git_info` in the variables in your theme `PROMPT` or `RPROMPT`. For example to place it in the right part of your theme use the `RPROMPT` environment variable : 

```bash
RPROMPT='$(oh_my_git_info)'
```


## Customize it

In order to customize either the symbol, the color or if some symbol should be displayed define on of these varaible in your oh-my-zsh theme.

For example in your theme set the following variables to have a prompt info that will look like : `[(master ᄉ origin)]`

```bash
# oh-my-git config
omg_prefix=" %{%B%F{green}%}[%{%f%k%b%}"
omg_suffix="%{%B%F{green}%}]%{%f%k%b%}"

display_git_symbol=false
display_git_current_action=left
print_unactive_flags_space=false
```

Here is the possible variables and flags with their default value


### Options

option variable                    | value
---------------------------------- | ----------
display_has_upstream               | `false`
display_tag                        | `false`
display_tag_name                   | `true`
use_color_off                      | `false`
print_unactive_flags_space         | `true`
display_git_symbol                 | `true`
display_git_current_action         | `false`

### Symbols and related colors

symbol and color variable          | value
---------------------------------- | ----------
is_a_git_repo_symbol               | `±`
is_a_git_repo_color                | `$violet`
has_untracked_files_symbol         | `∿`
has_untracked_files_color          | `$red`
has_adds_symbol                    | `+`
has_adds_color                     | `$yellow`
has_deletions_symbol               | `-`
has_deletions_color                | `$red`
has_deletions_cached_symbol        | `✖`
has_deletions_cached_color         | `$yellow`
has_modifications_symbol           | `✎`
has_modifications_color            | `$red`
has_modifications_cached_symbol    | `☲`
has_modifications_cached_color     | `$yellow`
ready_to_commit_symbol             | `→`
ready_to_commit_color              | `$green`
is_on_a_tag_symbol                 | `⌫`
is_on_a_tag_color                  | `$yellow`
needs_to_merge_symbol              | `ᄉ`
needs_to_merge_color               | `$yellow`
has_upstream_symbol                | `⇅`
has_upstream_color                 | `$on`
has_no_upstream_symbol             | ` ⃢`
has_no_upstream_color              | `$on`
detached_symbol                    | `⚯`
detached_color                     | `$red`
detached_current_commit_color      | `$on`
can_fast_forward_symbol            | `»`
can_fast_forward_color             | `$on`
has_diverged_symbol                | `Ⴤ`
has_diverged_color                 | `$red`
rebase_tracking_branch_symbol      | `↶`
rebase_tracking_branch_color       | `$reset`
merge_tracking_branch_symbol       | `ᄉ`
merge_tracking_branch_color        | `$reset`
should_push_symbol                 | `↑`
should_push_color                  | `$on`
has_stashes_symbol                 | `★`
has_stashes_color                  | `$yellow`
commits_behind_symbol              | `-`
commits_behind_color               | `$reset`
commits_ahead_symbol               | `+`
commits_ahead_color                | `$reset`
current_branch_color               | `$green`
tag_name_color                     | `$yellow`


### Default colors 

For the ZSH shell, the default values are the [ZSH prompt escape sequences](http://zsh.sourceforge.net/Doc/Release/Prompt-Expansion.html) which are correctly interpreted to match the terminal width.

display variable                   | value
---------------------------------- | ----------
on                                 | `%B`
off                                | `%b`
green                              | `%F{green}`
red                                | `%F{red}`
violet                             | `%F{magenta}`
yellow                             | `%F{yellow}`
reset                              | `%{%f%k%b%}`



## Show a demo

A rather long demo with [asciinema](https://asciinema.org/a/10426)

[![asciicast](https://asciinema.org/a/10426.png)](https://asciinema.org/a/10426)
