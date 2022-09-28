# Education_Pathways

This is a modified version of the previous Assignment1 template.

The deploye version can be found at https://lab3-docker.herokuapp.com".

## Changes
+ Remove hardcodes of backend urls.
+ Remove hardcodes of database, and replace the database with dummy static data.


## How to run it locally

+ Enter the repo directory
+ Create a virtual environment if you haven't done this before. Activate it. 
```
#Windows
py -3 -m venv venv
venv\Scripts\activate

#For Mac and Linux, please check the link: https://flask.palletsprojects.com/en/2.2.x/installation/
```
+ Install dependencies
```
pip install -r requirements.txt
```
+ Enter the Education_Pathways/ directory, run the backend
```
flask --app index --debug run
```
+ Enter the frontend/ directory
+ Make sure the baseURL is set as `localhost:5000`
```
# Education_Pathways/frontend/src/api.js
export default axios.create({
   baseURL: "http://localhost:5000/" -- baseURL for running it locally
});
```
+ Make sure the proxy link in package.json is set as "http://localhost:5000/"
```
...
"private": true,
"proxy": "http://localhost:5000/",
...
```

+ Build and run the frontend:
```
npm run build
npm start
```
+ Then you will see the application at `localhost:3000`


## Build and run with Docker

For detailed instructions on Docker, please refer to the documents for Lab3 on Quercus.

+ Change the proxy link in package. Remember to change it back to "http://localhost:5000/"
```
#Education_Pathways/frontend/package.json
...
"private": true,
"proxy": "http://host.docker.internal:5000/",
...
```

```
#Under the root directory
docker compose up --build
```

## How to deploy (not required for lab3)

Please make sure everything works well before you run it with docker.

+ Make sure the baseURL is set as [URL to your deployed project]
```javascript
#Education_Pathways/frontend/src/api.js
export default axios.create({
   baseURL: "[URL to your deployed project]" -- baseURL for deployment
});
```
+ Re-build the frontend to update the baseURL
```
#Under the frontend/ directory
npm run build
```
+ Deploy your changes to heroku
```
git push heroku main
```