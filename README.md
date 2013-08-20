git-shortmaps provides very concise (mostly one- and two-character),
user-configurable commands for Git with support for Bash tab completion.

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
* `B` - git bisect
* `Bs` - git bisect start
* `Bg` - git bisect good
* `Bb` - git bisect bad
* `Br` - git bisect reset
* `c` - git commit
* `ca` - git commit --amend
* `co` - git checkout
* `C` - git commit -am
* `CS` - git commit -S -am
* `d` - git diff
* `ds` - git diff --stat
* `f` - git fetch
* `lh` - git log --oneline --decorate --color | head
* `m` - git merge
* `ma` - git merge --abort
* `p` - git push
* `P` - git pull
* `Pr` - git pull --rebase
* `Prp` - git pull --rebase && git push
* `R` - git rebase
* `Ri` - git rebase --interactive
* `Ra` - git rebase --abort
* `Rc` - git rebase --continue
* `s` - git status --short
* `S` - git stash
* `t` - execute tig
* `T` - git tag
* `-` - git checkout -
* `--` - `cd` to root dir of repository

The shortmaps may only be used within a git repository; otherwise, they will
invoke the actual command on the system.

If a shortmap conflicts with an existing command on your system, then you may
wrap the command in quotes to invoke the actual command rather than the
shortmap (e.g. `'c'` to invoke `which c` rather than the shortmap `c`).

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
