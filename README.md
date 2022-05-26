# Python dependencies

Inkscape need a certain number a Python modules at runtime.

## `requirement.txt`

There is a top level `requirement.txt` to that contain all the modules
that can be installed using the standard mechanism.

The corresponding manifest fragment is `python3-requirements.json`. It
is generated using `flatpak-builder-tools`.
```
./pip/flatpak-pip-generator -r PATH_TO/org.inkscape.Inkscape/requirements.txt
```

## `lxml` module

Unfortunately `lxml` is not in the Platform but is in the Sdk. So it needs
to be force installed.
