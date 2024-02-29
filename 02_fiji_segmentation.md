# 2) Segmentation and Measurement

## 2.1) Thresholding

We will now segment and analyze the “Blobs“ image. Open it again (close all images first) and scale to 150%. Apply a Gaussian Blur (sigma = 2), then call the Threshold dialog (“Image=>Adjust=>Threshold“ or Ctrl+Shift+t) and try the different options.

The particles should be completely red, but without including too much background. Finally, select the “Otsu“-Algorithm and apply it (“Apply“).

## 2.2) Segmentation

Some of the objects are connected and need to be separated before measuring object properties. For this, we use the watershed transform.

For illustration, first activate the debug mode (“Edit=>Options=>Misc…“) and then apply the Watershed transform (“Process=>Binary=>Watershed“). An additional stack appears that contains the different steps of the process.

## 2.3) Measurement

We now determine different properties of the segmented objects. Select the “Analyze Particles“ tool in ImageJ  (“Analyze=>Analyze Particles“). Try different particle sizes, circularities and “Show“-options. The measurements for the individual particles are shown in the “Results“-window, the summary statistics in the “Summary“.

> How many objects have been detected? What is the average area?

The properties to be determined can be defined through the “Process=>Set Measurements“ dialog. Individual objects can be selected in the ROI manager (ROI = “Region of Interest“).

The intensity measurements in the binary image (after applying the threshold) are not meaningful any more (all = 255). So now, we want to measure the objects in the original image. Open the “Blob“ sample again and measure the properties of individual blobs using the ROI manager and the option “Analyze=>Measure“ (Ctrl+m).

You can also define ROIs yourself, e.g. using the first five buttons in the toolbar (from left). Create a line ROI in the “Blobs“ image and display the intensity profile along this line (“Analyze=>Plot Profile“ or Ctrl+k). Activate the “Live“ button and move the ends of the line, e.g. across several blobs. Observe the live plot.

## 2.4) Macro recorder

One of the most important tools for creating image analysis workflows in ImageJ/Fiji is the macro recorder. Most functions in ImageJ are controllable from macros. It is a good idea to always have the macro recorder running in the background to document what you have done.

Close all open images and call the macro recorder (“Plugins=>Macros=>Record…“). Now perform all steps from the part on segmentation above again, and observe how the corresponding macro commands are recorded:

1)	Open “Blobs“ example
2)	Apply Gaussian Blur with sigma = 2.0
3)	Apply threshold
4)	Apply watershed
5)	Analyze Particles

Now click on “Create“ to open the recorded commands as new macro in the editor. The result should look similar to this:
 
```
run("Blobs (25K)");
run("Gaussian Blur...", "sigma=2");
setAutoThreshold("Default");
//run("Threshold...");
//setThreshold(155, 255);
setOption("BlackBackground", false);
run("Convert to Mask");
run("Watershed");
run("Analyze Particles...", "  show=Overlay display exclude clear include summarize record add");
```

Single lines in the code can be commented out by putting `//` in front – here, `setThreshold` is commented out. Activate it by removing the `//`.

Now, run the macro and change individual parameters in the code, e.g. the radius of the Gauss filter (`sigma=2`) or the thresholds (`setThreshold(value1, value2)`).

>How does the final result (“Count“ and “Total Area“ in the summary window) change? 
