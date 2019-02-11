Tmux
====

Sessions
--------

Start a new session:

```console
$ tmux new -s <session_name>
```

Note the `-s` argument is optional, omit to create an unnameed session.

Detach from session:

`CTRL+b d`

List sessions:
```console
$ tmux ls
```

Attach to a session

```console
$ tmux a -t <session_name>|<session_id>
```

Note `a` is an optional shorthand for `attach`

Kill a session:

```console
$ tmux kill-session -t <session_name>|<session_id>
```

Panes
-----

Split horizontally (i.e., create a horizontal divider):
`CTRL-b "`

Split vertically (create a vertical divider):
`CTRL-b %`

Navigate to another pane:
`CTRL-b <arrow_key>`

Cycle through panes:
`CTRL-b o`

Switch between current and previous pane:
`CTRL-b ;`

Kill current pane:
`CTRL-b x`

Server
------

Kill the tmux server, along with all sessions:
```console
$ tmux kill-server
```
