---
title: Python PyQt
date: 2022-04-11
image: https://duckduckgo.com/i/20f514c0.png
comments: true
---
### What is PyQt5?

PyQt5 is a set of Python bindings for The Qt5, a cross-platform application and UI framework. It allows Python developers to easily deploy their applications on Windows, Apple macOS X, Linux desktops.

Assuming you have a basic understanding of Python, let's dive right in to PyQt5! We'll start by looking at the most fundamental aspects of PyQt5. Then, we'll move on to more advanced topics like signals and slots. By the end of this tutorial, you should be able to write your own PyQt5 applications with ease!

### Hello world

QLabel is used to display text and we're going to use it to create "Hello World". QLabel can take plain text, as well as HTML or even rich text (see setTextFormat()). You can also set an alignment for the contents using setAlignment(). The following code creates the hello world app.

```
import sys
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *


def window():
   app = QApplication(sys.argv)
   window = QWidget()
   label = QLabel(window)
   label.setText("Hello World!")
   window.setGeometry(200,200,300,200)
   label.move(100,80)
   window.setWindowTitle("PyQt5")
   window.show()
   sys.exit(app.exec_())

# program starts here
if __name__ == '__main__':
   window()
```

### Signals and slots

Now let's move on to more advanced PyQt5 topics like signals and slots!In PyQt5, signals and slots are used to communicate between widgets. If you have a custom widget that emits a signal, you can connect that signal to a slot in your application. Likewise, if you have a custom widget with a slot, you can connect it to any signal in your application.

Signals and slots are loosely coupled: A class can emit a signal that no other class is interested in, and no error will occur. Or, conversely,a class can receive a signal from another class that has no corresponding slot. This flexibility makes signals and slots powerful; however, it also comes with some disadvantages.

```python
import sys
from PyQt5.QtCore import *
from PyQt5.QtGui import *
from PyQt5.QtWidgets import *

def window():
   app = QApplication(sys.argv)
   win = QDialog()

   # first button widget
   button1 = QPushButton(win)
   button1.setText("Button1")
   button1.move(50,20)

   # connect signal to slot
   button1.clicked.connect(button1_clicked)
   
   # second button widget
   button2 = QPushButton(win)
   button2.setText("Button2")
   button2.move(50,50)

   # connect signal to slot
   button2.clicked.connect(button2_clicked)
   
   # create window
   win.setGeometry(100,100,200,100)
   win.setWindowTitle("Python PyQt5")
   win.show()
   sys.exit(app.exec_())

# slots
def button1_clicked():
   print ("Button 1 clicked")

def button2_clicked():
   print ("Button 2 clicked")

if __name__ == '__main__':
   window()
```

