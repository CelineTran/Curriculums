# Guessing Game Lab 

https://docs.google.com/document/d/1h3V2_Zxlzdlb0bGS0cEK15Omt0JSErQksc5fK5hO7dg/edit?usp=sharing

## Key Idea(s): 
	using Math.random(), if-else statements, operators, and slots

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
   
6. Adding “Sample Utterances” with slots.
	Slots are basically a placeholder for difference values. So we want to add one that holds the value of the user’s guess. We do so like this: 
    “My guess is {myNumber}”
    “I guess {myNumber}” 

7. For the slot we just added, we need to give it a type
   Scrolling down, you’ll see the slot we just created
   For slot type, we want to choose “AMAZON.NUMBER” 

8. Click “Save Model” at the top
9. Scroll down to “Endpoint” and select “AWS Lambda ARN” 
10. Switch over to AWS Lambda

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

https://github.com/CelineTran/Curriculums/tree/master/Amazon%20Alexa/NodeJs_Template

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

2. Now we must add an “Attribute” 
   Attributes make a variable within one intent, “global”, allowing the scope of this variable to be extended to the entire      program. This “attribute” will hold the computer’s random number between 1-10. To do so we add this code under our speechOuput. 

   Math.random() creates a number between 0 and 1, so we first need to multiply that by 10 to expand our range to 0-10. We then need to add 1 so that we get ranges 1(inclusive)-11(exclusive) -> [1,11). So finally, we need to turn it into an integer (whole number) by using Math.floor(). 

	this.attributes.computerNumber = Math.floor(Math.random()*10+1); 

3. On line 26, labeled ‘MyFirstIntent” 
   Change that to the custom intent we created (GuessIntent)
   Remove the words inside the double quotes, as we don’t want to output that speech yet.
   
4. Here is where the coding gets more interesting. 
5. Now that Alexa randomly picks her number, we need to retrieve the value that the user chooses by accessing the slot we created in the front end. To do so, we create a variable called ‘userGuess’ to store the slot value. 

		var userGuess = this.event.request.intent.slots.myGuess.value;  

6. Here’s where the coding gets fun! In order for Alexa to check if your guess was correct, we have to use If-Else Statements! If-Else statements are conditional statements that execute specific coding blocks only under certain conditions. These are very helpful when the input/output of our program is dynamic. 

The most crucial part of the If-Else Statements is the condition. In our guessing game, we have to check if the userGuess is equivalent to the computerNumber. To do so, we start with something like this 

	if (userGuess == this.attributes.computerNumber){

	}
	else{

	}


7. Then we want to fill in the if section, separated by the curly braces, with the speechOutput that correlates the condition. So if userGuess is equivalent to computerNumber, then we want Alexa to say something along the lines of “Congrats”. 

8. On the other hand, if they are not equivalent, we want to say something like “Try again”
9. So our final code should look something like this

		'GuessIntent': function(){
			var userGuess = this.event.request.intent.slots.myGuess.value; 
        		var speechOutput; 
       		 	if(userGuess == this.attributes.computerNumber){
            			speechOutput = "You are correct!"; 
        		}
        		else {
            			speechOutput = "Sorry, Try again."; 
       			}
        		var speechReprompt = "";
        		this.response.speak(speechOutput).listen(speechReprompt);
        		this.emit(':responseReady');
		},
	
9. Save and test!


## Testing:

1. In the ADC, click on the “Test” tab
2. Enable testing by switching to “Development” 
3. Enter your invocation name to invoke/open the skill and then try out appropriate utterances 






