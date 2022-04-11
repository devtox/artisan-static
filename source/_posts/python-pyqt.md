---
title: Python PyQt
date: 2022-04-11
image: /images/pyqt.jpeg
comments: false
---
### What is PyQt5?

PyQt5 is a set of Python bindings for The Qt5, a cross-platform application and UI framework. It allows Python developers to easily deploy their applications on Windows, Apple macOS X, Linux desktops.

Assuming you have a basic understanding of Python, let's dive right in to PyQt5! We'll start by looking at the most fundamental aspects of PyQt5. Then, we'll move on to more advanced topics like signals and slots. By the end of this tutorial, you should be able to write your own PyQt5 applications with ease!

### Why PyQt?

PyQt was created as a toolkit for writing Python GUI applications rapidly. Its main benefits over other scripting languages such as Perl or Tcl/Tk include:

It has a complete set of widgets that allow you to create any kind of application interface possible, not just the ones where everything is inside one window: PyQt also supports multi-window applications with multiple independent windows that can be moved arbitrarily across the desktop and that can support transparency.

It has a robust and mature set of tools for creating graphical user interfaces, including Qt Designer which provides a visual drag-and-drop interface for creating PyQt application user interfaces.

PyQt is a popular toolkit for creating Python GUI applications. Its main benefits over other scripting languages are its complete set of widgets, robust and mature tools, and support for all major operating systems: Windows, Mac OS X and Linux/Unix. You can deploy your applications on any of these platforms without having to rewrite your code.

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

```
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

The result of the code is shown below. Clicking on any of the buttons calls the slot functions and output is shown in the terminal.

![Buttons with PyQt](/images/pyqt-qpushbutton.png)

## Layout management

The QMainWindow class is derived from QMainWindow (class), which inherits QWidget (class). The QMainWindow class can be used to create the main application window for an application.

Qt provides different layout classes that enable you to create specific layouts. For example, you can use a grid layout to arrange widgets in a table format, or you can use a form layout to arrange widgets vertically or horizontally.

### Horizontal layout

The example below creates a horizontal layout in which several *QPushButton* widgets are places. Any widget can be added to the horizontal layout (hbox).

```
#coding = 'utf-8'

import sys
from PyQt5.QtWidgets import (QWidget, QPushButton, QApplication, QHBoxLayout, QVBoxLayout)

class Example(QWidget):
    def __init__(self):
        super().__init__()
        self.Init_UI()
    def Init_UI(self):
        self.setGeometry(300,300,400,100)
        self.setWindowTitle('Horizontal Layout')

        bt1 = QPushButton('Button 1', self)
        bt2 = QPushButton('Button 2', self)
        bt3 = QPushButton('Button 3', self)

        hbox = QHBoxLayout()
        hbox.addStretch(1)
        hbox.addWidget(bt1)
        hbox.addWidget(bt2)
        hbox.addWidget(bt3)

        vbox = QVBoxLayout()
        vbox.addStretch(1)
        vbox.addLayout(hbox)

        self.setLayout(vbox)

        self.show()

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    app.exit(app.exec_())
```

![horizontal layout pyqt](/images/qhboxlayout.png)

### Form layout

QFormLayout is a subclass of QWidget and can be used as a layout scheme. The widget is designed to display a form. An example is shown below

```
#coding = 'utf-8'
import sys
from PyQt5.QtWidgets import (QWidget, QPushButton, QApplication, QFormLayout, QLabel, QLineEdit, QTextEdit)

class Example(QWidget):
    def __init__(self):
        super().__init__()
        self.Init_UI()

    def Init_UI(self):
        self.setGeometry(320,200,300,200)
        self.setWindowTitle('Form Layout')
        formlayout = QFormLayout()
        nameLabel = QLabel("Name")
        nameLineEdit = QLineEdit("")
        descriptionLabel = QLabel("Description")
        descriptionLineEdit = QTextEdit("")
        formlayout.addRow(nameLabel,nameLineEdit)
        formlayout.addRow(descriptionLabel,descriptionLineEdit)
        self.setLayout(formlayout)
        self.show()

if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Example()
    app.exit(app.exec_())
```

![form layout python](/images/qformlayout.png)

\
I've been experimenting with PyQt lately and I'm really impressed with its capabilities. It's easy to use and extremely versatile. I highly recommend giving it a try if you're looking for a way to create beautiful Python GUIs.

There are widgets like QPushButton, QRadioButton, QPushButton, QRadioButton, QSpinBox, etc. Each widget has a purpose and  can be customized according to your needs. Besides these, there are many more widgets and there's much more to PyQt.