# 1) First steps in ImageJ/Fiji

## 1.1) Getting / starting Fiji

- Please go to the webpage https://fiji.sc, download and install Fiji (a distribution of ImageJ) for your operating system, and run it.

- If this does not work, you can alternatively try to use the online version from ImJoy: https://ij.imjoy.io/

- In the update dialog that appears after starting Fiji, select "Remind me later" for now.

## 1.2) First steps

The startup window has three parts: the menu bar, the tool bar and the status bar.

You can open files from the “File“ menu (“Open..“ oder “Import“). In the “Import“-submenu, you can see all the different file formats supported by ImageJ. Further file formats (e.g. microscope-specific) are supported through the “BioFormats“-Library.

ImageJ comes with a number of test images. These are accessible through the menu “File -> Open Samples“. Open the test image “Fly Brain“. Enlarge the display to 200% (press “+“ twice, or use the magnifying glass).

## 1.3) Metadata

At the top of the image window, important information about the volume is shown. How large is the test image (in pixels) in X, Y and Z direction? How large is a pixel?

There is more information about the image (*meta data*) stored in the TIFF file. You can display it by “Image -> Show Info“, or by pressing `i`.

> Where does the image come from? What type of organism is it? How many bits are stored per pixel? How many color channels does the image have?

To visualize the physical size, we add a “scale bar“ to the image: “Analyze -> Tools -> Scalebar“. Try the different options. The last step can be undone by “Edit -> Undo“.

Sometimes, Metadata are not stored alongside the images and have to be entered manually. This can be done for example by “Image -> Properties...“ and through “Analyze -> Set Scale...“.

## 1.4) 3D Visualization

The 3D image volume consists of a “stack“ of individual images. Using the slider below the image window, you can change the z position. However, this gives only a limited impression of the three-dimensionality of the data.

There are different possibilities to better visualize 3D image volumes:

- Orthogonal Views (Image -> Stacks -> Orthogonal Views, oder `Ctrl+Shift+h`). By clicking with the mouse, you can change the position of the cross-hair, corresponding to the layer that is shown.
- 3D Projection (Image -> Stacks -> 3D Project). Try different options, change e.g. the axis of rotation. By hitting “OK“, a new image opens up, the original one is kept.
- 3D Viewer (Plugins -> 3D Viewer). The position can be changed using the mouse.

> Try all three options. What are their advantages and disadvantages?

## 1.5) Filtering and noise reduction

Now we will learn about different possibilities for noise reduction.

Close all open windows (“File=>Close all“ or Ctrl+Shift+w). Open the example “Blobs“ and zoom to 150%. Duplicate the image (“Ctrl+Shift+d“). This is always a good idea before complex processing steps. Add white noise to the image (“Process=>Noise=>Add Noise“).

Now, try different filters to reduce the noise and to reconstruct the original image (“Process=>Filters=>Mean/Median/Gaussian Blur…“). 
> Which filter gives the best result?

Duplicate the original image again, and this time add “Salt and Pepper“ noise. Compare the result of mean and median filters, each with radius 1.

>Which filter works better here, and why?

Linear filters can be divided into high- and lowpass filters depending on their frequency response. An image can be transformed into frequency space using “Process => FFT => FFT“.

> How do the images differ in frequency space before and after adding noise, and after applying the respective filter?

Apply different bandpass filters to the image (“Process => FFT => Bandpass“) and observe the result.

