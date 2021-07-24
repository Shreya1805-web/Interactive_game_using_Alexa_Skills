# <b>Interactive game using Alexa Skills</b>

I made an interactive game using Alexa Skills Kit during my summer internship at VoiceQube, Bangalore, India.<br/>
It's called "Starting up in Silicon Valley" and it's a part of the "Your adventures with Cole and Haku" series.
The game is currently in the production phase and will be out in the Alexa Skills store very soon.
Now we'll look into the details of this project.

## <b>What is Alexa Skills Kit?</b>
The Alexa Skills Kit (ASK) is a software development framework that enables you to create content, called skills. Skills are like apps for Alexa. With an interactive voice interface, Alexa gives users a hands-free way to interact with your skill. Users can use their voice to perform everyday tasks like checking the news, listening to music, or playing a game. Users can also use their voice to control cloud-connected devices. For example, users can ask Alexa to turn on lights or change the thermostat. Skills are available on Alexa-enabled devices, such as Amazon Echo and Amazon Fire TV, and on Alexa-enabled devices built by other manufacturers.

### <b>How Does an Alexa Skill Work?</b>
<div align="center">
<img src ="https://github.com/Shreya1805-web/Interactive_game_using_Alexa_Skills/blob/main/img1.png">
</div>
An Alexa skill has both an interaction model—or voice user interface—and application logic. When a customer speaks, Alexa processes the speech in the context of your interaction model to determine the customer request. Alexa then sends the request to your skill application logic, which acts on it. You provide your application logic as a back-end cloud service hosted by Alexa, AWS, or another server.

### <b>Functional Architecture</b>
<div align="center">
<img src ="https://github.com/Shreya1805-web/Interactive_game_using_Alexa_Skills/blob/main/img2.jfif" width ="700px">
</div>
An Alexa skill is a small application that interacts with Alexa via an AWS Lambda function.

### <b>Skill development workflow</b>
<div align="center">
<img src ="https://github.com/Shreya1805-web/Interactive_game_using_Alexa_Skills/blob/main/img3.png">
</div>
Steps:
1. Create and Configure Skill 
2. Create Interaction Model
3. Coding the Backend system
4. Deploying the Backend system
5. Testing the Skill
6. Publishing the Skill

### <b>Alexa Skills Framework</b>
The Alexa Skills framework involves the following principal components -
1)	Alexa Enabled device
2) 	Alexa Voice Service(AVS) 
3) 	Alexa Skills Kit (ASK)

Alexa Enabled Device is the point of interaction with the user, it has the responsibility of wake word detection, which in this case is “Alexa” and to identify the and relay of user Utterances followed by a wake word to the Alexa Voice Service.
The Alexa Voice Service is the processing center of all the User commands (Utterances) and is tasked with carrying out the following functions-

1) Speech Recognition
2) Natural Language Understanding
3) Text to speech conversion ( for the output to the user)

The Alexa Voice Service(AVS) is where the user’s input is processed and is converted into logical predicates. This logical interpretation of the user’s input is then sent to the specific skill with which it is concerned for processing it with the program logic. This Programming logic is based on the Alexa Skills Kit (ASK) and is similar in function to what a Backend does in a typical web application scenario.

The output as determined by the Skill’s programming logic is sent back to the Alexa Voice Service (AVS) for its text to speech conversion. The Speech is sent back to the Alexa Device in direct interaction with the user in the form of SSML ( Speech Synthesis Markup Language) for it to give output to the user. A combination of Voice output and graphical output based on Informative cards is also possible.

### <b>Structure of An Utterance</b>
There are a few basic components of a User Utterance (Input to the Alexa Device).

Alexa requires a word, often called a Wake phrase which would alert the device that they can expect a command immediately after.The Default wake phrase is ALEXA. It can also be Amazon, Echo,Computer.

Launch Phrase is the word that tells Alexa to trigger a skill. Examples of Launch phrases are “ OPEN”, “ASK” , “START”, “LAUNCH”.

Invocation name is the name of the skill.

Intents are the goals that the user is trying to achieve by invoking the skill.

Utterance tells Alexa what the skill should do. Apart from Static utterances such as Start and Launch, dynamic commands can be added. These Dynamic commands are called slots.
Each intent can contain one or more slots. A Slot is the variable that is parsed and exposed to the application code.
<div align="center">
<img src ="https://github.com/Shreya1805-web/Interactive_game_using_Alexa_Skills/blob/main/img4.jpg" width ="700px">
</div>
There are a few basic intents that are necessary for all Alexa Skills to have, these are -

- Cancel_Intent = Functionality to cancel current command
- Help_intent = Standard Help feature for Alexa Skills
- Stop_intent = Functionality to stop the skill
- Repeat_intent = Repeat prompt functionality

## <b>Development Process</b>
Interaction Model Design
The interaction model forms what is a front-end parallel for an Alexa Skill, All possible spoken input by users is mapped onto a set of intents that concern the skill under development, and are handled at the backend.Every Alexa skill has a voice interaction model that defines the words and phrases users can say to make the skill do what they want. This model determines how users communicate with and control your skill.The intents can be mass edited into the Alexa Developer Console in the form of a JSON structure called the “Intent Schema”.Once a intent is created, the slot types that can be used in it are specified, Amazon provides a large variety of built-in slot types for different datasets e.g. AMAZON.Date, AMAZON.time.Once slots have been specified the sample utterances the intents are added.

 For intents that need multiple slots and detailed information, it becomes difficult to provide the entire set of information by the user in one go.For such cases Alexa allows us to create a Dialog Model, in form of multiple turns of questions and answers.The conversation is tied to a specific intent representing the user's overall request. The questions and answers are intended to gather, validate, and confirm slot values. The conversation continues until all slots needed for the intent are filled and confirmed according to the rules defined in the dialog model.
 
