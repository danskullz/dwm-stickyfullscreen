# stickyfullscreen

## Description

This patch keeps a client fullscreen until the user drops it. It applies to
dwm 6.8.

Many games clear `_NET_WM_STATE_FULLSCREEN` themselves when they lose focus,
so switching tags or moving the pointer leaves the window tiled or windowed.
With this patch a clear that arrives while the client is not the selected
client is ignored, and `focus()` restores the fullscreen geometry when the
client is focused again. A clear from the focused client is still honoured, so
the game's own exit or Alt+Enter works as before.

## Configuration

The patch uses the existing `lockfullscreen` option in `config.h`. Set it to
0 to disable the behaviour. No new options are added.

## Testing

Applies and builds against dwm 6.8. Runtime tested under Xvfb. A fullscreen
clear sent while unfocused was ignored, fullscreen geometry returned on
focus, and the same clear while focused was honoured. Setting
`lockfullscreen` to 0 disabled the geometry restore and allowed the
unfocused clear.

## Download

* [dwm-stickyfullscreen-6.8.diff](dwm-stickyfullscreen-6.8.diff)

## Author

* Daniel Guihot - [daniel@guihot.net](mailto:daniel@guihot.net)
