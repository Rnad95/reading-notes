# Read 31 = Espresso

## Definition

---
AWS Amplify is a service that helps you integrate with other AWS services, but it does so in a very different way.

AWS Amplify is a toolchain that helps you build and deploy entire applications very quickly. When setting up your project, you have a whole bunch of different configurations to choose from as seen in the image below. It is mainly aimed at full stack applications, but can also use it just for its ability to generate a backend.

![image](https://i0.wp.com/www.beabetterdev.com/wp-content/uploads/2021/09/image-27.png?resize=768%2C447&ssl=1)

We primarily use it as a Command Line Interface (CLI) tool, but there is a limited feature Admin UI that allows you to do some admin tasks within the app.

- Now you don't need to know what Amplify is provisioning behind-the-scenes to add these functions.

- Amplify is an Amazon Web Services (AWS) tool that allows developers to develop apps without having to know what AWS services to use. This way, developers can spend more of their time focusing on code rather than fumbling with infrastructure and deployment considerations.

- It uses a relatively old product called AWS Cloud-formation to do the heavy lifting for provisioning those services. Cloud-formation is an Infrastructure as Code service that allows you to define template files that instruct AWS which components you need for your application, and let AWS do the heavy lifting of provisioning those services.

## An Example Of Amplify Features

---

- Below is an image of the wide variety of application integration offers.
- This is a big list of impressive things you can do with Amplify, but behind the scenes there's no mystery ere.
- I've done my best to highlight some of the technologies used behind the scenes.

- Note: Links below are to my YouTube videos on service overviews.

- For raw object storage including asset files for your web applications, or deployment executables, we rely on the popular Amazon S3.For asynchronously communicate with other microservices, aka PubSub, we use a combination of Amazon Simple Notification Service (SNS) and Simple Queue Service (SQS).

- For analytics, we utilize Amazon Pinpoint.
- For domain registration and DNS modifications, we use Amazon Route 53.To build dashboards, examine logs, and add alarms we use Amazon Cloudwatch.
- For Serverless Compute we use AWS Lambda.
- And finally, for DataStores, we generally rely on the popular NoSQL Database Amazon DynamoDB.I'm not going to run through every single service here, but I think you get the idea.  
- Basically, Amplify is an abstraction that sits ontop of other core services, letting you quickly add functions without needing to understand which service is being used behind the scenes.

## Usage

---

How AWS Amplify looks like:

**Command Line Interface (CLI):**

You'll be interacting with Amplify through the command line tool Amplify. Amplify is a library that you can install to your terminal to interact with the library. It will ask you some basic questions about your application configuration including language, framework, name, and other details.

## Looking to get started with Amplify? Check out my Step by Step Tutorial here.

---

**Admin UI:**

It also produces a bunch of application code that you can use to create your own unique user-friendly interfaces for your site's website or mobile app.

It allows you to get a physical view of the components your building through the console.

## Pros and Cons of Amplify

**PRO**
`Pro # 1` – Getting Started Quickly
`Pro # 2` – Fast Development Cycles
`Pro # 3` – Shielding From the Complexity of AWS

**Conns**
`Con # 1` – You Don’t ‘Really’ Learn AWS;
`Con # 2` – Collaboration Can Be Frustrating
`Con # 3` – Stepping Outside The Box
`Con #4` – Potential For Surprise Bills

### Using AWS Lambda as Mobile Application Backend

![](https://i.pinimg.com/736x/e3/35/28/e33528e1b63f0d7c6f505df3d33d0b31--mobile-applications-on-demand.jpg)