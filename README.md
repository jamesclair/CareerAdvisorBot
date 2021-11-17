# c951careeradvisorbot

## A. Explain the functionalities of the chatbot and how they will meet the needs described in the scenario.

The c951careeradvisorbot is an AIML chatbot designed to help computer science students identify and recommend a job type or career specialization based on a short survey.  The bot will interact with the student asking him/her questions.  Once all questions have been answered the bot will evaluate the student's strengths and preferences and provide a personalized job type recommendation.

## B. Identify five computing job types that your chatbot can recommend based on student interaction with the chatbot.

The following five initial career paths are supported:
1. Platform Engineer
2. Frontend Engineer
3. Backend Engineer
4. Network Engineer
5. Machine Learning Engineer

## C. Provide the generated chatbot code files to support the five identified job types from part B.

The files for this project are stored on [pandorabots](https://home.pandorabots.com/dash/bot-directory) and published in [this repo](https://github.com/polarclair/c951careeradvisorbot).

## D. Explain how the chatbot training cases were selected and how you used artificial intelligence markup language (AIML) to enhance the functionality of the chatbot. Provide examples of the chatbot’s functionality that represent the selected cases at the end of the training process in support of your explanation.

The training cases are the multiple choice options the user can select from in each survey question.  Each option maps to a job type.  I chose to store these as AIML maps that way each training case was could be accessed uniformly, easily and repetitively.  It would also make it easier for adding new training cases:  Add the new `[Key, Value]` to each map and add new associated `<button>` and `<category>` for each survey question, no need to edit any existing code.  There are three maps:

[q1.map](maps/q1.map)
[q2.map](maps/q2.map)
[result.map](maps/result.map)

In addition to training cases that help determine the resulting job recommendation the `result.map` is used to capture what the message will be to the user once a decision has been made.

The main AIML logic can be found in [careeradvisor.aiml](files/careeradvisor.aiml).

The training cases were arbitrarily selected to determine "A" recommendation and are NOT indicative of the best and or right recommendations.  The logic could be easily extended for the bot to `<learn>` the categories based on user responses.

The job type mapped to the users selected option is saved as a predicate `a1` and `a2` allowing the chatbot to examine whether these values are matched and remember the users previously denoted preference.  Additionally if `a1` and `a2` do NOT match, the `tiebreaker1` and `tiebreaker2` predicates store the concatenated options from question one and question two based on the user's responses.  The two tiebreaker options are presented to the user assuming the job type indicated by question one and two do NOT match. 

## E. Create an installation manual for the chatbot that includes the web link to access the live chatbot in the Pandorabot platform.

- Navigate to [Pandorabots Directory](https://home.pandorabots.com/dash/bot-directory).
- Search for `Career Advisor Bot 846292`.
- Select `Career Advisor Bot 846292`, which should be the first option in the list (top left).
- Click on the orange Pandorabot chat widget icon (lower right) to access the bot.
- Enter any word to start interacting.


## F. Assess the strengths and weaknesses of the chatbot development environment and explain how they supported or impeded the construction of the chatbot.

The pandorabot environment makes it easy to get started with AIML and developing chat bots.  There is lot's of freely available documentation and resources to help aid a first time AIML developer like myself.  The simple interface with common, ready to use code snippets made coding in XML a little less painful than with a text editor.  And being able to save, run, test, and refresh the predicates in the same window made testing loop super quick and useful for iterative development.  

Unfortunately, as with any sandboxed development environment there are some opinions baked in and missing features that many seasoned developers will miss.  For example, the editor's ability to catch XML syntax errors wasn't always very thourough.  An extra `>>` on the end of an XML tag will result in a bug in your chatbot rather than found by your linter.  No intellisense to give you contextual help means you need to be better at searching out the solution you need.  Any programming language extensions that can help AIML with things like looping or nested data structures isn't available.  Unless you pay for an account you can't link directly to your bot once it is published to the pandorabot directory.  And last but not least, while there is integration with GH, if I were to push a new copy of my code to this repo, it will remove any files that do NOT exist in pandorabot.  Meaning this README will get erased and have to be recovered from a previous commit.

## G. Explain how the chatbot will be monitored and maintained to improve the final user experience.

Now that the chatbot is published on Pandorabot directory the logs for anyone who uses the bot will be available.  The logs and feedback gathered from them can be used to improve the questions, training cases and results.  Once the changes to the bot have been made a new version can be published to the directory.

## H. Provide a Panopto video recording that includes a verbal summary of the capabilities of your chatbot and an example of human interaction with the chatbot in which it provides meaningful career advice.


