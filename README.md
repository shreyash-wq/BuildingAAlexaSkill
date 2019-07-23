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




# Build An Alexa-Hosted Fact Skill
<img src="https://m.media-amazon.com/images/G/01/mobile-apps/dex/alexa/alexa-skills-kit/tutorials/quiz-game/header._TTH_.png" />


With an Alexa-hosted skill, you can build, edit, and publish a skill without leaving the developer console.
The skill includes a code editor for managing and deploying the backend code for your skill.
For details on what the Alexa-Hosted skills service provides, open [this page](https://developer.amazon.com/docs/hosted-skills/build-a-skill-end-to-end-using-an-alexa-hosted-skill.html) in a new tab.

### Steps
1.  **Go to the [Amazon Developer Portal](http://developer.amazon.com/alexa?&sc_category=Owned&sc_channel=RD&sc_campaign=Evangelism2018&sc_publisher=github&sc_content=Survey&sc_detail=fact-nodejs-V2_GUI-1&sc_funnel=Convert&sc_country=WW&sc_medium=Owned_RD_Evangelism2018_github_Survey_fact-nodejs-V2_GUI-1_Convert_WW_beginnersdevs&sc_segment=beginnersdevs).  In the top-right corner of the screen, click the "Sign In" button.**
(If you don't already have an account, you will be able to create a new one for free.)

2.  Once you have signed in, move your mouse over the **Your Alexa Consoles** text at the top of the screen and Select the **Skills** Link.

3.  From the **Alexa Skills Console** select the **Create Skill** button near the top-right of the list of your Alexa Skills.

4. Give your new skill a **Name**. This is the name that will be shown in the Alexa Skills Store, and the name your users will refer to. Also change the locale if so desired.

5. Keep the default **Custom** model selected, and scroll the page down.

6. Choose **Alexa-Hosted** for the method to host your skill's backend resources.  Scroll backup and select the **Create Skill** button at the top right.
It will take a minute to create your Alexa hosted skill, then you will be taken to the Build tab of the console.


7. **Build the Interaction Model for your skill**
	1. On the left hand navigation panel, select the **JSON Editor** tab under **Interaction Model**. In the textfield provided, replace any existing code with the code provided in the [Interaction Model](../models) (make sure to pick the model that matches your skill's language).  Click **Save Model**.
    2. If you want to change the skill invocation name, select the **Invocation** tab. Enter a **Skill Invocation Name**. This is the name that your users will need to say to start your skill.
    3. Click "Build Model".

	**Note:** You should notice that **Intents** and **Slot Types** will auto populate based on the JSON Interaction Model that you have now applied to your skill. Feel free to explore the changes here, to learn about **Intents**, **Slots**, and **Utterances** open our [technical documentation in a new tab](https://developer.amazon.com/docs/custom-skills/create-intents-utterances-and-slots.html?&sc_category=Owned&sc_channel=RD&sc_campaign=Evangelism2018&sc_publisher=github&sc_content=Survey&sc_detail=fact-nodejs-V2_GUI-1&sc_funnel=Convert&sc_country=WW&sc_medium=Owned_RD_Evangelism2018_github_Survey_fact-nodejs-V2_GUI-1_Convert_WW_beginnersdevs&sc_segment=beginnersdevs).

8. **Optional:** Select an intent by expanding the **Intents** from the left side navigation panel. Add some more sample utterances for your newly generated intents. Think of all the different ways that a user could request to make a specific intent happen. A few examples are provided. Be sure to click **Save Model** and **Build Model** after you're done making changes here.

9. If your interaction model builds successfully, proceed to the next step. If not, you should see an error.
Try to resolve the errors. In our next step of this guide, we will be creating our code.


     If you get an error from your interaction model, check through this list:

     *  **Did you copy & paste the provided code correctly?**
     *  **Did you accidentally add any characters to the Interaction Model or Sample Utterances?**

