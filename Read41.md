# Read41 - Intent filter LOL

## Introduction

---
Amazon Pinpoint is a flexible and scalable outbound and inbound marketing communications service. Amazon Pinpoint is easy to set up, easy to use, and is flexible for all marketing communication scenarios. Segment your campaign audience for the right customer and personalize your messages with the right content.

## How it works

---
![](https://d1.awsstatic.com/product-marketing/Pinpoint/Product-page-diagram_Amazon-Pinpoint-with-Journeys-%402x.59f755aedb4ea26ddbdeade13529046129c3d7a1.png)

## Benefits

---

### Get started quickly

    Whether you are a marketer or a developer, Amazon Pinpoint is flexible for marketing, bulk, or transactional communications use cases. Developers can leverage the Amazon Pinpoint APIs for message sending, scheduling campaigns, or tracking web and mobile activities. Marketers can design, orchestrate, and run campaigns visually through the console.

### Segment and personalize for impact

    Segment your audience for the right group of customers based on existing customer lists, attributes or use Amazon Pinpoint to create segments from mobile and web application data. Personalize the right message content to engage and delight your customers using both static and dynamic attributes.

### Measure your efficiency

    From message delivery results to campaign data like opens and clicks, use metrics to understand the success of your communications. View the campaign metrics natively in the Amazon Pinpoint reports or stream data to nearly any destination.

### Scale securely with the experts

    Amazon has relationships with the top email providers, telecoms, and spam advisories to ensure the highest customer delivery rates.

## How it works

---

![](https://d1.awsstatic.com/product-marketing/Pinpoint/Product-page-diagram_Amazon-Pinpoint-with-Journeys-%402x.59f755aedb4ea26ddbdeade13529046129c3d7a1.png)

## Use cases

---
**Marketing messages**
Promote your products and services with basic templates or highly-personalized messages, including special offers, newsletters, and other engaging content.

**Transactional messages**
Send immediate, trigger-based customer communications across channels directly from your application, such as purchase confirmations, one-time passwords, or shipping notifications.

**Bulk communications**
Send messages to communities of millions, including notifications and announcements. You can use Amazon Pinpoint to create targeted groups of customers, and then send them campaign-based messages.

## What Is Amazon Polly?

---
Additionally, Amazon Polly includes a number of Neural Text-to-Speech (NTTS) voices, delivering ground-breaking improvements in speech quality through a new machine learning approach, thereby offering to customers the most natural and human-like text-to-speech voices possible. Amazon Polly supports multiple languages and includes a variety of lifelike voices, so you can build speech-enabled applications that work in multiple locations and use the ideal voice for your customers.

Common use cases for Amazon Polly include, but are not limited to, mobile applications such as newsreaders, games, eLearning platforms, accessibility applications for visually impaired people, and the rapidly growing segment of Internet of Things (IoT).

Amazon Polly is a cloud service that converts text into lifelike speech. Neural TTS technology also supports a Newscaster speaking style that is tailored to news narration use cases. You can use Amazon Polly to develop applications that increase engagement and accessibility.

### Some of the benefits of using Amazon Polly include

1. High quality  
2. Low latency  
3. Support for a large portfolio of languages and voices  
4. Cost-effective  
5. Cloud-based solution

## Getting Started (AWS CLI)

---

### Step 3.1: Set Up the AWS Command Line Interface (AWS CLI)

1. Download and configure the AWS CLI.  
2. Add a named profile for the administrator user in the AWS CLI config file. You use this profile when running the AWS CLI commands.

> [profile adminuser]  
> aws_access_key_id = adminuser access key ID
    aws_secret_access_key = adminuser secret access key
    region = aws-region

3. Verify the setup by typing the following help command at the command prompt.

> aws help

**To enable Amazon Polly in the AWS CLI (optional)**

1. Verify the availability of Amazon Polly by typing the following help command at the AWS CLI command prompt.

> aws polly help

2. Use to enable Amazon Polly neither `Uninstall and reinstall the AWS CLI.` or Download the file service-2.json.

3. Reverify the availability of Amazon Polly.

> aws polly help

### Step 3.2: Getting Started Exercise Using the AWS CLI

Now you can test the speech synthesis offered by Amazon Polly. You can save the resulting audio as a file and verify its content.

1. Run the synthesize-speech AWS CLI command to synthesize sample text to an audio file (hello.mp3).

> aws polly synthesize-speech \
    --output-format mp3 \
    --voice-id Joanna \
    --text 'Hello, my name is Joanna. I learned about the W3C on 10/3 of last year.' \
    hello.mp3

In addition to the MP3 file, the operation sends the following output to the console.

    {
        "ContentType": "audio/mpeg", 
        "RequestCharacters": "71"
    }

2. Play the resulting hello.mp3 file to verify the synthesized speech.

3. Get the list of available voices by using the DescribeVoices operation. Run the following describe-voices AWS CLI command.

> aws polly describe-voices

Optionally, you can specify the language code to find the available voices for a specific language. Amazon Polly supports dozens of voices. The following example lists all the voices for Brazilian Portuguese.

> aws polly describe-voices \
  --language-code pt-BR

