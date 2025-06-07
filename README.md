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

12        Figure 1 Data Extraction code


Model Training:
After getting the data and labels saved, we loaded the data and then split it into training and testing sets with a normal shuffle and then fit it to the model with a randomforestclassifier algorithm to train on. Afterwards we did a simple prediction test for accuracy and saved the model to a pickle file as it’s the easiest to use format for saving models.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/2c2fc7b0-3f91-4b41-b091-8c9d609901fc" />
13         Figure 2 Model Code

Main functionality and Interfaces:
Instead of showing codes, and there are a lot of them for the main, we will show the interface and explain each part of it fully as it’s the important part of the implementation here and the code would just fill the pages uselessly.

 
 Main Menu:
A simple main menu that includes a synopsis of the team and project. There are two buttons here, one to go to start translating and another one that shows the saved translation text which is done in the translating page.


![image](https://github.com/user-attachments/assets/aae8f5a6-0457-49b1-8ccf-dd4d1b28b0e9)
14          Figure 3 Esharat Main Menu






