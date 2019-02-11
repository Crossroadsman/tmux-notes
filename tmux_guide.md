Tmux
====

Anatomy of a Tmux Session
-------------------------
Tmux has 'sessions', 'windows', and 'panes'.

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

or from inside a session:
`CTRL-b s`

Attach to a session

```console
$ tmux a -t <session_name>|<session_id>
```

Note `a` is an optional shorthand for `attach`

Name a session:
`CTRL-b $`

Kill a session:

```console
$ tmux kill-session -t <session_name>|<session_id>
```

Windows
-------

Create a new window:
`<prefix> c`

Rename current window:
`<prefix> ,`

Switch windows:
- cycle next: `<prefix> n`
- cycle previous: `<prefix> p`
- toggle last selected: `<prefix> l`
- list all windows (and sessions?): `<prefix> w`
- switch to window #: `<prefix> <number>`
- find window: `<prefix> f`


Panes
-----

Split vertically (i.e., turn pane into two vertically-stacked panes aka create a horizontal divider):
`CTRL-b "`

Split horizontally (turn pane into two horizontally side-by-side panes aka create a vertical divider):
`CTRL-b %`

Navigate to another pane:
`CTRL-b <arrow_key>`

Cycle through panes:
`CTRL-b o`

Switch between current and previous pane:
`CTRL-b ;`

Kill current pane:
`CTRL-b x`

Toggle pane zoom:
`CTRL-b z`

Server
------

Kill the tmux server, along with all sessions:
```console
$ tmux kill-server
```

Customisation
-------------

It's possible to customise tmux, including replacing the `CTRL-b` keystroke (e.g.,
`CTRL-a`).

The config file lives at `~/.tmux.conf`. To rebind the prefix keystroke, add the 
following line:
```
set -g prefix Ctrl-a
```
