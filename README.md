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
