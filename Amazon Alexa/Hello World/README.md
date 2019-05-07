# Hello World Lab 

https://docs.google.com/document/d/1FC8oOAS2pC8Hy75Ko0AKefglhapDy1Nei57dbKGsOqo/edit?usp=sharing

## Key Goals
    Achieving simple output, navigating through Amazon Developer Console and AWS Lambda
    
## Setup: 
###	Amazon Developer Console (ADC, Front-End)

1. Create Skill, Skill Name: Hello World
2. Select “custom” as your model
3. Select “Start from Scratch” when prompted to choose a template
4. Click “Invocation” 
    Enter a unique “Skill Invocation Name”
     “hello world celine” 

5. Click “Add” next to “Intents” 
    Add your first custom intent, (call it “GreetingIntent”)
    Click “Create Custom Intent”

6. Adding “Sample Utterances” like
    “Good Morning” 
    “Morning” 
    “Hey” 
    
7. Click “Save Model” at the top
8. Scroll down to “Endpoint” and select “AWS Lambda ARN” 
9. Switch over to AWS Lambda


## Creating a function and connecting “Endpoints”:

1. Find Services: Lambda by searching it
2. Select “Create Function” in the top right
   Select “Use a blueprint” and select “alexa-skill-kit-sdk-factskill”
     Scroll to the bottom and click “Configure” 
     
3. Enter a unique “Function Name” 
   SageHill_CelineT_HelloWorld
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
  https://github.com/CelineTran/Curriculums/AmazonAlexa/NodeJs_Template

## Function Setup: 

1. In AWS, in the designer tab, select the top orange configuration with your function name
2. Scroll down until you see the code 
3. Go to Github Link and open the “template_index.js” file 
   Click “Raw” 
   Select all and copy 

4. Replace the current code by pasting over the copied code  in the AWS
5. Save 

## Writing your own code:  

1. In the code, on line 19 should be the ‘Launch Request’ 
2. Change the Alexa’s speech output on line 20 but editing the text inside the quotation marks
3. On line 24, labeled ‘MyFirstIntent” 
   Change that to the custom intent we created (GreetingIntent)
   And similarly, edit the text within the quotation marks on line 25 
4. Save and test! 

## Testing:

1. In the ADC, click on the “Test” tab
2. Enable testing by switching to “Development” 
3. Enter your invocation name to invoke/open the skill and then try out appropriate utterances 




