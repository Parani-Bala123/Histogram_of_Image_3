# Experiment 3: Histogram of an Image

## Aim
To calculate and plot the histogram of an image and perform histogram equalization using Python, OpenCV, NumPy, and Matplotlib to improve image contrast.

## Objectives
- To read and display grayscale and color images.
- To plot the histogram of an image.
- To perform histogram equalization on a grayscale image.
- To improve the contrast of a color image using the HSV color space.
- To compare original and equalized images and their histograms.

## Software Requirements
- Python 3.x
- Jupyter Notebook
- OpenCV (`cv2`)
- NumPy
- Matplotlib
- Input image: `My_Image.png`

## Algorithm
1. Start the program.
2. Import OpenCV, NumPy, and Matplotlib libraries.
3. Read the input image in grayscale mode.
4. Display the original grayscale image.
5. Calculate and plot the grayscale image histogram.
6. Apply histogram equalization using `cv2.equalizeHist()`.
7. Plot the equalized histogram and display the equalized image.
8. Read the input image in color mode.
9. Convert the color image from BGR to HSV color space.
10. Apply histogram equalization to the Value (V) channel.
11. Convert the processed image back to BGR color space.
12. Display the equalized color image and its histogram.
13. Compare the original and equalized images and histograms.
14. Stop the program.

## Program

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image in grayscale
img = cv2.imread('My_Image.png', cv2.IMREAD_GRAYSCALE)

# Display the original grayscale image
plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.show()

# Plot the original histogram
plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Image')
plt.show()

# Perform histogram equalization
img_eq = cv2.equalizeHist(img)

# Plot the equalized histogram
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Histogram')
plt.show()

# Display the equalized grayscale image
plt.imshow(img_eq, cmap='gray')
plt.title('Original Image')
plt.show()

# Read the image in color
img = cv2.imread('My_Image.png', cv2.IMREAD_COLOR)

# Convert BGR to HSV
img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

# Equalize the Value channel
img_hsv[:, :, 2] = cv2.equalizeHist(img_hsv[:, :, 2])

# Convert HSV back to BGR
img_eq = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)

# Display the equalized color image
plt.imshow(img_eq[:, :, ::-1])
plt.title('Equalized Image')
plt.show()

# Plot the histogram of the equalized color image
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Histogram Equalized')
plt.show()

# Compare original and equalized color images
plt.figure(figsize=(20, 10))

plt.subplot(221)
plt.imshow(img[:, :, ::-1])
plt.title('Original Color Image')

plt.subplot(222)
plt.imshow(img_eq[:, :, ::-1])
plt.title('Equalized Image')

plt.show()

# Compare the original and equalized histograms
plt.figure(figsize=[15, 4])

plt.subplot(121)
plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Image')

plt.subplot(122)
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Histogram Equalized')

plt.show()
```

## Result
The histogram of the input image was plotted, and histogram equalization was performed on both grayscale and color images. The original and equalized images and their histograms were displayed for comparison. In the color image, equalization was applied to the Value channel in HSV color space to improve contrast while retaining the color information.
