# Debug MATE

This page contains some tips to help to debug MATE issues

## caja (mate-file-manager)

See [Caja debug](applications-caja.md#Debug).

```bash
gdb caja `pidof caja`
```

## mate-screensaver

```bash
killall mate-screensaver
mate-screensaver --debug
```

## mate-settings-daemon

```bash
killall mate-settings-daemon
mate-settings-daemon --no-daemon --debug
```

## marco (window-manager)

```bash
MARCO_DEBUG=1 marco --replace
```
