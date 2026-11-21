# Detect the Line using Hough Diagram
# Name: Sowmiya R
# Reg No: 212225040420

## AIM

To perform basic lane edge detection using Python and OpenCV by reading an input image, converting it into grayscale, applying Canny edge detection, and displaying the detected edges.

## LEARNING OBJECTIVES

- Understand basic image processing techniques.
- Learn grayscale image conversion.
- Understand Canny edge detection.
- Identify edges and boundaries in road images.

## SOFTWARE REQUIRED

- Python
- OpenCV
- NumPy
- Matplotlib
- Jupyter Notebook
- Anaconda (optional)

## INSTALLATION

Install the required libraries using the following command:

```bash
pip install opencv-contrib-python-headless numpy matplotlib
```

## ALGORITHM

### Step 1: Import Libraries
- Import OpenCV for image processing.
- Import NumPy for numerical operations.
- Import Matplotlib for displaying images.

### Step 2: Read the Input Image
- Load the road image using `cv2.imread()`.
- Display the original input image.

### Step 3: Convert to Grayscale
- Convert the input image into grayscale using `cv2.cvtColor()`.
- Display the grayscale image.

### Step 4: Apply Canny Edge Detection
- Apply the Canny edge detection algorithm using `cv2.Canny()`.
- Set the lower threshold to 50 and the upper threshold to 150.
- Detect edges and boundaries in the image.

### Step 5: Display the Results
- Display the input image.
- Display the grayscale image.
- Display the Canny edge detected image.
- Display the final result.

## PROGRAM

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load the image using imread() from cv2 module
image = cv2.imread('Mine.jpeg')  # Replace 'image.jpg' with your image path

# Step 3: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Input image and grayscale image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert image to RGB for displaying
plt.title("Input Image")
plt.axis('off')

plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')

# Step 4: Using Canny operator from cv2, detect the edges of the image
edges = cv2.Canny(gray_image, 50, 150)  # Canny edge detection with threshold values 50 and 150

# Canny Edge Detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')

# Step 5: Using the HoughLinesP(), detect line coordinates for every point in the image
# The parameters of HoughLinesP are: image, resolution, threshold, minLineLength, maxLineGap
lines = cv2.HoughLinesP(edges, 1, np.pi / 180, 200, minLineLength=100, maxLineGap=20)

# Step 6: Using a for loop, draw the lines on the original image using the detected coordinates
# The lines variable contains the endpoints of the detected lines
for line in lines:
    x1, y1, x2, y2 = line  # Unpacking the line coordinates
    cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)  # Draw green lines with thickness of 2

# Display the result of Hough Transform (Image with lines)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Image with lines drawn
plt.title("Result of Hough Transform")
plt.axis('off')

```

## OUTPUT

The following outputs are obtained:

## 1. Original input image 
<img width="527" height="333" alt="image" src="https://github.com/user-attachments/assets/04308196-05a2-401a-8170-e205ae101e48" />


## 2. Grayscale image 
<img width="490" height="322" alt="image" src="https://github.com/user-attachments/assets/f06d67b6-7a3b-4595-b875-97a342424eff" />

## 3. Canny edge detected image showing the edges and boundaries
   <img width="520" height="331" alt="image" src="https://github.com/user-attachments/assets/ab4cba2c-7282-4f62-bfff-55a3445a4960" />

## 5. Final lane detection result displayed
<img width="470" height="338" alt="image" src="https://github.com/user-attachments/assets/e1a8f5b6-0332-4549-81f7-612ff8c98147" />


## RESULT
Thus, basic lane edge detection was performed successfully using Python and OpenCV. The input image was converted into grayscale, and the Canny edge detection algorithm was applied to identify edges and boundaries in the image.
