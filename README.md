# Customer Churn Prediction

## Project Overview
*  This projects predicts whether a customer is likely to stop using a company's services (ie. 'Churn') based on historical data. It's designed for Telecommunication companies but can be adapted to other industries.

* The project includes two main components: model training (main.py) and a web application (app.py) for interactive prediction.

## Project files
1. Dataset: Telco Customer Churn sourced from HuggingFace
    
    The dataset contains information about customers of a fictional telecommunications company, including demographic information, services subscribed to, location details, and churn behavior. The dataset combines the information from the original Telco Customer Churn dataset with additional details.

    The dataset is structured as a CSV file with 49 columns, each representing a customer attribute. The columns include:
* Customer Details: Age, Gender, Senior Citizen, Married, Dependents
* Service Usage: Internet Service, Internet Type, Streaming TV/Music/Movies, Phone Service, Multiple Lines, Device Protection, Online Security/Backup, Premium Tech Support, Unlimited Data
* Billing & Payments: Monthly Charges, Total Charges, Total Refunds, Payment Method, Paperless Billing, Contract Type, CLTV
* Churn Information: Churn Label, Churn Score, Churn Reason, Churn Category, Churn Value
* Location: City, State, Country, Zip Code, Latitude, Longitude, Population
* Other Features: Tenure in Months, Number of Referrals, Referred a Friend, Satisfaction Score

2. main.py:
    * Libraries Used : 
        * pandas : for data manipulation
        * pycaret.classification : for automated machine learning workflow.

    * Workflow:
        1. Load Dataset: Loads customer data from Dataset/train.csv.
        2. Ignore Non-Predictive Features: Certain columns such as customer ID, location details, and churn reasons are excluded from modeling to avoid leakage.
        3. Initialize PyCaret: Sets up the classification experiment with normalization, target variable Churn, and ignored features.
        4. Model Comparison: Uses PyCaret’s compare_models() to test multiple classification algorithms and selects the best performing one.
        5. Model Finalization: Finalizes the best model to prepare it for deployment.
        6. Model Evaluation: Provides an interactive interface to evaluate the finalized model's performance metrics.
        7. Model Saving: Saves the finalized model as churn_model for later use.

    * Output:

        * Trained and saved churn prediction model ready for inference.

3. app.py:
    * Libraries Used
        * streamlit: For building the interactive web app interface.
        * pandas: To organize user inputs into a DataFrame.
        * pycaret.classification: To load the saved model and perform prediction.

    * Workflow
        1. Load Model: Loads the trained churn_model.
        2. User Input: Collects customer details using Streamlit widgets including age, contract type, service subscriptions, monthly charges, and more.
        3. Input Processing: Converts "Yes"/"No" inputs to numerical format (1/0) as required by the model.
        4. Prediction: Upon clicking "Predict Churn", the app creates a DataFrame of inputs and runs it through the model to predict churn probability or label.
        5. Output Display: Shows the model’s prediction output, including churn probability if available, and indicates whether the customer is predicted to churn ("Yes") or not ("No").

    * User Interaction
        * Intuitive interface to enter customer features.
        * Immediate churn prediction displayed with clear labeling.

## How To Run

1. Ensure Python environment has required packages : pandas, pycaret, streamlit. (if not, install them using pip install <package_name>)
2. Place the dataset in "Dataset/train.csv".
3. Run main.py to train and save the model(first time only).
4. Run the streamlit app using the command in terminal: streamlit run app.py.
5. Use the web app interface to input customer data and get churn predictions.


### NOTES
* The model training uses automated machine learning to select the best classification model for the churn dataset.
* The app expects inputs to be consistent with the training data features and formats. 
* Columns ignored during training are excluded in prediction inputs to avoid data leakage.

        


