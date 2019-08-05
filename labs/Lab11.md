

## Lab 11 : Sample Project - Facial Detection

In this lab, you will work with images in Python. Using a predefined library, you will try to locate faces on a photo. And once a face is found, you will try to match a specific face on the photo. The instructions for this lab are less detailed, so you might need to browse back in this document (or use google) to find the exact syntax for some statements. 

The instructions for this lab will be using a new library, `face_recognition`.

**Step 1:**

Create a new project in CDSW with a Python template, and start a Python 3 workbench with 16GB of RAM.

**Step 2:**

Install the `face_recognition` library using the `pip3 install` command.

As soon as the library is installed, stop your CDSW session. As soon as it is stopped, open a new CDSW session with 4 GB of memory, to allow other students resources to install the library.

Also, install the `opencv-python` library, to use some graphic processing capabilities.

**Step 3:** 

Try to display a photo using the Image command. Before you can use this command, you need to import some display libraries, with the statement: 

 `from IPython.display import Image, display`

 As soon as the library is imported, try to display a photo. Use the command:

`display(Image(‘<filename>’))`

In the directory with .jpg files, search for the image that you would like to use (`blackwidow`, or `ironman`)

**Step 4:**  

Detect the exact location of the face on the image, using the face_recognition library.

First, load the library:

`import face_recognition`

 Now you can use the following statement to find where the face is located on the photo:

`my_photo = face_recognition.load_image_file(“ironman.jpg”)`

`my_face_locations = face_recognition.face_locations(my_photo)`

 Check if your algorithm has detected a face, by showing the value:

`my_face_locations`

You will see a list of tuples, with the locations of where a face can be found on the photo. Most probably, you will only see 1 tuple, with 1 face on the photo. The output should be something like this:

`[(32L, 107L, 94L, 45L)]`

 This is the representation of 1 tuple, with the values [(top, right, bottom, left)], which represent the pixel in the top right corner, as well as the bottom left corner. The face on the photo is located in the square between these 2 corners.

**Step 5:**

Cut the face out of the picture. To do this, use the corners found in step 4. First, extract the corners form the array of tuples. You can do this with the following command:

`top, right, bottom, left = my_face_locations[0]`

 Now we can extract the face out of the photo, using the following statement:

`from PIL import Image, ImageDraw`

`my_face=my_photo[top:bottom, left:right]`

`my_face_img=Image.fromarray(my_face)`

 And now visualise the image, to check if it worked.

We use some libraries from PIL for that, so we need to import that first.

`display(my_face_img)`

You should see the face only now.

**Step 6:**

Use the face_recognition library to encode the face to a ‘match_code’. 

`my_face_encoding = face_recognition.face_encodings(my_photo)[0]`

The face encoding is an array of numbers that represent the face from the picture. This array is used for matching to find a face that is similarly looking.

**Step 7:**

Encode the faces on group photo.

First, show the group photo with the statement:

`from IPython.display import Image, display`

`display(Image(filename="avengers.jpg"))`

 Now, find the face locations on the group photo:

`group_photo = face_recognition.load_image_file("avengers.jpg")`

**Step 8:**

Write a loop that makes an encoding of each face in the photo, and that matches the face on the group photo with the encoding created in step 5.

 A piece of example code is here:

 `group_photo = face_recognition.load_image_file("avengers.jpg")`

`group_face_locations = face_recognition.face_locations(group_photo)`

`print len(group_face_locations)`

`for face_location in group_face_locations:`

  `top, right, bottom, left = face_location`

 ` print top, right, bottom, left`

Your hints are:

●      Find the number of faces in the group photo. Use the statement from Step 4.

●      Create a loop to an encoding for each face. Encoding is done using the statement in Step 6.

●      Match the encoding of my_photo and the face of the group_photo. 

●      `face_recognition.compare_faces([my_face_encoding], group_face_encoding)`

●      If matching is True, then draw a box around the face on the group photo.

●      Draw a box statement: 

●      `import cv2`

●      `cv2.rectangle(<image>, (left, top), (right, bottom), (0,0,255), 2)`



### End of Lab 11

**That’s It Folks**

Thanks for working your way through the labs and we hope you learned how CDSW might make your Data Science journey easier. Please fill out the survey form!

------

[Back to Main](https://github.com/rajatrakesh/cdswlabs)