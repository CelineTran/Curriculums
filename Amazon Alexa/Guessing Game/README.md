# Guessing Game Lab 

https://docs.google.com/document/d/1h3V2_Zxlzdlb0bGS0cEK15Omt0JSErQksc5fK5hO7dg/edit?usp=sharing

## Key Idea(s): using Math.random(), if-else statements, operators, and slots

## Setup: 
	Amazon Developer Console (ADC, Front-End)

1. Create Skill, Skill Name: Guessing Game
2. Select “custom” as your model
3. Select “Start from Scratch” when prompted to choose a template
4. Click “Invocation” 
   Enter a unique “Skill Invocation Name”
   “guessing game celine” 

5. Click “Add” next to “Intents” 
   Add your first custom intent, (call it “GuessIntent”)
   Click “Create Custom Intent”

6. Adding “Sample Utterances” with slots like
   “My guess is {myNumber}”
   “I guess {myNumber}” 

7. Click “Save Model” at the top
8. Scroll down to “Endpoint” and select “AWS Lambda ARN” 
9. Switch over to AWS Lambda

## Creating a function and connecting “Endpoints”:

1. Find Services: Lambda by searching it
2. Select “Create Function” in the top right
   Select “Use a blueprint” and select “alexa-skill-kit-sdk-factskill”
   Scroll to the bottom and click “Configure” 
   
3. Enter a unique “Function Name” 
   SageHill_CelineT_GuessingGame
   Execution Role: use an existing role 
   Click the arrow next to “Existing Role”
      In the drop-down menu select or find “lambda_basic_execution”
   Scroll to the bottom and click “Create Function” 

4. In the Designer Tab, on the left side, click on “Alexa Skills Kit” 
   A new configuration should appear in the main skeleton
   Making sure the “Alexa Skills Kit” is highlighted in blue, scroll down 

5. “Configure Triggers” 
   Switch back over to the ADC 
   Click “Copy to Clipboard” to copy your Skill ID
   Paste this in the configuration box in the AWS
   Click “Add” at the bottom right
   Scroll back to the top and click “Save” at the top right

6. Above the “Save” button, click the two small square icons to copy the ARN
   Switch over to the ADC
   Paste the ARN in the “Default Region” 
   Click “Save Endpoints”

7. Navigate back to the invocation and select “Build Model”

## Coding (Lambda): 

https://github.com/CelineTran/Genius_Camp_Alexa/tree/master/NodeJs_Template

## Function Setup: 

1. In AWS, in the designer tab, select the top orange configuration with your function name
   Scroll down until you see the code 

2. Go to Github Link and open the “template_index.js” file 
   Click “Raw” 
   Select all and copy 

3. Replace the current code by pasting over the copied code  in the AWS
4. Save

## Writing your Coding: 

1. In the code, on line 19 should be the ‘Launch Request’ 
   Change the Alexa’s speech output on line 20 but editing the text inside the quotation marks
   “Welcome to Celine’s guessing game, I am thinking of a number between 1 and 10. Try guessing what number I’m thinking of”. 

2. On line 24, labeled ‘MyFirstIntent” 
   Change that to the custom intent we created (GuessIntent)
   Remove the words inside the double quotes, as we don’t want to output that speech yet.
   
   ‘GuessIntent’: function () {
        var speechOutput = "";
        var speechReprompt = "";
        this.response.speak(speechOutput).listen(speechReprompt);
        this.emit(':responseReady');
    },

3. Save and test!

## Testing:

1. In the ADC, click on the “Test” tab
2. Enable testing by switching to “Development” 
3. Enter your invocation name to invoke/open the skill and then try out appropriate utterances 






