git-shortmaps provides very concise (one- or two-character), user-configurable
commands for Git with support for Bash tab completion.

# shortmaps / Bash Completion
The `bash_completion` file contains Bash completion for custom commands and
"shortmappings", which provide single-character aliases to common Git commands.

## Setup
Source the `bash_completion` file (e.g. place in `.bashrc` or in
`/etc/bash_completion.d/` on Debian systems), with the path to the provided
`shortmaps` file as the only argument:

```
$ . bash_completion ./shortmaps
```

You may also add your own mappings to `~/.git-shortmaps`.

## Usage
By default, the following mappings are available, each with tab completion:

* `a` - git add
* `A` - git add -A
* `b` - git bisect
* `bs` - git bisect start
* `bg` - git bisect good
* `bb` - git bisect bad
* `br` - git bisect reset
* `c` - git commit
* `C` - git commit -am
* `co` - git checkout
* `d` - git diff
* `f` - git fetch
* `m` - git merge
* `p` - git push
* `P` - git pull
* `R` - git rebase
* `Ri` - git rebase --interactive
* `Ra` - git rebase --abort
* `Rc` - git rebase --continue
* `s` - git status
* `S` - git stash
* `t` - execute tig
* `T` - git tag
* `-` - git checkout -
* `--` - `cd` to root dir of repository

The shortmaps may only be used within a git repository. Otherwise, they will
invoke the actual command on the system.

If a command conflicts with an existing command on your system (e.g. `bg`), wrap
the command in quotes to invoke the actual command. For example:

```shell
$ 'bg'  # invoke actual 'bg' command rather than shortmap
```

## Configuration
The file format is as follows:

```
KEY COMPLETION :CMD
KEY COMPLETION |CMD
KEY COMPLETION CMD
```

If `CMD` contains a colon (`:`) prefix, the command will be prefixed with `git`. If
prefixed with a pipe (`|`), the command will be sent to `eval` (needed for
certain features like subshells). Commands without either prefix will be
executed normally.
