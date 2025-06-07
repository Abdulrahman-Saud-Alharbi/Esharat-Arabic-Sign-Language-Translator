Esharat - The Arabic Sign Language Translation App


There are over 500,000 hearing-impaired people in Saudi Arabia, and a lot of them face daily hardships when trying to communicate with other people, and the same thing happens when other people try and communicate with them, as most people don’t know sign language. Translators have helped in bringing people with different backgrounds and cultures together, so what if we did the same thing, but with Saudi Sign Language?

In Our Project, we aim to create an easy-to-use, fast, and efficient Saudi Sign Language translator. This will be done by creating a machine learning model trained on datasets of Arabic/Saudi Sign Language and then using it in an application we will develop that takes a live camera feed and tracks hand movement and recognizes hand gestures efficiently.

Implementation

Our project is implemented entirely in the program code, there is no database and no physical tools or hardware that is used aside from a webcam. The implementation is split into three core parts. First, hand detection and tracking and data extraction which is done in multiple parts of the code, but we’ll show one of them only as it’s the same method. Second, model training on the data extracted from the dataset, we created our own dataset. Lastly, the translation and text saving which is the part that will be used by the users in the program.
Here we will introduce each major library and explain what it was used for. Afterwards we will show the program and how each part functions.

Mediapipe:
One of the core parts of the project is hand detection and tracking and we did that entirely through the Mediapipe HANDS model which tracks the user’s hand movement by detecting specific landmarks on each finger, these landmarks are XYZ coordinates. We use the X and Y coordinates to detect hand gestures, and this detection is used in two ways, extracting data from the dataset pictures so we can train the model, and translating sign language with the trained model.

SKLearn:
SKLearn provides a wide range of machine learning algorithms that can be used to process data and train a model efficiently. We decided to go with SKLearn instead of Keras because of its simplicity and having some algorithms that are useful to our project, here we used the randomforestclassifier algorithm which goes through a voting system between trees to decide the outcome of the prediction. This algorithm is good for a project of this scale but might cause problems in accuracy with much larger projects. 

Kivy:
A core focus of our project is creating an efficient to use program that anyone can use intuitively without even needing a guide. We decided to go with the Kivy library for our interface, it’s simple to use and extremely flexible to out needs and requirements for the program.

Data Extraction Code:
Before going into the main implementation codes, this is the code used for data extraction from the dataset for model training as explained before and then saving to a pickle file so that the data and labels are saved together.


<img width="351" alt="image" src="https://github.com/user-attachments/assets/e12f0886-df2a-46a4-85b8-0264562e55f6" />

-

<img width="351" alt="image" src="https://github.com/user-attachments/assets/476ca65c-98cb-4d35-bc58-42e9a6c28329" />
Figure 1 Data Extraction code


Model Training:
After getting the data and labels saved, we loaded the data and then split it into training and testing sets with a normal shuffle and then fit it to the model with a randomforestclassifier algorithm to train on. Afterwards we did a simple prediction test for accuracy and saved the model to a pickle file as it’s the easiest to use format for saving models.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/2c2fc7b0-3f91-4b41-b091-8c9d609901fc" />
Figure 2 Model Code

Main functionality and Interfaces:
Instead of showing codes, and there are a lot of them for the main, we will show the interface and explain each part of it fully as it’s the important part of the implementation here and the code would just fill the pages uselessly.

 
 Main Menu:
A simple main menu that includes a synopsis of the team and project. There are two buttons here, one to go to start translating and another one that shows the saved translation text which is done in the translating page.


![image](https://github.com/user-attachments/assets/aae8f5a6-0457-49b1-8ccf-dd4d1b28b0e9)
Figure 3 Esharat Main Menu


 Translation Page:
This page contains the bulk of our program, almost every functionality is accessed and done through here. First there’s a camera window, through here the program will track hand movement for translation purposes, after the program predicts the hand gesture, it will be written below the camera window. If the hand isn’t shown to the camera the program will print out a space character.
Below that we have four buttons, from left to right:
-	Delete Translation: Deletes the written translation and begins a new one.
-	Save Translation: Saves the current translation into a file that can be viewed in the saved translation page.
-	Stop Translation: Stops the app.
-	Delete: Deletes the last written letter.


  ![image](https://github.com/user-attachments/assets/0eeb183b-9a3e-4ef9-b92b-b0ba00394292)
  Figure 4 Translation Page

 Saved Translation Text Page:
Here you can read the translation you saved previously, saving a new translation will wipe the currently saved one.


![image](https://github.com/user-attachments/assets/64b493ae-91d3-4ae1-a247-d769ae88f968)
Figure 5 Saved Translation Text Page

Testing
 7.1 Introduction:
A testing phase is an important phase in a software’s development cycle, here we can verify that everything works as intended without major issues. During this phase we will make tests that guarantee that the implementation of each functionality meets our project requirements and works as flawlessly as possible and works under most needed circumstances.
First, we will write test descriptions with tasks that have certain paths that lead to certain expected results, if these results are reached by completing the paths, then the program passed the tests.
 7.2 Tasks and Paths:
There are 5 main tasks in our program, these tasks are essential for our project and have an important requirement which is efficiency and ease of use, and so, our tests are written with those in mind:
•	Task 1: Start Translation
•	Task 2: Translate a hand gesture
•	Task 3: Delete a translated letter
•	Task 4: Delete all of the translated text
•	Task 5: Save the translated text and view it
•	Task 6: Stop the translation

 
Below is a table with the correct path for each task, these will be used in testing:
8 Table 7.1 Task Navigation Paths
Task No.	Task Name	Correct Path
1	Start Translation	Main Menu > Start Translation
2	Translate a hand gesture	Start Translation > Hand gesture to the camera
3	Delete a translated letter	Start Translation > Hand gesture > Delete
4	Delete all of the translated text	Start Translation > Hand gesture > Delete Translation
5	Save the translated text and view it	Start Translation > Hand gesture > Save Translation > Back arrow to Main Menu > Translated Text
6	Stop the translation	Start Translation > Stop Translation







