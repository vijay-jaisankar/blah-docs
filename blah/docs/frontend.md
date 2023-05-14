# Frontend

The frontend is implemented in React:

---
**Steps to install and run locally**    
- Populate the three text files `username.txt`, `password.txt` and `email.txt` with your docker hub details 
- `npm install`  
- `npm start`  
- Alternatively, you can run `docker run -p 3001:3001 jaggu21/blah-frontend:latest`  
- Kubernetes deployment: `kubectl apply -f blah-frontend.yaml`  
- Ansible Deployment: `ansible-playbook -i inventory ansible-playbook.yml`   
- To run the tests, run `npm test`.  

**Routes**  
1. `/` - Landing Page  
2. `/signup` - To sign a user up  
3. `/home` - Home page of the Application    
4. `/allReviews` - View the latest movies that can be reviewed   
5. `/addReview` - Add a new review of any movie of your choice

All the end points are enabled with Private-Routing(i.e), a user can access the end points only after successful authentication. 
