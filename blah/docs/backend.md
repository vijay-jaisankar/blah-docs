# Backend

The backend is split into three services:

---

## Blah controller
This stores and fetches reviews from MongoDB.  
**Steps to install and run locally**    
- `cd blah-controller/`  
- Populate the `.env` file akin to `.env.example`.  
- `npm install`  
- `node index.js`  
- Alternatively, you can run `docker run -p 3000:3000 thehungrypigeon/reviewdetails:latest`  
- Kubernetes deployment: `kubectl -f kubectl apply -f   review-details-deployment.yaml`   
- To run the tests, run `npx mocha test.js`.  

**Routes**  
1. `/` - base route to check if the API is active  
2. `/auth/register` - to sign a user up  
3. `/auth/login` - to log in a user (can generate a JWT token)    
4. `/reviews/fetch` - to fetch reviews pertaining to a particular IMDB ID  
5. `/reviews/new` - to add a review pertaining to a particular IMDB ID  

--- 

## Details controller
This validates and returns movie details.  
**Steps to install and run locally**  
- `cd details-controller`    
- Populate the `.env` file akin to `.env.example`.  
- `pip install -r REQUIREMENTS.txt`  
- `uvicorn main:app --reload`  
- Alternatively, you can run `docker run -p 3000:3000 thehungrypigeon/moviedetails:latest`  
- Kubernetes deployment: `kubectl -f kubectl apply -f movie-details-deployment.yaml`  
- To run the tests, run `pytest` 

**Routes**  
1. `/` - base route to check if the API is active  
2. `/details/{movie_id}` - to get details about a particular IMDB ID  
3. `/valid/{movie_id}` - to check the validity of a particular IMDB ID (uses local file to cache IMDB data dumps)  
4. `/feed` - gets details about a random predefined number of movies/titles (uses local file to cache IMDB data dumps)   
5. `/recent` - gets details about the most recent movies/titles (uses local file to cache IMDB data dumps) 

---

## Sentiment controller
This is an experimental feature that returns the approximate sentiment of a review.  
**Steps to install and run locally**  
- `cd sentiment-controller/`  
- Populate the `.env` file akin to `.env.example`.  
- `npm install`  
- `node index.js`  
- Alternatively, you can run `docker run -p 3000:3000 thehungrypigeon/sentimentdetails:latest`  
- Kubernetes deployment: `kubectl -f kubectl apply -f sentiment-details-deployment.yaml`  
- To run the tests, run `npx mocha test.js --exit`

**Routes**   
1. `/` - base route to check if the API is active  
2. `/sentiment` - returns the sentiment of the given review text


--- 
**Running Ansible Config**
Ansible Deployment: `ansible-playbook -i inventory ansible-playbook.yml`  
