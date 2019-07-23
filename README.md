# BuildingAlexaSkill
As voice services like Amazon Alexa gain in popularity, consumers are adopting VUIs to play games, get the latest news, and control their growing number of smart home devices.


What’s so appealing about Alexa?
-As voice services like Amazon Alexa gain in popularity, consumers are adopting VUIs to play games, get the latest news, and control their growing number of smart home devices.




Simple Architecture of Alexa Working-
![image](https://user-images.githubusercontent.com/53215589/61700296-54202780-acf1-11e9-8e21-5222f1633f75.png)





Requirements to build a skill->



1.Account on the Alexa developer console.


2.Internet-accessible endpoint for hosting your backend cloud-based service.
Your backend skill code is usually a Lambda function. In this case, you need an account with Amazon Web Services (AWS), in addition to your Alexa developer console account. Alternatively, you can build and host an HTTPS web service. In this case, you will need a cloud hosting provider and a Secure Sockets Layer (SSL) certificate.


3.Development environment appropriate for the programming language you plan to use.
Lambda natively supports Java, Go, PowerShell, Node.js, C#, Python, and Ruby and provides a runtime API, which allows you to use any additional programming languages to author your functions.


4.Publicly accessible website to host any images, audio files, or video files used in your skill.
One possible solution is Amazon Simple Storage Service (Amazon S3). If you do not have files other than a skill icon, you do not need to host any resources.

5.(Optional) Alexa-enabled device for testing.
Skills work with all Alexa-enabled devices, such as the Amazon Echo, Echo Dot, Fire TV Cube, and devices that use the Alexa Voice Service (AVS). If you don't have a device, you can use the Alexa simulator in the developer console. Through the simulator, you can see the display templates for Echo Show and Echo Spot, although the display is not interactive. If your skill includes display and touch interactions, you need an Alexa-enabled device with a screen to test the skill.
