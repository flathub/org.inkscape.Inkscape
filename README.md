# Inkscape Flatpak

## Cairo

Cairo 1.18 is built in the flatpak for gradiant support in Inkscape 1.3.1.
It should be removed when the newer runtime has it.

## Python dependencies

Inkscape need a certain number a Python modules at runtime.

### `requirements.txt`

There is a top level `requirements.txt` to that contain all the modules
that can be installed using the standard mechanism.

The corresponding manifest fragment is `python3-requirements.json`. It
is generated using `flatpak-builder-tools`.
```
./pip/flatpak-pip-generator -r PATH_TO/org.inkscape.Inkscape/requirements.txt --runtime org.gnome.Sdk//44 --ignore-installed lxml
```

This will also take care of the `lxml` that needs to be force installed

## Permissions rationale

This application requests the following restricted permissions:

- Network access for the extension mamanger: `--share=network`
- Needs access to all files: `--filesystem=host` (FIXME?)
- X11: we use `--socket=x11` instead of the fallback as it is required
  for extensions that use tkinter. See
  https://github.com/flathub/org.inkscape.Inkscape/issues/101
