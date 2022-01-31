---
date: 2021-06-08T23:48:05.000Z
layout: post
title: Create Awesome GUI application in Python
subtitle: 'Learn to use create a GUI applications in python using PyQt and Qt Designer.'
description: >-
  Learn to create cross-platform UI aaplication in python using PyQt and Qt Designer.
image: >-
  https://res.cloudinary.com/dog8hn5qv/image/upload/v1641637593/blog/PyQt_e3qapq.png
optimized_image: >-
 https://res.cloudinary.com/dog8hn5qv/image/upload/c_scale,w_380/v1640797676/blog/PyQt_e3qapq.png
category: YouTube
tags:
  - Qt
  - PyQt
  - GUI
  - YouTube
  - Python
  - Qt Designer
author: harshmittal
paginate: true
---


Creating applications can be quite challenging. Each OS has its own libraries to create GUI applications and learning all of them is not a simple task. 
That is why it’s better to write code that can work across platforms. 


## Python to the rescue

Python has tons of different libraries which can help you create amazing applications which will work across platforms. 
Two of the majorly used libraries are PyQt and PySide. In this blog, we will explore PyQt. 


Note: PyQt and PySide are very similar in terms of coding, refer to the documentation of both to read more about them.

[![PyQt YouTube Video](https://img.youtube.com/vi/N8BedE0UIc4/0.jpg)](https://www.youtube.com/watch?v=N8BedE0UIc4)

**Github Link:** [https://github.com/harshmittal2210/youtubeProjects/tree/master/PyQt](https://github.com/harshmittal2210/youtubeProjects/tree/master/PyQt)


## Create Design
Creating design by writing code and then testing can become quite cumbersome, so for this, we will take the help of the Qt designer.

Learn more about Qt: [www.qt.io](www.qt.io)

[https://riverbankcomputing.com/software/pyqt/intro](https://riverbankcomputing.com/software/pyqt/intro)

![Qt Designer](https://res.cloudinary.com/dog8hn5qv/image/upload/v1641637955/blog/Capture_omsiso.jpg)

In the above image, a basic UI is created with push buttons, progress bar, check box, text window, slider bar and some labels.

You can play around and create your own UI

Note: Keep the correct object name in Object Inspector (Left side up)

## Method 1 - Import UI in python
```python
from PyQt5 import QtWidgets, uic
import sys


class NetworkUi(QtWidgets.QMainWindow):
	def __init__(self):
		super(NetworkUi,self).__init__() #Call the inherited classes __init__ method
		uic.loadUi('test.ui', self)
		self.show()

app = QtWidgets.QApplication(sys.argv)
window = NetworkUi()
app.exec_()
```

With the help of the above code, you can directly call the UI file created and use it.

## Method 2 - Convert UI into python code

While installing PyQt, an application is also installed called pyuic which converts UI files into python code. 

You can also look for this application in the GitHub Link.

```bash
$ pyuic5.exe -x "test.ui" -o "test.py"
```

```python
from PyQt5 import QtCore, QtGui, QtWidgets

class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(675, 304)
        self.centralwidget = QtWidgets.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")
        self.okButton = QtWidgets.QPushButton(self.centralwidget)
        self.okButton.setGeometry(QtCore.QRect(40, 180, 71, 28))
        self.okButton.setObjectName("okButton")
        self.closeButton = QtWidgets.QPushButton(self.centralwidget)
        self.closeButton.setGeometry(QtCore.QRect(130, 180, 93, 28))
        self.closeButton.setObjectName("closeButton")
        self.label = QtWidgets.QLabel(self.centralwidget)
        self.label.setGeometry(QtCore.QRect(250, 0, 171, 51))
        font = QtGui.QFont()
        font.setPointSize(17)
        self.label.setFont(font)
        self.label.setObjectName("label")
        self.textEdit = QtWidgets.QTextEdit(self.centralwidget)
        self.textEdit.setGeometry(QtCore.QRect(40, 50, 191, 121))
        self.textEdit.setObjectName("textEdit")
        self.testSlider = QtWidgets.QSlider(self.centralwidget)
        self.testSlider.setGeometry(QtCore.QRect(450, 160, 160, 16))
        self.testSlider.setOrientation(QtCore.Qt.Horizontal)
        self.testSlider.setObjectName("testSlider")
        self.option1CheckBox = QtWidgets.QCheckBox(self.centralwidget)
        self.option1CheckBox.setGeometry(QtCore.QRect(260, 60, 71, 20))
        self.option1CheckBox.setObjectName("option1CheckBox")
        self.progressBar = QtWidgets.QProgressBar(self.centralwidget)
        self.progressBar.setGeometry(QtCore.QRect(40, 230, 611, 23))
        self.progressBar.setProperty("value", 24)
        self.progressBar.setObjectName("progressBar")
        self.option2CheckBox = QtWidgets.QCheckBox(self.centralwidget)
        self.option2CheckBox.setGeometry(QtCore.QRect(260, 90, 75, 20))
        self.option2CheckBox.setObjectName("option2CheckBox")
        MainWindow.setCentralWidget(self.centralwidget)
        self.menubar = QtWidgets.QMenuBar(MainWindow)
        self.menubar.setGeometry(QtCore.QRect(0, 0, 675, 26))
        self.menubar.setObjectName("menubar")
        MainWindow.setMenuBar(self.menubar)
        self.statusbar = QtWidgets.QStatusBar(MainWindow)
        self.statusbar.setObjectName("statusbar")
        MainWindow.setStatusBar(self.statusbar)

        self.retranslateUi(MainWindow)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    def retranslateUi(self, MainWindow):
        _translate = QtCore.QCoreApplication.translate
        MainWindow.setWindowTitle(_translate("MainWindow", "MainWindow"))
        self.okButton.setText(_translate("MainWindow", "OK"))
        self.closeButton.setText(_translate("MainWindow", "Close"))
        self.label.setText(_translate("MainWindow", "Test Window"))
        self.option1CheckBox.setText(_translate("MainWindow", "Option 1"))
        self.option2CheckBox.setText(_translate("MainWindow", "Option 2"))


if __name__ == "__main__":
    import sys
    app = QtWidgets.QApplication(sys.argv)
    MainWindow = QtWidgets.QMainWindow()
    ui = Ui_MainWindow()
    ui.setupUi(MainWindow)
    MainWindow.show()
    sys.exit(app.exec_())
```

As you can see in the above code all the object names are the same as given in the Qt Designer.

Read the documentation carefully for better understanding. A much more detailed explanation will also e given in future blogs.

LinkedIn : [www.linkedin.com/in/harshmittal2210](www.linkedin.com/in/harshmittal2210)

Github   : [www.github.com/harshmittal2210](www.github.com/harshmittal2210)

