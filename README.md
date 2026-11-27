## HOUGH TRANSFORM
## Name: ELAKYA L
## Reg No: 212225230066
## Aim
To perform Hough Transform on an image using OpenCV and Python for detecting lines in the image.
## Software Required
- Anaconda - Python 3.7
- OpenCV
- NumPy
- Matplotlib
## Algorithm
Step 1
Import all the necessary modules for the program.
Step 2
Load an image using the cv2.imread() function.
Step 3
Convert the image into grayscale using cv2.cvtColor().
Step 4
Apply the Hough Transform technique to detect lines in the image.
Step 5
Draw the detected lines on the image.
Step 6
Display the image with the detected Hough lines using Matplotlib.
## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image using imread() from cv2 module
image = cv2.imread('me.jpeg')

# Step 2: Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Step 3: Display the original image
plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')

# Step 4: Canny Edge Detection
canny_edges = cv2.Canny(gray_image, 50, 150)

plt.subplot(2, 2, 2)
plt.imshow(canny_edges, cmap='gray')
plt.title("Canny Edge Detection")
plt.axis('off')

# Step 5: Hough Line Transform
lines = cv2.HoughLinesP(
    canny_edges,
    1,
    np.pi / 180,
    threshold=50,
    minLineLength=50,
    maxLineGap=10
)

# Step 6: Draw detected Hough lines on the original image
hough_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(
            hough_image,
            (x1, y1),
            (x2, y2),
            (0, 255, 0),
            2
        )

plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(hough_image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')

# Step 7: Display grayscale image
plt.subplot(2, 2, 4)
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')

plt.tight_layout()
plt.show()
```

## Output
**Grayscale image**

<img width="166" height="209" alt="image" src="https://github.com/user-attachments/assets/9d8c3fca-9935-455f-a389-805d0476c39f" />

**Canny edge detector**

<img width="149" height="187" alt="image" src="https://github.com/user-attachments/assets/d268f3c4-39d0-4ede-a6b9-c634793811aa" />

**Hough transform**

<img width="170" height="191" alt="image" src="https://github.com/user-attachments/assets/3baba8ef-9fbd-41f2-9fa7-ae18180c8114" />




## Result
Thus, the Hough Transform experiment was performed using OpenCV and Python, and the image result was displayed successfully.
