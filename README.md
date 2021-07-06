## STREAMLIT LIBRARY:

	Its a WEB APP FRAMEWORK like FLASK
	In Streamlit no need to have template folder, static folder with xml file like Flask . 
	Its app.py file only will have html and python code integrated to make our web page design

## Problem Statement:
### Bank Note Authentication
Data were extracted from images that were taken from genuine and forged banknote-like specimens. For digitization, an industrial camera usually used for print inspection was used. The final images have 400x 400 pixels. Due to the object lens and distance to the investigated object gray-scale pictures with a resolution of about 660 dpi were gained. Wavelet Transform tool were used to extract features from images.

https://github.com/krishnaik06/Dockers

To Understand Docker and Strealit, i have downloaded already built project folder from Krish naik Github
So actual python code is MOdelTraining.ipynb. I have already created classifier.pkl file, app.py , requirement.txt , (templates, static not req)
Just i did deployment by syncing this in my github

### Approach:
By using Linear RandomForset Regressor , we are predicting the JBank Note Authentication based on user input data as 0 or 1
Here we have 4 input value: variance,skewness,curtosis,entropy output class 0 or 1
  > 0 means real note, 1 is fake note

Here we used Streamlit web application Framework and deployed in Heroku(PlatformAs A service-PAAS) using gIThUB.


## Deployment via Heroku by using STREAMLIT LIBRARY:
#### 1. Deployment main files:
  app.py
  model.pkl
  requirements.txt (It should have streamlit library)
  Procfile
  setup.sh  (This used inside Procfile)



#### 2. Install streamlit in anaconda 
		conda install -c conda-forge streamlit

#### 3) procfile:
	This file required to deploy in Heroku env

	So write below statement inside of procfile  (but in flask procfile script like this: web: gunicorn app:app)
	
		web: sh setup.sh && streamlit run app.py

	
	Create Proc file:

		In cmd write below line
			echo web: sh setup.sh && streamlit run app.py >Procfile

#### 4) Create setup.sh file:
	
	This is streamlit related .sh file. inside it has below line. This is batch program, it creates batch script.

		mkdir -p ~/.streamlit/
		echo "\
		[general]\n\
		email = \"your-email@domain.com\"\n\
		" > ~/.streamlit/credentials.toml
		echo "\
		[server]\n\
		headless = true\n\
		enableCORS=false\n\
		port = $PORT\n\
		" > ~/.streamlit/config.toml


#### 4) Run Streamlit Local Run:

	Run this in local environment with below command in anaconda
	
	cd C:\Users\prabh\DS Project Toolkit\Project\Dockers_master_AND_Streamlit\Bank_Note_Authentication_Streamlit
	
		streamlit run app.py


	Error: We got below error " module 'google.protobuf.descriptor' has no attribute '_internal_create_key'"
		upgrade 
		
		--> Tried all method to fix, not resolved in local machine
				conda install -c anaconda protobuf

		--> By above error its failing in Local, but got deployed in Heroku and showing values correctly

#### 5) Deploy in Heroku
	
	Upload to Github and Deploy in Heroku as normal process
