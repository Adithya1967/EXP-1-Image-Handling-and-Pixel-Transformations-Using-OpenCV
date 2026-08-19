# EXP-1-Image-Handling-and-Pixel-Transformations-Using-OpenCV
## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels.

## Program Developed By:
- **Name:**Vignesh.P
- **Register Number:** 212224230302

### Ex. No. 01

#### 1. Read the image ('spidey.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('spidey.jpg', cv2.IMREAD_GRAYSCALE)
```

#### 2. Print the image width, height & Channel.
```python
height, width = img.shape

print("Width :", width)
print("Height:", height)
print("Channel: 1")
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite('spidey.jpg', img)
print("Image saved successfully.")
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img_gray = cv2.imread('spidey.jpg', cv2.IMREAD_GRAYSCALE)
img_color = cv2.cvtColor(img_gray, cv2.COLOR_GRAY2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img_color)
plt.title("Colour Image")
plt.axis("off")
plt.show()

height, width, channel = img_color.shape

print("Width :", width)
print("Height:", height)
print("Channel:", channel)
```

#### 7. Crop the image to extract any specific object from the image.
```python
cropped = img_color[150:450, 200:500]

plt.imshow(cropped)
plt.title("Cropped Image")
plt.axis("off")
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```python
resized = cv2.resize(
    img_color,
    None,
    fx=2,
    fy=2,
    interpolation=cv2.INTER_LINEAR
)

plt.imshow(resized)
plt.title("Resized Image (2x)")
plt.axis("off")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
flipped = cv2.flip(cropped, 1)

plt.imshow(flipped)
plt.title("Horizontally Flipped Image")
plt.axis("off")
plt.show()
```

#### 10. Read in the image ('city.jpg').
```python
img = cv2.imread('spidey.jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image).
```python
text = "Smart City View"
font_face = cv2.FONT_HERSHEY_PLAIN

text_position = (180, img_rgb.shape[0] - 20)

cv2.putText(
    img_rgb,
    text,
    text_position,
    font_face,
    2,
    (255, 255, 255),
    2,
    cv2.LINE_AA
)
```

#### 12. Draw a magenta rectangle that encompasses any prominent object in the image.
```python
rect_color = (255, 0, 255)

cv2.rectangle(
    img_rgb,
    (250, 180),
    (500, 450),
    rect_color,
    3
)
```

#### 13. Display the final annotated image.
```python
plt.imshow(img_rgb)
plt.title("Annotated City Image")
plt.axis("off")
plt.show()
```

#### 14. Read the image ('city.jpg').
```python
img = cv2.imread('spidey.jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 15. Adjust the brightness of the image.
```python
# Create a matrix of ones (with data type float64)

matrix = np.ones(img.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img, matrix)
img_darker = cv2.subtract(img, matrix)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_darker, cv2.COLOR_BGR2RGB))
plt.title("Darker Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_brighter, cv2.COLOR_BGR2RGB))
plt.title("Brighter Image")
plt.axis("off")

plt.show()
```

#### 18. Modify the image contrast.
```python
# Create two higher contrast images using the 'scale' option
# with factors of 1.1 and 1.2 (without overflow fix)

img_higher1 = cv2.convertScaleAbs(img, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(img, alpha=1.2, beta=0)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_higher1, cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.1")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_higher2, cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.2")
plt.axis("off")

plt.show()
```

#### 20. Split the image into the B, G, R components & Display the channels.
```python
B, G, R = cv2.split(img)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(B, cmap="gray")
plt.title("Blue")

plt.subplot(1,3,2)
plt.imshow(G, cmap="gray")
plt.title("Green")

plt.subplot(1,3,3)
plt.imshow(R, cmap="gray")
plt.title("Red")

plt.show()
```

#### 21. Merge the R, G, B displays along with the original image.
```python
merged_rgb = cv2.merge((R, G, B))

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1,2,2)
plt.imshow(merged_rgb)
plt.title("Merged RGB")

plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

H, S, V = cv2.split(hsv)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(H, cmap="gray")
plt.title("Hue")

plt.subplot(1,3,2)
plt.imshow(S, cmap="gray")
plt.title("Saturation")

plt.subplot(1,3,3)
plt.imshow(V, cmap="gray")
plt.title("Value")

plt.show()
```

#### 23. Merge the H, S, V displays along with the original image.
```python
merged_hsv = cv2.merge((H, S, V))
merged_bgr = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2BGR)

plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original")

plt.subplot(1,2,2)
plt.imshow(cv2.cvtColor(merged_bgr, cv2.COLOR_BGR2RGB))
plt.title("Merged HSV")

plt.axis("off")
plt.show()
```

## Output:
<img width="712" height="423" alt="image" src="https://github.com/user-attachments/assets/7571a1da-8107-4082-a430-7b97e3ba5d11" />
<img width="693" height="437" alt="image" src="https://github.com/user-attachments/assets/6561912d-354c-447d-96e6-55ba7335cdec" />
<img width="776" height="416" alt="image" src="https://github.com/user-attachments/assets/5979da3d-e11b-41cd-8b63-49e180429706" />
<img width="785" height="413" alt="image" src="https://github.com/user-attachments/assets/528d9754-5956-4832-a784-ce6358112581" />
<img width="690" height="432" alt="image" src="https://github.com/user-attachments/assets/e3f0eb6f-e7b3-429c-a390-4620c3cd825f" />
<img width="715" height="452" alt="image" src="https://github.com/user-attachments/assets/237bf799-4f38-4c7c-b7cb-d0244bbddec3" />
<img width="812" height="442" alt="image" src="https://github.com/user-attachments/assets/7e93c3e4-c374-45c8-b56a-291f25e41529" />
<img width="802" height="457" alt="image" src="https://github.com/user-attachments/assets/711eea53-d7f3-465f-8593-eacf0964efac" />
<img width="777" height="452" alt="image" src="https://github.com/user-attachments/assets/748e8327-39c8-46cc-afae-1639d3857636" />
<img width="890" height="467" alt="image" src="https://github.com/user-attachments/assets/ac581b7d-2fb7-4110-abbe-dac5033bcbdf" />
<img width="802" height="415" alt="image" src="https://github.com/user-attachments/assets/9991ba2c-9a9c-45db-bab9-84e1d0d659d3" />
<img width="718" height="555" alt="image" src="https://github.com/user-attachments/assets/eb923692-44c4-4cbb-b55a-5866a5e2a0fb" />
<img width="575" height="532" alt="image" src="https://github.com/user-attachments/assets/98e032a9-dd6d-4297-af49-970b40963e25" />
<img width="792" height="452" alt="image" src="https://github.com/user-attachments/assets/fdb3b0e7-97b9-4f30-8395-339307b1d7d2" />
<img width="841" height="446" alt="image" src="https://github.com/user-attachments/assets/23eae819-b97d-4847-b6d3-9e82d062b2ed" />





## Result:
Thus, the image was read and displayed successfully. Brightness and contrast adjustments were performed, the BGR and HSV channels were split and merged successfully, and the required image processing operations were implemented using OpenCV.
