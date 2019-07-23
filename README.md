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


# Alexa

### Prerequisites

- [AWS Account](https://aws.amazon.com/)
- [Create a Developer Portal Account](https://developer.amazon.com/edw/home.html)
- Alexa-enabled device for testing (Optional)
  * Companion App - http://alexa.amazon.com/

## Why Develop for Alexa?

- Millions of devices sold to date (Estimated 11 million)
- Top sellers on Amazon during Christmas 2016
- Companies need developers to build out skills (e.g. Starbucks)

## How Alexa Works

When a user speaks to an Alexa-enabled device, the speech is streamed to the Alexa service in the cloud. Alexa recognizes the speech, determines what the user wants, and then sends a structured request to the particular skill that can fulfill the user’s request. All speech recognition and conversion is handled by Alexa in the cloud.
Every Alexa skill has an interaction model defining the words and phrases users can say to make the skill do what they want. The type of skill you build dictates the interaction model that Alexa uses to communicate with your users.

## Alexa Skills

- [Alexa Skills Kit](https://developer.amazon.com/alexa-skills-kit)

### Skill Types 

- [Custom Skills](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/overviews/understanding-custom-skills)
- [Smart Home Skill API](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/overviews/understanding-the-smart-home-skill-api) - The Smart Home Skill API enables you to create skills to control cloud-connected devices
- [Flash Briefing Skill API](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/understanding-the-flash-briefing-skill-api) - A Flash Briefing Skill provides content for a customer’s Flash Briefing, and so when you create a Flash Briefing skill, you have a chance for your original content to reach customers on a daily basis.

[Understanding the Different Types of Skills](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/understanding-the-different-types-of-skills)

## Custom Skills

1. Define `intents` (Requests the skills can handle)
  - **Look up tide information**
  - **Order a pizza**
  - **Request a taxi**
2. The words users say to make (or invoke) those requests. This is the interaction model, and it provides the `voice user interface` by which users communicate with the skill.
  - **Get high tide for Seattle** (this phrase would be mapped to a TideRequest intent)
  - **Order a large pepperoni pizza** (this phrase would be mapped to an OrderPizza intent)
  - **Order a car** (this phrase would be mapped to an OrderCar intent)
3. The name Alexa uses to identify your skill, called the `invocation name`. Users include this when making a request. For example, the skill for looking up tides could be called “tide pooler”.

> User: get high tide for Seattle from Tide Pooler

- [Understanding Custom Skills](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/overviews/understanding-custom-skills)

### Hosting Custom Skills

* [AWS Lambda](http://aws.amazon.com/lambda/)
* [Custom Web Service](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/developing-an-alexa-skill-as-a-web-service)

## Create a Custom Skill

[Steps to Build a Custom Skill](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/overviews/steps-to-build-a-custom-skill)

### 1. Design a Voice User Interface

- [Defining the Voice User Interface](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/defining-the-voice-interface)
- [Voice Design Best Practices](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/alexa-skills-kit-voice-design-best-practices)
- [Understanding How Users Interact with Skills](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/understanding-how-users-interact-with-skills)

Create your intent schema. This is a JSON structure which declares the set of requests (“intents”) your service can accept and handle.
```js
// IntentSchema.json
{
  "intents": [
    {
      "intent": "HelloWorldIntent"
    },
    {
      "intent": "AMAZON.HelpIntent"
    }
  ]
}
```

Intents can optionally support named parameters with `slots`. Alexa will pass these values to the Lambda function when invoked.

```js
{
  "intents": [
    {
      "intent": "GetHoroscope",
      "slots": [
        {
          "name": "Sign",
          "type": "LIST_OF_SIGNS"
        },
        {
          "name": "Date",
          "type": "AMAZON.DATE"
        }
      ]
    },
    {
      "intent": "GetLuckyNumbers"
    }
  ]
}
```

You can then access `slot` variables like so within Node: 
```
intent.slots.Sign.value
```

[Slot Type Reference](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/built-in-intent-ref/slot-type-reference)

Create a set of sample utterances that map to your intents. These are the phrases users say when interacting with your skill.

```
HelloWorldIntent say hello
HelloWorldIntent say hello world
HelloWorldIntent hello
HelloWorldIntent say hi
HelloWorldIntent say hi world
HelloWorldIntent hi
HelloWorldIntent how are you
```

If you have slots defined, you can create a sample utterance like so:

```
GetHoroscopeIntent what will the horoscope for {Sign} be on {Date}
```

### 2. Set up the Skill

- [Registering and Managing Custom Skills in the Developer Portal](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/registering-and-managing-alexa-skills-in-the-developer-portal)
- [Choose Invocation Name](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/choosing-the-invocation-name-for-an-alexa-skill)

### 3. Write and Test the Code for Your Skill

- [Creating an AWS Lambda Function for a Custom Skill](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/developing-an-alexa-skill-as-a-lambda-function)
- [Fill in Lambda Function endpoints in the Developer Portal](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/registering-and-managing-alexa-skills-in-the-developer-portal)
- [Test your skill with the Service Simulator or an Alexa-enabled device](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/testing-an-alexa-skill)

### 4. Submit the Skill 

- [Submitting the Skill for Certification](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/publishing-an-alexa-skill)

## Code Samples

- [Alexa Skills Kit SDK for Node.js](https://github.com/alexa/alexa-skills-kit-sdk-for-nodejs)
- https://github.com/amzn/alexa-skills-kit-js/tree/master/samples/helloWorld


----------------------------------------------------------------------------------------------------------------------------------------

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

