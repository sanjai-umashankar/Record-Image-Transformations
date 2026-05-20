# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By: SANJAI U
### Register No: 212224240145
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('baseball.jpg')
image.shape

plt.imshow(image[:,:,::-1])
plt.title('Original Image')
plt.show()

# i) Image Translation
tx, ty = 100, 200  
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  
translated_image = cv2.warpAffine(image, M_translation, (636, 438)) 

plt.imshow(translated_image[:,:,::-1])
plt.title("Translated Image")
plt.axis('on')
plt.show()
fx, fy = 2.0, 1.0  
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
plt.imshow(scaled_image[:,:,::-1]) 
plt.title("Scaled Image") 
plt.axis('on')
plt.show()
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  
sheared_image = cv2.warpAffine(image, shear_matrix, (636, 438))
plt.imshow(sheared_image[:,:,::-1])
plt.title("Sheared Image") 
plt.axis('on')
plt.show()
reflected_image = cv2.flip(image, 2)  
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(image[:, :, ::-1])
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(reflected_image[:,:,::-1])
plt.title("Reflected Image")
plt.axis('off')

plt.tight_layout()
plt.show()
(height, width) = image.shape[:2]  
angle = 45 
center = (width // 2, height // 2) 
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  
rotated_image = cv2.warpAffine(image, M_rotation, (width, height)) 
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB)) 
plt.title("Rotated Image")  
plt.axis('off')
image .shape    
angle = 145  
center = (636 // 2, 438 // 2)  
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  
rotated_image = cv2.warpAffine(image, M_rotation, (width, height)) 
plt.imshow(rotated_image[:,:,::-1])  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')
plt.show()
# Image Cropping
x, y, w, h = 0, 0, 200, 150  

cropped_image = image[y:y+h, x:x+w]   
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(image[:, :, ::-1])
plt.title("Original Image")
plt.axis('on')

plt.subplot(1, 2, 2)
plt.imshow(cropped_image[:,:,::-1])
plt.title("Cropped Image")
plt.axis('on')

plt.tight_layout()
plt.show()
```
## OUTPUT
### Original Image
<img width="622" height="470" alt="image" src="https://github.com/user-attachments/assets/a195564f-d9a6-41d3-9711-91f421ed0758" />


### Image Translation
<img width="632" height="470" alt="image" src="https://github.com/user-attachments/assets/6b63a980-b562-4b7d-8249-4ea96cb9ec8d" />


### Image Scaling

<img width="630" height="222" alt="image" src="https://github.com/user-attachments/assets/1280771c-f3b2-4256-85c9-f529ab582518" />


### Image Shearing
<img width="632" height="462" alt="image" src="https://github.com/user-attachments/assets/ea26c892-2bcc-4b70-8fc7-fa8be4f72d16" />


### Image Reflection
<img width="617" height="461" alt="image" src="https://github.com/user-attachments/assets/24f05fed-ce53-42d2-8717-30a62066b0b4" />


### Image Rotation
<img width="635" height="462" alt="image" src="https://github.com/user-attachments/assets/5eaafef7-1bcd-4721-9d34-ab8abbe49089" />


##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
