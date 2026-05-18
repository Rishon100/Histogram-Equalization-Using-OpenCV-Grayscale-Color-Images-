# Histogram Equalization Using OpenCV (Grayscale & Color Images)

## Aim
To write a Python program using :contentReference[oaicite:0]{index=0} to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image
- Plot histogram of the grayscale image
- Apply histogram equalization on grayscale image
- Read and display a color image
- Plot histogram of B, G, R channels
- Convert image to HSV color space
- Apply histogram equalization on the Value (V) channel
- Convert the enhanced image back to BGR format
- Display original and enhanced images with histograms

---

# Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- :contentReference[oaicite:1]{index=1} (`cv2`)
- NumPy
- Matplotlib

---

# Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 2:
Read the image `parrot.jpg` in grayscale format.
```
img_gray = cv2.imread("parrot.jpg",0)
```
### Step 3:
Display the grayscale image and plot its histogram.
```
plt.imshow(img_gray,cmap="gray")
plt.title("gray scale image")
plt.axis("off")
plt.show()

plt.hist(img_gray.ravel(), 256, range = [0,256])
plt.title("Orginal image")
plt.show()
```
### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.
```
img_eq = cv2.equalizeHist(img_gray)
```
### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.
```
plt.figure(figsize=(8,10))

plt.subplot(2,2,1)
plt.imshow(img_gray, cmap="gray")
plt.title("Original image")
plt.axis("off")

plt.subplot(2,2,2)
plt.hist(img_gray.ravel(), 256, [0,256])
plt.title("Histogram of Original Image")

plt.subplot(2,2,3)
plt.imshow(img_eq, cmap='gray')
plt.title("Enhanced (Equalized) Image")
plt.axis("off")

plt.subplot(2,2,4)
plt.hist(img_eq.ravel(), 256, [0,256])
plt.title("Histogram of Enhanced Image")

plt.tight_layout()
plt.show()
```
### Step 6:
Read the same image in color format.
```
img = cv2.imread('parrot.jpg', cv2.IMREAD_COLOR)
```
### Step 7:
Split the image into B, G, R channels and plot their histograms.
```
b, g, r = cv2.split(img)

# Plot histograms
plt.figure(figsize=(8,5))

plt.hist(b.ravel(), 256, [0,256], color='blue', alpha=0.5, label='Blue')
plt.hist(g.ravel(), 256, [0,256], color='green', alpha=0.5, label='Green')
plt.hist(r.ravel(), 256, [0,256], color='red', alpha=0.5, label='Red')

plt.title("Histogram of BGR Channels")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")
plt.legend()

plt.show()
```
### Step 8:
Convert the image from BGR to HSV color space.
```
img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```

### Step 9:
Apply histogram equalization on the V (Value) channel.

```
h, s, v = cv2.split(img_hsv)
v_eq = cv2.equalizeHist(v)
```
### Step 10:
Merge the channels and convert the image back to BGR format.
```
hsv_eq = cv2.merge((h, s,  v_eq))
enh_img = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)
```
### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.
```
plt.figure(figsize=(10,8))

# Original image
plt.subplot(2,2,1)
plt.imshow(img[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

#origianl hist
plt.subplot(2,2,2)
plt.hist(img.ravel(),bins=256,range=[0,256])
plt.title("Original Histogram")

#Enhanced iamge
plt.subplot(2,2,3)
plt.imshow(enh_img[:,:,::-1])
plt.title("Enhanced Image")
plt.axis("off")

#Enhanced hist
plt.subplot(2,2,4)
plt.hist(enh_img.ravel(),bins=256,range=[0,256])
plt.title("Enhanced Histogam")
plt.show()
```
---

# Developed By

**Name:** V RISHON ANAND

**Register No:** 212224240135

---

# Output

<img width="1005" height="588" alt="image" src="https://github.com/user-attachments/assets/032a9b17-6eef-4cbd-a0ee-e12e4a9216f1" />
<img width="961" height="387" alt="image" src="https://github.com/user-attachments/assets/e962e8cb-9750-439b-9c8b-88e74e8e7f7e" />


## Grayscale Histogram Equalization

- Original grayscale image is displayed
- Histogram of original grayscale image is plotted
- Enhanced image after histogram equalization is displayed
- Histogram of enhanced grayscale image shows improved contrast

## Color Image Histogram Equalization

- Original color image is displayed
- Histogram of B, G, R channels is plotted
- Enhanced image after HSV-based equalization is displayed
- Histogram of enhanced image shows better intensity distribution

---

# Result

Thus, histogram equalization is successfully performed on both grayscale and color images using :contentReference[oaicite:2]{index=2}. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
