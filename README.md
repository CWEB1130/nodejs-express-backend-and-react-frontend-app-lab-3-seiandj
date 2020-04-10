# nodejs-express-backend-and-react-frontend-app-lab-3-seiandj
nodejs-express-backend-and-react-frontend-app-lab-3-seiandj created by GitHub Classroom
 (Links to an external site.)Step 1 - Create a web project and implement version control
Create a folder titled [cweb1130_lab3]
Make sure you are in the newly created directory and install git by running command [git init]
Run the command [git pull origin lab3] to pull down the README.md file that contain instructions
 (Links to an external site.)Step 2 - Configure and install Express
Run command [npx express-generator backend]
This command scaffolds the application into a folder called backend.

Change directories into backend folder

Install dependencies listed in package.json by running command [npm install]

Fix any dependencies by running command [npm audit fix]

Run command [npm start] and view application in browser by navigating to localhost:3000.
After viewing application in browser stop application by running [Control + C]
 (Links to an external site.)Step 3 - Alter Route and Data source
This step is going to include a route that responds back with offers

Data Source - Navigate to lab3_resources repository (Links to an external site.) and add the offers.json file into the backend folder.

Navigate to the route folder and open the users.js

Include the statement below that makes the offers.json file available within the the users.js file.
  var offers = require('../offers.json');
Within the router.get(), alter the res.render() method to the statement below.
   res.json(offers)
Within the terminal, run the command below to change the PORT and start the server. After running the command below, enter the url to

   PORT=8080 npm start
Once the server is started, navigate to URL path that will trigger the users.js route to display the offers json data. If you can see the offers.json data once you go to the route, your route is properly configured to send json data.

After viewing the route that displays the offer json data, stop application by running [Control + C]

 (Links to an external site.)Step 4 - Create a React Front-end Framework
Change directories back into the [cweb1130_lab3] root folder.

Install React - Run the two commands below

   npm install -g create-react-app
   create-react-app frontend
Change directories into the frontend folder and open the package.json file and include the following line after the scripts object. The line below adds a proxy key that tells react app to proxy api request to express server.

"proxy": "http://localhost:8080",
 (Links to an external site.)Step 5 - Alter the App Component to receive JSON data
Within the frontend folder, Navigate to the src folder and create a new file titled [Offers.js] and paste the following code below:

import React, { Component } from 'react';


class Offers extends Component {

  state = { offers: [] }
  

  componentDidMount(){
	fetch('/offers')
	  .then(res => res.json())
	  .then(offers => this.setState( { offers }));
  }

  render(){
	return (
	  <div>
		{this.state.offers.map(aoffer =>
		<section className="aoffer" key={aoffer.id} >
		  <h5>{aoffer.property}</h5>
		  <h5>{aoffer.offer_exp}</h5>
		  <h6>Offer Details</h6>
		  <p>{aoffer.offer_details}</p>
		</section>
		)}
	  </div>
	);
  }
}

export default Offers;
Navigate to the [index.js] file within the src folder and include the Offers.js component by placing the statement below at the top of the document:

import Offers from './Offers';
Staying within the [index.js] file replace the contents of the ReactDOM.render() with the following:

  <React.StrictMode>
      <Offers />
    </React.StrictMode>,
    document.getElementById('offers')
 (Links to an external site.)Step 6 - Adding the default HTML/CSS and static resources
Within the frontend folder, replace the contents of the public folder with the public folder found at lab3_resources repository (Links to an external site.)
 (Links to an external site.)Step 7 - End-user Interaction
Navigate to the backend folder and start the server by running command [PORT=8080 npm start]. Your server should start up with no problems
While the server for you backend is started, create a new bash terminal within visual studio code by clicking the plus sign. [Please email instructor or watch lecture if you are unable to find]
With the new bash terminal open, change directories into the frontend folder and start the server by running command [npm start]
If all the steps were properly completed, your app should render and display in the browser. The offers component should display offers data from the offers.json file that is in your backend folder.
 (Links to an external site.)STEP 8 - Extra Credit (3 Points)
Create new functionality that would populate suggested properties component. You will need to alter the the route within the backend folder, add a new data source and create a new component within the frontend src folder.
 (Links to an external site.)STEP 9 - Github Repository
Add Instructor as a contributor to repository by searching for [instructorc]
Adjust README.md file at the end to include date of completion and course information.
 (Links to an external site.)STEP 10 - Submission
Comment your name to the app.js file within the backend folder.
Make sure your master branch is clean and push up your final changes.
In Canvas, submit the URL to your repository
