---
title: Matplotlib for Python Developers
date: 2022-04-11
image: /assets/images/pyqt-qpushbutton.png
comments: true
---

Matplotlib is an incredibly popular Python data visualization library. It's used in a wide variety of scientific Python applications and can generate publication-quality figures. Its APIs are well documented, it's highly extensible and powerful, but at the same time its default look is easy on the eyes.

## Install matplotlib

Since matplotlib is so popular, there are many different ways to install it. The easiest way is probably to just use pip:

```
pip install matplotlib
```

This will install the latest official release. If you want to install a specific version (e.g., 2.2), you can do so by specifying the version number:

```
pip install matplotlib==2.2
```

If you're using Anaconda, then you can use conda to install matplotlib:

```
conda install -c anaconda matplotlib
```


There are a few other ways to install matplotlib, but these are the two most common. 

## Use matplotlib

Once you have it installed, you can import it into your Python scripts with the following line:

```
import matplotlib.pyplot as plt
```

This line imports the pyplot submodule of matplotlib and gives it the shorter name plt for convenience. Now let's take a look at some basic plotting with pyplot.

First, we need to create a figure. You can do this with the plt.figure() function. Figures are like blank canvases that we can add different kinds of plots to. We can optionally specify the size of the figure in inches (width, height) and its resolution in dots per inch (dpi).

```
plt.figure(figsize=(8,6), dpi=80)
```

After running that code, we haven't actually generated a plot yet. We've just told Python to set up the environment that we'll be using to generate our plot. Think of it like opening a blank Microsoft Word document vs. actually typing something in the document. 

In order to start typing, or in our case plotting, we need to add something called an Axes. The Axes is basically where your data goes and where the scale for your x- and y-axis are located. 

You can add an Axes by calling the plt.axes() function. By default, this will create what's called a Subplot, which is simply a smaller plot located within a grid on top of your figure. 

If you don't specify anything else, your Subplot will take up the entire figure space:

```
plt.axes()
```

