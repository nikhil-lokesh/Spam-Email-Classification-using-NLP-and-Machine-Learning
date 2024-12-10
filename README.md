# Spam-Email-Classification-using-NLP-and-Machine-Learning
The purpose of this code is to create a simple web interface that allows users to input an email and classify it as either spam or not spam using a pre-trained machine learning model.

Detailed Breakdown:
Import Libraries:

python 
Copy code



import streamlit as st
import pickle
streamlit: A web framework for creating interactive web applications directly from Python scripts.
pickle: A module for loading (unpickling) the pre-trained machine learning model and vectorizer.
Load Pre-trained Model and Vectorizer:

python
Copy code


model = pickle.load(open(r'C:\Users\nikhi\OneDrive\Desktop\Spam_AICTE_PRO\spam123.pkl', 'rb'))
cv = pickle.load(open(r'C:\Users\nikhi\OneDrive\Desktop\Spam_AICTE_PRO\vec123.pkl', 'rb'))
Load the trained model from the specified file path.
Load the text vectorizer (CountVectorizer or similar) from the specified file path. These were previously saved using the pickle module.
Define the main Function:

python
Copy Code


def main():
    st.title("Spam Email Classification")
    st.markdown("Classify emails as **Spam** or **Not Spam** using Machine Learning.")
Define the main() function, which will be the entry point to the Streamlit app.
Set the app title.
Add a markdown description explaining the app's functionality.
User Input:

python
Copy Code


user_input = st.text_area("Enter your email for classification", height=150, max_chars=1000)
Create a text area widget for users to enter the email they want to classify.
Set some constraints like height and maximum characters allowed.
Classify Button:

python
Copy Code


if st.button("Classify Email"):
    if user_input:
        data = [user_input]
        vect = cv.transform(data).toarray()
        result = model.predict(vect)
        if result[0] == 0:
            st.success("This is NOT a Spam Email")
        else:
            st.error("This is a Spam Email")
    else:
        st.warning("Please enter an email to classify.")
When the "Classify Email" button is pressed, the following steps occur:
Check if there is user input:
If the input is non-empty, proceed; otherwise, warn the user to enter an email.
Transform User Input:
Convert the user input email into a list.
Use the vectorizer (cv) to transform the input text into the numerical format required by the model.
Classify the Input:
Use the loaded model to predict if the email is spam or not spam.
Display the Result:
If the model predicts 0, show a success message indicating the email is not spam.
If the model predicts 1, show an error message indicating the email is spam.
Run the Application:

python
Copy Code


main()
Call the main() function to run the application.
Summary:
This Streamlit application provides an interface for users to input an email text.
It uses a pre-trained machine learning model to classify the email as spam or not spam.
The results are displayed on the web page, giving immediate feedback to the user.
This code is efficient for creating a simple and interactive web app where users can test the spam classification model without needing to understand the underlying machine learning processes. The Streamlit framework makes it easy to build and deploy such applications quickly.
