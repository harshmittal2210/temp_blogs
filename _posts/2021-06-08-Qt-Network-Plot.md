---
date: 2021-06-08T23:48:05.000Z
layout: post
title: Qt Network Plot using QCustomPlot & Python
subtitle: 'Plot realtime data in Qt'
description: >-
  Learn to create cross-platform UI for plotting real-time data comming over TCP.
image: >-
  https://res.cloudinary.com/dog8hn5qv/image/upload/v1640797676/blog/PLOT_REAL_TIME_DATA_IN_QT_n5t9g2.png
optimized_image: >-
 https://res.cloudinary.com/dog8hn5qv/image/upload/c_scale,w_380/v1640797676/blog/PLOT_REAL_TIME_DATA_IN_QT_n5t9g2.png
category: YouTube
tags:
  - Qt
  - QCustomPlot
  - Plotting
  - GUI
  - YouTube
  - Python
  - TCP
author: harshmittal
paginate: true
---

Qt is a really powerful cross-platform GUI application. There are lot of internal features that you can use to create awesome applications. You can also use thousands of open-source third party libraries to improve your application drastically.

![Network Plot Image](https://res.cloudinary.com/dog8hn5qv/image/upload/v1640797676/blog/PLOT_REAL_TIME_DATA_IN_QT_n5t9g2.png)

In this project we will be using QCustomPlot to plot our data in Qt. **QCustomPlot** is a Qt C++ widget for plotting and data visualization.

Link: https://www.qcustomplot.com/

In this project we will create a simple GUI which will plot our real time data coming on TCP. The graph will be interactive and can be descaled easily. Even the plot style can be changed according to our need.

GitHub link: https://github.com/harshmittal2210/Qt-Network-Plot


## How to use QCustomPlot in Qt?

It is fairly very easy to use QCustomPlot in Qt. In the following video I have shown how to set up the project and organize your source and header files and then plot basic data.

[![QCustomPlot YouTube Video](https://img.youtube.com/vi/VCx8i2W52TY/0.jpg)](https://www.youtube.com/watch?v=VCx8i2W52TY)

You can also refer the official documentation of QCustomPlot from here to get basic idea.

## Add Push Buttons

In the above section we have seen how to add plot in Qt. Now we will add push buttons to plot, clear data and close the program.

[![Push Button YouTube Video](https://img.youtube.com/vi/-1Pb0caKrmE/0.jpg)](https://www.youtube.com/watch?v=-1Pb0caKrmE)

## Change Plotting Style

QCustomPlot also gives us different plotting features. In the following video I have shown how to change the plotting style of data coming in real time.

[![Plotting Style YouTube Video](https://img.youtube.com/vi/drLbFy_qxN0/0.jpg)](https://www.youtube.com/watch?v=drLbFy_qxN0)



## Create Server accepting multiple connections

Creating server can be challenging in different OS, but Qt makes it really easy. In the following video I have used multi-threading to create server which enables multiple clients to send data at same time.

[![Server YouTube Video](https://img.youtube.com/vi/-5vZgeF2_G0/0.jpg)](https://www.youtube.com/watch?v=-5vZgeF2_G0)

## Create Python Client and send JSON Data

Creating client is very straightforward. In this video I have shown how you can send continuously data in JSON format to a server.


[![Python Client YouTube Video](https://img.youtube.com/vi/ovTJdx24Osw/0.jpg)](https://www.youtube.com/watch?v=ovTJdx24Osw)

## Use SIGNAL & SLOTS to send data between threads

In this section I have shown how you can send data from a thread to main window for plotting using multiple Signal and Slots.

[![Signal and Slots Youtube video](https://img.youtube.com/vi/rgLIAmbTUA4/0.jpg)](https://www.youtube.com/watch?v=rgLIAmbTUA4)


### Method 1

We will create a server thread to run server independently to accept connection request. This enables GUI to run separately so that it does not hangs.

[![Method 1 YouTube Video](https://img.youtube.com/vi/rgLIAmbTUA4/0.jpg)](https://www.youtube.com/watch?v=rgLIAmbTUA4)

### Method 2

We will run server on main thread itself. This allows us to decrease number of thread and signals emitted to send data to main window.

[![Method 2 YouTube Video](https://img.youtube.com/vi/E33LqSKsmYA/0.jpg)](https://www.youtube.com/watch?v=E33LqSKsmYA)


### Create EXE

This video shows a simple way of converting your code to a executable.

[![Create EXE YouTube Video](https://img.youtube.com/vi/Y0MSOQGv5N4/0.jpg)](https://www.youtube.com/watch?v=Y0MSOQGv5N4)

