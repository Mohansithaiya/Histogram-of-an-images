# Histogram-of-an-images
## Aim
To obtain a histogram for finding the frequency of pixels in an Image with pixel values ranging from 0 to 255. Also write the code using OpenCV to perform histogram equalization.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Read the gray and color image using imread()

### Step2:
Print the image using imshow().

### Step3:
Use calcHist() function to mark the image in graph frequency for gray and color image.

### step4:
Use calcHist() function to mark the image in graph frequency for gray and color image.

### Step5:
The Histogram of gray scale image and color image is shown.


## Program:

### Developed By: Mohan S
### Register Number: 212223240094

## GrayScale Image:
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
### Step 1: Get the input color image
```python
gray_image = cv2.imread('seed.jpg', cv2.IMREAD_GRAYSCALE)
```
### Step 2: Display the grayscale image
```python
plt.title("Grayscale Image")
plt.imshow(gray_image, cmap='gray')
plt.axis('off')
```
### Step 3: Plot the histogram of the grayscale image
```python
plt.title("Histogram of Grayscale Image")
plt.hist(gray_image.ravel(), bins=256, color='black', alpha=0.6)
plt.xlim(0, 255)
plt.tight_layout()
plt.show()
```

### Step 4: Apply histogram equalization using OpenCV
```python
equalized_gray_image = cv2.equalizeHist(gray_image)
```

### Step 5: Display the histogram of the equalized image
```python
plt.title("Histogram of Equalized Grayscale Image")
plt.hist(equalized_gray_image.ravel(), bins=256, color='black', alpha=0.6)
plt.xlim(0, 255)
```
### Step 6: Display the enhanced grayscale image
```python
plt.title("Enhanced Grayscale Image")
plt.imshow(equalized_gray_image, cmap='gray')
plt.axis('off')
```

##  ColorImage:

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 1: Get the input color image
```python
color_image = cv2.imread('Lake.jpg')
```

### Step 2: Display the input color image
```python
plt.title("Input Color Image")
plt.imshow(cv2.cvtColor(color_image, cv2.COLOR_BGR2RGB))
plt.axis('off')
```

### Step 3: Plot the histogram of the input color image (combined channels)
### Calculate the histogram for all channels separately
```python
hist_b = cv2.calcHist([color_image], [0], None, [256], [0, 256])
hist_g = cv2.calcHist([color_image], [1], None, [256], [0, 256])
hist_r = cv2.calcHist([color_image], [2], None, [256], [0, 256])
```

### Plot the histograms
```python
plt.title("Histogram of Input Color Image")
plt.plot(hist_b, color='blue', label='Blue channel')
plt.plot(hist_g, color='green', label='Green channel')
plt.plot(hist_r, color='red', label='Red channel')
plt.show()
```

### Step 4: Apply histogram equalization to each channel of the color image
```python
blue_channel_eq = cv2.equalizeHist(color_image[:, :, 0])
green_channel_eq = cv2.equalizeHist(color_image[:, :, 1])
red_channel_eq = cv2.equalizeHist(color_image[:, :, 2])
```

### Step 5: Merge the equalized channels back into a color image
```python
equalized_color_image = cv2.merge([blue_channel_eq, green_channel_eq, red_channel_eq])
```


## Output:
### Input Grayscale Image and Color Image

![Screenshot 2025-03-29 135737](https://github.com/user-attachments/assets/7f1743d4-3c1f-42e3-9852-6fcdafc2efff)

![Screenshot 2025-03-29 135752](https://github.com/user-attachments/assets/b0f4f8c3-edf1-4a14-ab35-6369d228c496)


### Histogram of Grayscale Image and any channel of Color Image

![Screenshot 2025-03-29 135934](https://github.com/user-attachments/assets/87c35893-5f03-4e43-9696-5f8eba465e28)

![Screenshot 2025-03-29 140028](https://github.com/user-attachments/assets/e2d4c272-4445-4a73-95ce-54a96a116178)


### Histogram Equalization of Grayscale Image.

![Screenshot 2025-03-29 140058](https://github.com/user-attachments/assets/cc195b2f-f1c4-4202-90f3-a6bc49dd740a)



## Result: 
Thus the histogram for finding the frequency of pixels in an image with pixel values ranging from 0 to 255 is obtained. Also,histogram equalization is done for the gray scale image using OpenCV.
