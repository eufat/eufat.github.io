---
title: Hyperspectral Image Preprocessing with Python
---

This is the preliminary prerequisites you need if you want to build a preprocessing system using Python.

- Anaconda
- SpectralPy
- RAW and HDR file from hyperspectral camera

As usual we import the required modules, we use spectral library for opening files, numpy for numerical processing and matplotlib for visualization.
```python
from spectral import imshow, view_cube
import spectral.io.envi as envi
import numpy as np
import matplotlib.pyplot as plt
import matplotlib
```
Using `envi.open()` function we open both RAW and HDR file, we need three type of data here: dark reference, white reference and data capture.
```python
dark_ref = envi.open('path/to/dark_reference.hdr', 'path/to/dark_reference.raw')
white_ref = envi.open('path/to/white_reference.hdr', 'path/to/white_reference.raw')
data_ref = envi.open('path/to/data_capture.hdr', 'path/to/data_capture.raw')
```
With numpy, we convert the loaded data to numpy array tensor, as oposed of standard Python array.
```python
white_nparr = np.array(white_ref.load())
dark_nparr = np.array(dark_ref.load())
data_nparr = np.array(data_ref.load())
```
Using correction formula, the captured data is subtracted by dark reference and divided with white reference subtracted dark reference.
```python
corrected_nparr = np.divide(
    np.subtract(data_nparr, dark_nparr),
    np.subtract(white_nparr, dark_nparr))
```
With this [file](https://raw.githubusercontent.com/eufat/skripsi/master/notebooks/helpers/bands.csv) that represent each value of spectral bands we can display each pixel spectral features as figured with reflectance versus wavelength.
```python
bands = np.genfromtxt('bands.csv', delimiter=',')
```
Using selected pixel by defining its coordinae we can call the pixel vector from above corrected hyperspectral tensor. Then we squeeze to acquire un-arrayed elements of vector. At last, we could plot its spectral footprint.
```python
leaf_pixel_y = 75
leaf_pixel_x = 200

leaf_pixel = corrected_nparr[
    leaf_pixel_y:leaf_pixel_y+1,
    leaf_pixel_x:leaf_pixel_x+1,
    :]

leaf_pixel_squeezed = np.squeeze(leaf_pixel)

plt.plot(bands, leaf_pixel_squeezed)
plt.title('Leaf Spectral Footprint\n(Pixel {},{})'.format(
    leaf_pixel_x, leaf_pixel_y))
plt.xlabel('Wavelength')
plt.ylabel('Reflectance')
plt.show()
```
To acquire ROI that we will use for processing phase (training phase) we can extract the ROI by using bounding box method.
```python
def extract_roi(arr, x, y, w, h, intensity, line):
    roi = arr[y:y+h, x:x+w, :]

    bounding_box = arr
    bounding_box[y-line:y, x-line:x+w+line, :] = intensity # garis atas
    bounding_box[y:y+h, x-line:x, :] = intensity # garis kiri
    bounding_box[y+h:y+h+line, x-line:x+w+line, :] = intensity # garis bawah
    bounding_box[y:y+h, x+w:x+w+line, :] = intensity # garis kanan

    return (roi, bounding_box)

coordinates = [
    (105, 65),
    (120, 60),
    (160, 65),
    (215, 65),
    (265, 65),
    (320, 50)]

rois = [] # returned ROIs
length = 50 # width and height
intensity = 2 # bounding box line intensity
line = 0 # bounding box line width
bounding_boxed = corrected_nparr

for coordinate in coordinates:
    (x, y) = coordinate
    (roi, bounding_boxed) = extract_roi(
        bounding_boxed, x, y, length, length, intensity, line)
    rois.append(roi)

imshow(bounding_boxed, (100, 100, 100))
```
Finally, to get the averaged spectral features in each boxes we could `np.mean()` function.
```python
for i in range(len(rois)):
    roi = rois[i]
    intensity = []
    for b in range(roi.shape[2]):
        intensity.append(np.mean(roi[:, :, b]))
    plt.plot(bands, intensity, label='ROI {}'.format(i+1))

plt.legend(loc='upper left')
plt.title('Leaf Spectral Footprint\n Mean in ROI Area')
plt.xlabel('Wavelength (nm)')
plt.ylabel('Reflectance')
plt.show()
```