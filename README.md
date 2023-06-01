# Inkscape Flatpak

## Python dependencies

Inkscape need a certain number a Python modules at runtime.

### `requirement.txt`

There is a top level `requirement.txt` to that contain all the modules
that can be installed using the standard mechanism.

The corresponding manifest fragment is `python3-requirements.json`. It
is generated using `flatpak-builder-tools`.
```
./pip/flatpak-pip-generator -r PATH_TO/org.inkscape.Inkscape/requirements.txt
```

### `lxml` module

Unfortunately `lxml` is not in the Platform but is in the Sdk. So it needs
to be force installed.

## Permissions rationale

This application requests the following restricted permissions:

- Network access for the extension mamanger: `--share=network`
- Needs access to all files: `--filesystem=host` (FIXME?)
- X11: we use `--socket=x11` instead of the fallback as it is required
  for extensions that use tkinter. See
  https://github.com/flathub/org.inkscape.Inkscape/issues/101
