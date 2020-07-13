# Documnetation
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
