---
title : "Web Frontend"
date : 2026-07-27
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

In real-world medical systems, doctors and healthcare staff don't interact directly with command lines or APIs. They need an intuitive, friendly interface to upload images and view results. That's why we need to connect the API we just created to a Web Frontend application.

### 1. The Diagnostic Web App
In this project, the user interface is built lightweight in Python via the `app.py` source file. This application provides a web page that lets you:
*   Upload a patient's X-ray or CT image.
*   Send the image data through API Gateway to the SageMaker Endpoint for processing.
*   Receive the AI's result and visually display the lung condition assessment on screen.

### 2. Running the Application from AWS CloudShell
To launch the web interface, we'll run the `app.py` file. Depending on which UI library is used (such as Streamlit or Gradio), the system will spin up a local web server.

Go back to the **AWS CloudShell** terminal and run the command to start the application:

```bash
streamlit run app.py    
```

After running the command, you'll see a URL printed in the terminal. This is the link to access the AI diagnostic web interface.

![Streamlit URL](/images/5-Workshop/5.7-Frontend/url-streamlit.png)

### 3. Trying Out the Diagnosis Feature
Once the application is running, you can open the provided web link and the AI diagnostic interface will appear.

Steps to try it out:

* Prepare a sample X-ray image (for example, download the file NORMAL2-IM-1252-0001.jpeg or NORMAL2-IM-1116-0001-0002.jpeg from the toy_data/NORMAL/ folder to your personal computer).

* Click the Upload Image button on the web interface and select the image you just downloaded.

* Click the Diagnose Now (Serverless) button to have the system send the image through the API.

* Wait a moment, and the prediction result (for example: "Normal" or "Signs of pneumonia") along with the confidence score will be displayed right on the screen.

![Diagnosis screen](/images/5-Workshop/5.7-Frontend/web1.png)
![Sending a request to the AWS Serverless API](/images/5-Workshop/5.7-Frontend/web2.png)
![Displaying the prediction result](/images/5-Workshop/5.7-Frontend/web3.png)

*With that, we've completed the entire process of building the AI Pulmonary Diagnostic Suite system, from data preprocessing, to model training, to forming a complete Web App product that can be used interactively in the real world!*

**Thank you all for joining the workshop, and best of luck deploying your own AI projects!**