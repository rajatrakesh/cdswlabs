# Lab 14: Facial Recognition

In this lab, we will work with a images using Python. We will use a pre-defined library of faces, and will try to match that in another collection of faces. 

This lab does explore the specifics of the code in detail, but aims to show you an example of how a use-case for image processing might look like, through a simple lab. 

Let's get started. 

**Step 1:** Create a new project in CDSW, you can call it 'Face Detection' if you like, and start a Python Workbench with 16 GB of RAM. 

**Step 2:** Once the session has been started, we will install the ```face_detection``` library using the ```pip install``` command. Once this library is installed, we don't need the 16 GB instance anymore, and we can shut it down.

The command is:

```!pip3 install face-recognition```
```!pip3 install opencv-python```

**Step 3: **Once the installation is completed, stop this session and start a new one in the same project, but this time with 4GB RAM. 

**Step 4:** You would now be building a sample code to test this functionality. The following elemts in the code would be critical for achieving this.

**Step 4A:** Try to display a photo using the Image command. Before you can use this command, you need to import some display libraries, with the statement:

```from IPython.display import Image, display```

**Step 4B:** As soon as the library is imported, try to display a photo. Use the command:

```display(Image(“ironman.jpg”))```

The file must exist in the root folder of your project. This will display an image with a face, that we are trying to detect. 

**Step 4C:** Detect the exact location of the face on the image, using the face_recognition library. First, load the library:

```import face_recognition```

**Step 4D:** Now you can use the following statement to find where the face is located on the photo:

```my_photo = face_recognition.load_image_file(“ironman.jpg”)```
```my_face_locations = face_recognition.face_locations(my_photo)```

**Step 4E:** Check if your algorithm has detected a face, by showing the value.

```my_face_locations```

You will see a list of tuples, with the locations of where a face can be found on the photo. Most probably, you will only see 1 tuple, with 1 face on the photo. The output should be something like this:

```[(47, 88, 121, 13)]```

**Step 4F:** Now we need to cut the face out of the picture. 
To do this, use the corners found in previous step. First, extract the corners form the array of tuples. You can do this with the following command:

```top, right, bottom, left = my_face_locations[0]```

**Step 4G:** Now we can extract the face out of the photo, using the following statement:

```from PIL import Image, ImageDraw```
```my_face=my_photo[top:bottom, left:right]```
```my_face_img=Image.fromarray(my_face)```

**Step 4H:** And now visualise the image, to check if it worked.
We use some libraries from PIL for that, so we need to import that first.

```display(my_face_img)```

You should see the face only now.

**Step 4I:** Use the face_recognition library to encode the face to a ‘match_code’.

```my_face_encoding = face_recognition.face_encodings(my_photo)[0]```

The face encoding is an array of numbers that represent the face from the picture. This array is used for matching to find a face that is similarly looking.

**Step 4J:** Encode the faces on group photo.
First, show the group photo with the statement:

```from IPython.display import Image, display```
```display(Image(filename="teamphoto.jpg"))```

**Step 4K:** Now, find the face locations on the group photo:

```group_photo = face_recognition.load_image_file("avengers.jpg")```


**Step 4L:** Write a loop that makes an encoding of each face in the photo, and that matches the face on the group photo with the encoding created.

A piece of example code is here:

```group_photo = face_recognition.load_image_file("avengers.jpg")``` 
```group_face_locations = face_recognition.face_locations(group_photo)```
```print len(group_face_locations)```

```for face_location in group_face_locations:```
```   top, right, bottom, left = face_location```
 ```  print top, right, bottom, left```
 
## Hints
 
 Your hints are:
 
- Find the number of faces in the group photo. Use the statement from Step 4C.
- Create a loop to an encoding for each face. Encoding is done using the statement provided in 4I.
- Match the encoding of ```my_photo``` and the face of the ```group_photo```.

```face_recognition.compare_faces([my_face_encoding], group_face_encoding)```

- If matching is True, then draw a box around the face on the group photo.
- Draw a box statement:

```import cv2```
```cv2.rectangle(<image>, (left, top), (right, bottom), (0,0,255), 2)```