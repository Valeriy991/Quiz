# Quiz
Assignment on the topic "Developing an application with a graphical user interface in Java using JavaFX tools".
An illustration with the forms and the necessary objects is given in the file Forms.png
Requirements for the task:

1. Implement the Main Form, which is the main menu. The main menu should contain the following attributes:
1.1. The Button object with the Label “From Internet". When the button is pressed, the Loading Form should be launched (see point 2), which implements the loading of the quiz from the Internet. 
1.2. Button object with Label “From File". When the button is clicked, the quiz will have to be loaded from .json or .csv file. To do this, you need to use an object of the FileChooser.ExtensionFilter class. The dialog box for selecting a folder with a quiz should remember the previously selected path to the folder, and not open the default folder (you can use the Preferences class for this). After selecting the file, the form responsible for the game (Game Form) should be launched.
1.3. The CheckBox object with the Label “Show Correct Answers".

2. Implement a Loading Form that loads a quiz from the Internet according to the user's choice. To be able to select in the Loading Form, you need to create the following objects:
2.1 A TextField object with the name “Number of questions”, which takes a parameter in the form of an integer from 1 to 10.
2.2 A ComboBox object with the Label “Select Category”, with which the user can select the topic of questions. You need to manually select 4 categories, from which the user will then select one. 
2.3 A ComboBox object with the Label “Select Difficulty”, with which the user can choose the complexity of the questions (one of Easy, Medium, Hard). 
2.4 The Button object with the label “Save”, when clicked, an API request to the page should be generated https://opentdb.com/api_config.php , where a quiz with previously selected parameters will be created. Next, a dialog box (File Chooser) should open to save the generated quiz in one of two possible formats - .json or .csv. The dialog box should remember the previously selected folder path, and not open the default folder (you can use Preferences for this). Also, correct and incorrect answers must be encrypted before writing to the file (you can use, for example, cyclic shift, Caesar cipher, XOR ...). When trying to save a quiz with unselected or incorrectly selected parameters, AlertMessage should be displayed in the file, and the dialog box for selecting a folder should not open.  The objects are first converted by the Jackson parser into Java objects, and then the questions and answers must be decoded using URLDecoder. Do this in the Repository class constructor.
2.5 The Button object with the Label “Start”, when the button is clicked, the Game Form should open, which takes data from the API.  The form should not open if any quiz parameters are selected incorrectly or are not selected. AlertMessage should be displayed instead.

3. Implement a form (Game Form), which is a game menu. It should contain the following attributes:
3.1. TabPane panel with tabs - quiz questions. Each quiz question is a Label object, and the answer options are RadioButton.
3.2. The last tab of the TabPane with the name “Results". The panel should contain a Button object with the name “Check”, when clicked:
• The availability of answers to all questions is checked. If not all questions have been answered, then an AlertMessage should be displayed with the corresponding message.
• The TabPane “Results” displays statistics (Label Statistics) for each question in the format Question i : (+/-), Correct/Incorrect (for example, 3/2) and Correct Answer Rate (60%). If “Show Correct Answers” was selected in Form 1, then the correct answers to each question are also shown.
