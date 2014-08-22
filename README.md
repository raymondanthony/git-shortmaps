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

You may also add your own mappings to `~/.git-shortmaps`, which is sourced
automatically and will take precedence over any other mappings.


## Usage
By default, the following mappings are available, each with tab completion:

* `a` - git add
* `A` - git add -A
* `b` - git branch
* `bv` - git branch -v
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
* `L` - git log --show-signature
* `Ld` - git log --show-signature --decorate
* `Lf` - git log --show-signature --first-parent
* `Lg` - git log --show-signature --graph
* `Lgd` - git log --show-signature --graph --decorate
* `Lm` - git log --show-signature --merges
* `Ln` - git log --show-signature --no-merges
* `m` - git merge
* `ma` - git merge --abort
* `p` - git push
* `P` - git pull
* `Pr` - git pull --rebase=preserve
* `Prp` - git pull --rebase=preserve && git push
* `R` - git rebase
* `Ri` - git rebase --interactive
* `Ra` - git rebase --abort
* `Rc` - git rebase --continue
* `s` - git status --short
* `S` - git stash
* `Sa` - git stash apply
* `Sl` - git stash list
* `Sp` - git stash pop
* `Ss` - git stash show
* `t` - execute tig
* `T` - git tag
* `-` - git checkout -
* `--` - `cd` to root dir of repository
* `?` - display all shortmaps

The shortmaps may only be used within a Git repository; otherwise, they will
invoke the actual command on the system.

If a shortmap conflicts with an existing command on your system, then you
may either unalias the map, or use `command X` to invoke the system command
`X`.


## Configuration
The file format is as follows:

```
key completion :cmd
key completion |cmd
key completion cmd
```

If `cmd` contains a colon (`:`) prefix, the command will be prefixed with
`git`. If prefixed with a pipe (`|`), the command will be sent to `eval`
(needed for certain features like subshells). Commands without either prefix
will be executed normally.


## License
This program is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option)
any later version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
more details.