Limits to the interaction models components - 
- Maximum number of intents in a skill - 250
- Maximum number of slot types and intents combined  - 350
- Maximum no of characters in a given slot value - 140
<div align="center">
<img src ="https://github.com/Shreya1805-web/Interactive_game_using_Alexa_Skills/blob/main/interaction%20model.png" width="900px">
</div>

### <b>Backend Design</b>
We are using NodeJS for programming the backend to the story. The backend consists of a request handler, which when passed a request tries to match it with different intents that have been programmed. In case that the request type matches with an intent its Handler function is fired and the necessary response takes place.
Any smart device running alexa has to stream the voice input which follows the Wake word to the ALEXA SERVICES on cloud where the NLP engine parses the input, recognises the demand made by the user and delegates the request to the required skill. 

Alexa communicates with the required skill by using a request-response mechanism over the HTTPS interface. When a user invokes an Alexa skill, the said skill receives a POST request containing a JSON body. The request body contains the parameters necessary for the skill to understand the request, perform its logic, and then generate a response.
The Skill code can run on any cloud platform, but Amazon provides 2 very convenient ways to host a skill -

1. Alexa Hosted Skills
2. Custom AWS Lambda hosted skill

<div align="center">
<img src ="https://github.com/Shreya1805-web/Interactive_game_using_Alexa_Skills/blob/main/backend.png" width ="900px">
</div>

#### <b>Alexa Hosted Skills</b>
Provides a quick and easy to go provisioning of compute resources by Alexa itself on amazon's cloud services infrastructure.The following resources are provisioned for the skill on AWS platform -
1. AWS Lambda endpoints
2. S3 Bucket for media storage
3. Amazon DynamoDB instance for persisting data
4. AWS CodeCommit Repository

The resource usage for skills developed in Alexa Hosted mode have some resource usage restrictions, like 1 million free AWS Lambda requests and 3.2 million seconds of compute time per month.5 GB of Amazon S3 storage, 20,000 get requests, 2,000 put requests, and 15 GB of data transfer out per month.25 GB of Amazon DynamoDB storage, and 1 GB of data transfer out per month.It is due to these restrictions the company decided to use custom provisioned AWS resources in form of AWS Lambda.

#### <b>Hosting skills on AWS Lambda Function</b>
AWS Lambda is a cloud services offering that runs your code only when it's needed and scales automatically,meaning that  there is no need to provision or continuously run servers. The code for an Alexa skill is uploaded to a Lambda function and Lambda does the rest, executing it in response to Alexa voice interactions and automatically managing the compute resources for you.

### <b>How Does the Backend Work?</b>
Interaction between the Alexa Services and the Skill backend code hosted in AWS Lambda essentially depends on the request handling functionality provided by ASK SDK. The first step to this is verification of a request received by the Lambda function. This is necessary to ensure that no malicious skill is configured with your AWS Lambda endpoint making it able to make requests to your skill.The skill genuineness evaluation is done through use of unique SKILL IDs as a part of actual request which are then compared against the actual ID to guarantee genuineness.The AWS Lambda can be configured with a given Skill ID to eliminate the need for Skill ID checking.

A request can be of two types - 
- Intent Request - A request warranting some skill intent specific response
- Event notification request - A request generated by Alexa itself reporting status of different processes. E.g. Audio Playback Started
- All requests contain a request object which tells about the action being invoked by the user and the necessary information such as the timestamp of the request etc.

Most Common request Types and their use cases - 
- LaunchRequest : Sent when the user invokes the skill but does not provide a specific command
- IntentRequest : Sent when the user speaks a command that maps to one of your intents. The request includes the name of the intent.

The specific action required by the user is captured in the Intent object which is a part of the request 
SessionEndedRequest : Sent when the skill's currently open session is closed because the user exited the skill, the user provided a response your skill can't understand, or an error occurs.

#### <b>What are request handlers?</b>
<div align="center">
<img src ="https://github.com/Shreya1805-web/Interactive_game_using_Alexa_Skills/blob/main/Screenshot%20(168).png" width ="700px">
</div>

The code responsible for handling a given request and generating the skill’s response for a request is made by implementing the RequestHandler Interface. A skill contains a variety of Request Handlers, these identify which requests they can handle by using the CanHandle function to which a HandlerInput object is passed.The function checks the HandlerInput object for the Request Type, IntentRequest, Slot Values etc to decide whether it handles an Request or not. A request handler can handle multiple intents, all that has to be made sure is that all the intents described in the interaction model are handled.

Once a request handler is decided upon, the Handle function encapsulates the necessary logic for catering to the request and returns a response.

Handling a request in a Handle function often requires the program to make use of the slot values as specified in the interaction model, the slot values are present in a request as part of a slots member which is a key-value map with slot names and values.

The Final stage of handling a request in a Handler function is to generate and return a response. This is typically achieved in form of a card returned to the smart device along with a string which is spoken.The response is generated by using speak() and withSimpleCard methods on the responseBuilder object which is a part of the handlerInput object, the speech can be customised with the required effects using SSML (Speech Synthesis Markup Language), our project aims to use Voice-Actors to generate the necessary audio clips and store them in S3 bucket for building response to intents therefore the SSML is not necessary.
