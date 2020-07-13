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

