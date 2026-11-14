# [Issue]

```
OSError: no library called "cairo-2" was found
no library called "cairo" was found
no library called "libcairo-2" was found
cannot load library 'libcairo.so.2': error 0x7e
cannot load library 'libcairo.2.dylib': error 0x7e
cannot load library 'libcairo-2.dll': error 0x7e
```

# [Solution]

1. GTK3 needs to be installed, restart

2. Add following before import cairosvg (see: https://github.com/Kozea/CairoSVG/issues/388#issuecomment-1548803422):

```
import sys
import os
if sys.platform == 'win32':
    gtkbin = r'C:\gtk3\bin'
    add_dll_dir = getattr(os, 'add_dll_directory', None)
    if callable(add_dll_dir):
        add_dll_dir(gtkbin)
    else:
        os.environ['PATH'] = os.pathsep.join((gtkbin, os.environ['PATH']))
```