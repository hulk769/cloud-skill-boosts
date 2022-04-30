# Perform Foundational Infrastructure Tasks in Google Cloud: Challenge Lab

[YouTube Video Link](https://youtu.be/ZdZ3SiarZrs)

## Let's start with defining some variables given by Cloud Skill Boosts

Defining Cloud Function name variable
```
export CLOUDFUNCTION_NAME=
```
Defining entrypoint variable
```
export ENTRYPOINT=
```

## Downloading main.py and requirements.txt file we will use this while creating cloud function 

```
wget https://github.com/guys-in-the-cloud/cloud-skill-boosts/raw/main/Challenge-labs/Build%20Interactive%20Apps%20with%20Google%20Assistant:%20Challenge%20Lab/main.py

wget https://github.com/guys-in-the-cloud/cloud-skill-boosts/raw/main/Challenge-labs/Build%20Interactive%20Apps%20with%20Google%20Assistant:%20Challenge%20Lab/requirements.txt

```

## Task 1: Create the Cloud Function for the Magic Eight Ball app

1.1 Replacing the variable with REPLACE_WITH_YOUR_ENTRY_POINT
```
sed -i "s/REPLACE_WITH_YOUR_ENTRY_POINT/$ENTRYPOINT/g" main.py
```

1.2 Deploy the function 
```
gcloud functions deploy $CLOUDFUNCTION_NAME \
    --entry-point $ENTRYPOINT \
    --runtime python39 \
    --max-instances 5 \
    --trigger-http --allow-unauthenticated \
    --region us-central1
```

## Task 2: Create the Magic 8 Ball app for Google Assistant

Goto to the Action Console link provided --> New Project --> select new project --> import project --> click on your project --> action console --> click on your project --> Decide how your Action is invoked --> Enter Display Name (magic 8 ball) --> Save

Build your Action:
Go to Action console --> click on your project --> Build your Action --> Add Action(s) --> Get Started --> Build --> Sign in with your account in the Dialogflow window(if needed) --> create --> Fullfillment --> Webhook --> Enable --> Enter url --> here enter the trigger url of the cloud function created --> Save 

Intents --> Click on "Default Welcome Intent" --> Responses --> Add Responses --> Text Response --> Enter "Welcome to the lab magic 8 ball, ask me a yes or no question and I will predict the future!"
as response --> Save

Intents --> Click on "Default Fallback Intent" --> Responses --> enable Set this intent as end of conversation --> Fulfillment --> enable Enable webhook call for this intent --> Save

You can test in Dialogflow to ensure it works.

## Task 3: Add multilingual support to your Cloud Function

Cloud Funcctions --> Trigger --> Edit --> Next --> Update the main.py file at line 13(line no. may differ) --> Deploy 

Goto to Dialogflow window --> Test --> Test the sentences

# Congratulations you've completed your challenge lab
## Happy Learning
## See you in the cloud..

