# qtimshow
Little hack to have an imshow function like OpenCV

OpenCV and Qt are graphically incompatible. Both require
ownership and also hijack program's main thread.

This module brings the Qt version of cv2.imshow.
To maximize compatibility with both cases, remove prefix:
```
from cv2 import imshow
from qtimshow import imshow
```

## Usage
This module requires two parts to work:
* Attach to main thread (enable it)
```
import qtimshow

if __name__ == '__main__':
    ...
    app = QtGui.QApplication(sys.argv)
    qtimshow.enable()
    ....
    app.exec_()

```
* Import imshow function (use it)
```
from qtimshow import imshow
```

## Image types
Image type handling is too limited. Supported:
* RGB
* Grayscale

Any further type can be *manually* supported by pass the 
Qt's counterpart type:
```
from PyQt4.QtGui import QImage
imshow('a title', img_rgb, QImage.Format_RGB888)
```


## Install
This module can be installed, added to pythonpath or just copied.


## License
Program is under GPLv3 or later, copyrigth (C) 2015 Victor Arribas.
You can get a copy of license from http://www.gnu.org/licenses/.
