# IMAGE-TO-PENCIL-SKETCH
#IMPORTING NECESSARY LIBRARIES
import cv2
from google.colab.patches import cv2_imshow
#IMPORTING THE IMAGE USED
img = cv2.imread("/content/nature img.png")
#DISPLAYING THE IMAGE USED
cv2_imshow(img)
#CONVERTING IMAGE TO GRAYSCALE
gray_img = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
#DISPLAYING GRAYSCALE IMAGE
cv2_imshow(gray_img)
#INVERTING THE IMAGE
invert_img = cv2.bitwise_not(gray_img)
#DISPLAYING INVERTED IMAGE
cv2_imshow(invert_img)
#SMOOTHING THE IMAGE USING GAUSSIAN BLUR
smooth_img = cv2.GaussianBlur(invert_img,(21,21),sigmaX=0,sigmaY=0)
#DISPLAYING SMOOTH IMAGE
cv2_imshow(smooth_img)
#CONVERTING TO PENCIL SKETCH
def finalsketch(x, y):
  return cv2.divide(x, 255 - y, scale=256)
#DISPLAYING FINAL PENCIL SKETCH
final_img = finalsketch(gray_img, smooth_img)
cv2_imshow(final_img)
#COMPARING PICTURE USED AND SKETCH OBTAINED
print("Image used")
cv2_imshow(img)  
print("\n")
print("Pencil sketch obtained using image")
cv2_imshow(final_img)
