from IPython.display import Image, display
display(Image(filename="blackwidow.jpg"))

import face_recognition

my_photo = face_recognition.load_image_file("blackwidow.jpg")
my_face_locations = face_recognition.face_locations(my_photo)

my_face_locations

top, right, bottom, left = my_face_locations[0]

from PIL import Image, ImageDraw
my_face=my_photo[top:bottom, left:right]
my_face_img=Image.fromarray(my_face)

display(my_face_img)

my_face_encoding = face_recognition.face_encodings(my_photo)[0]

from IPython.display import Image, display
display(Image(filename="avengers.jpg"))

group_photo = face_recognition.load_image_file("avengers.jpg")
group_face_locations = face_recognition.face_locations(group_photo)
print(len(group_face_locations))
counter=0
for face_location in group_face_locations:
  top, right, bottom, left = face_location
  group_face_encoding = face_recognition.face_encodings(group_photo)[counter]
  result = face_recognition.compare_faces([my_face_encoding], group_face_encoding)
  if result[0] == True:
    print("Found at face ", counter)
    tp, rt, bt, lt = group_face_locations[counter]
    print("The rectangle is ", tp, rt, bt, lt)
  counter+=1

import cv2
res = cv2.rectangle(group_photo, (lt, tp), (rt, bt), (0,0,255), 2)

from PIL import Image, ImageDraw
new_group_photo = Image.fromarray(group_photo)
display(new_group_photo)