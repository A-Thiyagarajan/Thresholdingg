# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

### Step1:
Load the input image using cv2.imread() and convert it to a grayscale image using cv2.cvtColor() with the color conversion code cv2.COLOR_BGR2GRAY.

### Step2:
Use a fixed threshold value (e.g., 127) for global thresholding with cv2.threshold(). Pixels with intensity above this value are set to maximum intensity (255), and the rest are set to minimum intensity (0).

### Step3:
Use adaptive thresholding, which calculates the threshold for smaller regions of the image. The threshold is calculated dynamically using cv2.adaptiveThreshold() with the ADAPTIVE_THRESH_GAUSSIAN_C method.

### Step4:
Otsu's method automatically finds an optimal threshold value by minimizing the within-class variance. Apply it using cv2.threshold() with the flag cv2.THRESH_OTSU.

### Step5:
Use plt.imshow() to visualize the grayscale image and the segmented images from global, adaptive, and Otsu's thresholding techniques.

## Program

```python
# Load the necessary packages

import cv2
import numpy as np
import matplotlib.pyplot as plt


# Read the Image and convert to grayscale

image = cv2.imread('cat.jpg')

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.xticks([]), plt.yticks([])
plt.show()



# Use Global thresholding to segment the image

ret_global, th_global = cv2.threshold(gray_image, 127, 255, cv2.THRESH_BINARY)

# Display the global thresholding result
plt.imshow(th_global, cmap='gray')
plt.title('Global Thresholding (v=127)')
plt.xticks([]), plt.yticks([])
plt.show()



# Use Adaptive thresholding to segment the image

th_adaptive = cv2.adaptiveThreshold(gray_image, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
                                    cv2.THRESH_BINARY, 11, 2)

# Display the adaptive thresholding result

plt.imshow(th_adaptive, cmap='gray')
plt.title('Adaptive Gaussian Thresholding')
plt.xticks([]), plt.yticks([])
plt.show()



# Use Otsu's method to segment the image 

ret_otsu, th_otsu = cv2.threshold(gray_image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

# Display the results

plt.imshow(th_otsu, cmap='gray')
plt.title("Otsu's Thresholding")
plt.xticks([]), plt.yticks([])
plt.show()

```
## Output

### Original Image
![image](https://github.com/user-attachments/assets/f9ccdb51-a8bc-4ad2-a0a9-17d2ce5037d5)

### Global Thresholding
![image](https://github.com/user-attachments/assets/aee04610-0902-41ca-8740-37785d2ae293)


### Adaptive Thresholding
![image](https://github.com/user-attachments/assets/13cb77e6-0c69-440b-aaaa-adce5fa4e838)


### Optimum Global Thesholding using Otsu's Method
![image](https://github.com/user-attachments/assets/289cb1e4-96a9-4238-a622-7f73bc054b8e)



## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
