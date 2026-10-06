**Community:** I chose my friends, family, and extended community as the community. This is a good fit for the classification task because there is a nuanced but still obvious difference in the way different types of people communicate with me via text.

 ### Labels:

**OldHead:** A text from an older person. My mom, aunts and uncles, teachers, older mentors etc. You can normally tell by the grammar they use, what type of (if any) emojis, and the subject matter.

  Example 1: Hi Selma, thank you my precious niece. 🤗😘♥️
  
  Example 2: Yes, it is. You can delete it from your phone
  
**Youngin:** A text from one of my peers. My friends, close-in age cousins, classmates, etc. You can tell by the grammar they use as well, how many abbreviations are in the text, the subject matter, and in what context different emojis are used.
 
  Example 1: i like dat
  
  Example 2: u right

**Hard edge cases:** 
  - Messages from millinneals (those in the middle of the two labels) are extremely nuanced and can sometimes different messages from the same millinneal can fit into different categories. I will use messages from millinneals to further define the two categories. Though a message may be from a middle-range-aged person, it may have the vibe of one of the two categories and help deepen the understanding of that category.
  - Shorter text messages can cause confusion. The key marker in the difference will be the use (or lack there of) of punctuation. 


**Data collection plan:** I will collect data from my own text messages. There is a possibility for there to be more texts from the Youngin category, since younger people tend to communicate via text more than older people. I will remedy this with the millinaeal filler texts.

**Evaluation metrics:** The metrics I will use are: 
        -  Per-class precision, recall, and F1:
            - This will show if the model  tends to get one label correct more often than the other.
        -  Macro-F1:
            - This is the average of the F1 scores of both classes, and will give an overall view.
        - Confusion matrix:
            - This will show which directions the errors trend: False OldHead or False Youngin 

            
**Definition of success:** This classification is not very useful outside of the scope of the project, since most people will see the contact name when receiving a text, therefore knowing the classification already themselves. It is more fun and experimental, and the type of project that first drew me to computer science when I was younger, before college. However, if someone were to have lost all their contacts and needed to figure out who a text was from without asking the person (due to embarrassment, not wanting to offend the person, etc), the classification could help narrow down the list of people the text could be from. Success in the context of the project would be if the model yields around 85% accuracy for each metric, and if the confusion matrix tends towards False OldHead, which is what I suspect to happen.


**AI Tool Plan:** 
  - Support With Understanding: Some of the Machine Learning concepts take a bit longer for me to grasp, so I will use Claude to assist in gaining a deeper understanding of these concepts. Gaining a deeper understanding of these concepts will also support me in planning (for example with the evaluation metrics).
  - Label Stress Testing: I gave Claude my label definitions and examples, as well as my edge case explanations, and asked it to generate 5 edge case examples.
    - Output from Claude:
      Here are 5 messages that sit between OldHead and Youngin. For each one I've noted which way it leans and why, since your plan is to use these to sharpen the category definitions.

        1. "Sounds good! See you at 7 😊"
        Leans OldHead. Full punctuation, complete sentences, a standard smiley. A younger person would more likely write "sounds good see u at 7." But it's friendly and fast, so it            isn't a strong OldHead.
        
        2. "lol yeah I'm running late, be there in 10"
        Leans Youngin. Lowercase "lol" and no ending period give it the peer vibe, but the full "I'm" and the tidy comma keep it from being a clear Youngin. Typical millennial text.
        
        3. "Ok."
        Genuinely ambiguous. This is your short-text problem in its purest form. The capital O and the period make it read as OldHead, or as passive-aggressive Youngin (the period-as-          tone use). Only context or the sender can break the tie.
        
        4. "ok"
        Leans Youngin. Same word as #3, but with no capital and no punctuation. This pair isolates punctuation as the marker, which is the signal you described.
        
        5. "Haha that's so true 😂 I can't believe he said that!!"
        Leans Youngin, but only slightly. The 😂 and "Haha" are casual, but the correct grammar, apostrophes, and double exclamation points are millennial-typical. An OldHead would             more likely use "Ha ha" or "LOL" with a different emoji, like 😄 or 🤣.

  - Annotation Assistance: To ensure the most accurate data, I will label every message myself. This is not as tedious of a task as it would be for a different type of data, because I don't have to make a decision for most of the text messages (besides the millennial edge cases). I know who the text is from, and I know what category they fit into.
  - Failure/General Analysis: I will give Claude the evaluation from testing, and ask it to do the numerical calculations for the metrics I am recording.

 
