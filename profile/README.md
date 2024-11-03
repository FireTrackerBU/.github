## Inspiration
The Fire Tracker project was inspired by the need to monitor and model wildfire spread accurately and inform communities about risks. Recognizing that wildfires can spread unpredictably, our project integrates not only fire detection but also predictive modeling for smoke and fire dispersion, visualized through an interactive web application. By integrating machine learning with smoke dispersion models, we aim to create a tool that can aid in both proactive and reactive wildfire management.

## What it does
Fire Tracker combines a detection system with a simulation model that predicts wildfire and smoke spread based on factors like wind speed, wind direction, and smoke source coordinates. The tool:

Detects Wildfire Presence: Identifies if a wildfire is visible in image data.
Simulates Smoke Dispersion: Uses a Gaussian plume dispersion model to estimate smoke spread based on real-time weather data.
Visualizes Wildfire Risk: A Wildfire Risk Map web application allows users to click locations on an interactive Google Map to view simulated wildfire risk in that area.
Generates Dynamic Heatmaps: Displays areas at high risk of wildfire or smoke impact, assisting in decision-making for residents and emergency responders.
## How we built it
Gaussian Plume Dispersion Modeling:
To simulate smoke dispersion, we implemented a Gaussian plume dispersion model that considers factors like wind direction, wind speed, and the source location of the smoke. This mathematical approach is widely used in air pollution modeling and provides a scientific basis for predicting smoke spread over distances.
Google Maps and Heatmap Integration:
Our Wildfire Risk Map frontend uses Google Maps embedded in a React application. We leveraged the @vis.gl/react-google-maps package for easy integration, customizing the map with user interactions.
The heatmap overlay was created using Google Maps Visualization tools, which display the output of the machine learning model and dispersion simulation as an intuitive, color-coded risk map.
Machine Learning Model for Fire Detection:
The core wildfire detection model was built with a Convolutional Neural Network (CNN) in TensorFlow and trained on labeled wildfire images. We applied the model to classify images as “wildfire” or “non-wildfire.”
For smoke and fire spread predictions, the model generates output data in the form of risk probabilities that feed into the heatmap overlay.
Frontend Development in React:
The frontend interface was developed in React and styled with Tailwind CSS for a modern, responsive design.
Users can click on any point on the map to simulate wildfire risk, with options to view specific coordinates and trigger simulations.
We implemented a dynamic InfoWindow that displays location details and includes a button to initiate the simulation.
Backend Simulation Trigger:
Each location selected by the user sends a POST request to a backend endpoint, which triggers the machine learning model.
The simulation results are returned to the frontend, where the HeatMapLayer component visualizes the risk as a heatmap overlay on the map.
Security and Deployment:
Environment variables were used to securely manage the Google Maps API key, ensuring sensitive data remained secure in both local and deployed environments on Vercel.
## Challenges we ran into
Complex Modeling: Developing the Gaussian plume dispersion model required a deep understanding of air pollution science and adapting it to fire spread and smoke.
Real-Time Simulation: Ensuring that simulations based on user interactions in the frontend could trigger and display accurate results in real time was challenging, especially with asynchronous data flow.
Data Processing and Integration: Integrating machine learning results and the simulation model into a dynamic heatmap that could respond to user interactions took careful design of data handling between the backend and frontend.
## Accomplishments that we're proud of
Smoke Dispersion Model: Successfully implementing a Gaussian plume dispersion model for realistic smoke spread simulation based on environmental factors.
Interactive Wildfire Risk Map: Integrating Google Maps and developing an intuitive interface that allows users to interact with risk data visually.
High Detection Accuracy: Achieving high accuracy in identifying wildfire images, with our CNN model performing reliably even in complex scenarios.
Effective Backend-Frontend Communication: Setting up a seamless data flow between the frontend’s map interactions and backend simulations to provide users with a smooth experience.
## What we learned
Gaussian Plume Dispersion Modeling: We gained experience in adapting theoretical models from environmental science to practical applications in predicting wildfire behavior.
Google Maps API and Frontend Integration: Using React and Google Maps helped us understand the complexities of interactive data visualization on the web.
Backend API Design for Simulations: Developing a responsive API for machine learning simulations was valuable, as we learned how to manage asynchronous processes effectively.
Security Best Practices: Configuring environment variables for deployment taught us the importance of secure data management in cloud applications.
## What's next for Fire Tracker
Advanced Spread Simulation: Incorporate more sophisticated models that take into account terrain, vegetation, and local weather conditions for more accurate smoke and fire spread predictions.
Alert System for High-Risk Areas: Add an alert feature to notify users in specific high-risk zones based on simulation results.
Mobile Application: Build a mobile app version of Fire Tracker to make wildfire detection and risk information accessible to more users in real-time.
Improved Visualizations: Explore 3D modeling for the risk map to enhance visualization of smoke plume height and spread.
Enhanced User Feedback: Allow users to report wildfire activity directly through the app, creating a crowdsourced data layer that can improve model predictions.
