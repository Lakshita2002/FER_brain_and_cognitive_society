# Documnetation
## Libraries Used
* tensorflow
* keras
* mlxtend  (resource link)
* openCV

## Datasets Used
* JAFFE   : No of pictures:___ ,  Link of dataset
* Ck-plus : No of pictures: ___ , Link of dataset

## Steps implemented  [Link of implemented Research Paper](https://link.springer.com/article/10.1007/s00371-019-01627-4)
## `Image Loading` 
_Function_ : **Load_dataset**\
**To read all the images of the dataset and convert them into an array**\
**_Input_** : \
_img_dir_ -- path to the images folder\
_emotion_code_ -- list containing emotion labels\

**_Returns_** : <br/>
_img_data_ -- array representing images, of shape (Number of images, pixels, pixels)\
_labels_ -- list of index values(emotion_code) associated with each image\
_img_names_ -- list of names of image files\

## `Image Rotation` 
_Function_ : **Load_dataset**\
**Corrects the tilt of a rotated image given the angle(degrees) to be rotated **\
**_Input_** : \
_image_ -- image to be rotated in (pixels,pixels) shape\
_angle_ -- output of _find angle_ function :angle required to align the image horizontally\
**_Returns_**:\
perfectly Horizontal image\

## `Preprocessing` [Reference repository Link](https://github.com/anas-899/facial-expression-recognition-Jaffe)
**The preprocessing involves rotation of the image and image cropping.**\ 
**Rotation**
The rotation angle for horizontal alignment is calculated on the basis of the eyes centers and then the image is rorated to mke it horizontal 
* _Sequence of the predefined functions used for Rotation:_ eye_centers(landmarks) -->  find_angle(p1, p2) --> rotate_image(img, angle)

**Cropping**
The forehead region was then removed in such a way that
perpendicular distance from the top side of the cropped image
to the horizontal line connecting the eye centres is 0.6 d (d
is the distance between eye centres),The other three sides of the cropped image are defined by the
coordinates of 1st, 9th, and 17th face landmark points.
* _Sequence of steps used for Cropping:_ eye centers for rotated image using eye_centers(extract_face_landmarks(rot_img)) ---> find d, the distance between the two eye centers--> find d_mid, mid point of the 2 eye centers --> crop_img with img(y_start:y_end,x_start:x_end) where y_start: a coordinate 0.6d distance above from the mid point of line joining both eyes, y__end: 9th landmark, x_start: 1st landmark, x_end: 17th landmark

**_Input_** : \
input_images-- array of images of shape (Number of images, pixels, pixels)\
**_Returns_**:\
_preprocessed_faces_ -- array of images after preprocessing (Number of images, pixels, pixels)

## Functions used
_Function:_ `eye_centers(landmark)`<br>
__To find the center of the eye in the image__<br>
_landmark_ -- 6 landmark points around the eyes<br>
point1 is the mean of landmark points 36-41<br>
point2 is the mean of landmark points 42-47<br>

_Returns:_ `(point1, point2)`<br>
_point1_ -- center of right eye<br>
_point2_ -- center of left eye<br>

_Function:_ `find_angle(point1, point2)`<br>
__To find the angle that the line joining these 2 points makes with the horizontal__<br>
_point1_ -- center of right eye<br>
_point2_ -- center of left eye<br>
Using the arctangent `math.atan()` function in math library, we calculate the angle in radians<br>
Using the degrees conversion function `math.degrees()` we then convert it into degrees<br>

_Returns:_ `(angle_d)`<br>
_angle_d_ -- angle in degrees with the horizontal<br>

_Function:_ `normalization(imagedata, mean, std_dev)`<br>
__To apply Histogram equalization and Z-Square Normalization to the preprocessed images
    Arguments__<br>
_imagedata_ -- array of preprocessed images of shape (m,h,w)<br>
_mean_ -- mean of imagedata array<br>
_std_dev_ -- standard deviation of imagedata array<br>
We applied the opencv function `cv2.equalizeHist()` on the pre-processed images for histogram equalization<br>
Z-score normalisation is done using the simple formula `[(value-mean)/standard_deviation]`<br>
The normalized images are then resized to `48x48` size using `cv2.resize()`<br>
The resized images are then appended into the _normalised_images_ array using `np.append()` function<br>

_Returns:_ `(normalised_images)`<br>
_normalised_images_ -- array of normalised and resized images<br>
