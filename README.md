# hangman
For my programming 1 class my group made a hangman program

# Playing the Game
To play the game download the .exe file in the repository. The user is given seven tries to guess the word.  
For each correct answer part of the word is output to show the user what the word looks like.

![image](https://user-images.githubusercontent.com/117185451/235273379-100c94be-3655-4c15-b600-935e1a90a8bd.png)


For each incorrect answer a part of the hangman appears.

![image](https://user-images.githubusercontent.com/117185451/235273570-d13ca3b9-ccfb-4fd6-956b-3ea0ed854be0.png)

The user has the option to guess the word all at once, but for every incorrect letter a hangman appears.

# Editing the code
To edit the code, a c++ compiler is recommeneded because the code is writen in c++. The code is made up of three functions: the main function, the playgame function, and the main function. 

# The hangman function
The playGame function makes up the game loop.It is home to the words vector, which keeps 50 words that the program can chose to present to the user. After picking one randomly, the program takes user input. The user may try to guess the entire word or enter one letter at a time. The program then loops through the correct answer to see if the user has selected a correct letter. This funciton keeps track of the number of guesses the user has made and the number of incorrect guesses.
# The hangman funciton
The hangman function is mostly comprised of a switch case. The switch takes in the number of times the user has input an incorrect letter and based off of the outputs an image. The function contains seven cases. The function takes in the incorrectguesses variable as a parameter.

# The main function
The main function calls the other variable. To access the you can click on the .cpp file or you may copy and paste it into your c++ compiler from here:


#include <iostream>
#include <vector>
#include <string>
#include <cstdlib>
#include <ctime>

using namespace std;

// initialize functoions
void playGame();
void hangman(int incorrectGuesses);


void playGame()
{
    int incorrectGuesses = 0;

    vector<string> words = {"innovation", "stroll", "finger", "pan", "sleeve","run","frequency","justice","development","chimney","hobby","shelf","challenge","pledge","tenant","nursery","chief","humanity","hit","obligation","safety","throat","absence","coincide","station","belong","enter","mosaic","straight","refuse","fastidious","commission","fairy","brainstorm","passage","dribble","fill","graduate","fill","able","yard","confession","tower","chop","strong","dominant","crowd","rehabilitation","advance","departure","quarter"};

    // Generate a random index
    srand(time(nullptr));
    string word = words[rand() % words.size()];
    int lengthword = word.length();

    // Create a string with underscores to represent the word
    string wordGuessed(word.size(), '_');

    // Start the game loop
    int numGuesses = 0;
    int maxGuesses = 7;

    bool gameWon = false;

    while (numGuesses < maxGuesses && !gameWon)
    {
        cout << "\nguess the word: ";
        for (int i = 0; i < lengthword; i++)
        {
            if (wordGuessed[i] != '_')
            {
                cout << " " << wordGuessed[i] << " ";
            }
            else
            {
                cout << " _ ";
            }
        }

        cout << "\n";
        char guess;
        cin >> guess;

        // Check if the guess is correct
        bool correct = false;
        for (int i = 0; i < word.size(); i++)
        {
            if (word[i] == guess)
            {
                wordGuessed[i] = guess;
                correct = true;
            }
        }

        if (correct)
        {
            cout << "Good guess! The word looks like this: ";
            for (int i = 0; i < lengthword; i++)
            {
                if (wordGuessed[i] != '_')
                {
                    cout << " " << wordGuessed[i] << " ";
                }
                else
                {
                    cout << " _ ";
                }
            }
            cout << "\n";

            if (wordGuessed == word)
            {
                gameWon = true;
            }
        }
        else
        {
            cout << "Sorry, that letter is not in the word. You have " << maxGuesses - numGuesses - 1 << " guesses left." << endl;
            numGuesses++;
            incorrectGuesses++;
            hangman(incorrectGuesses);
        }
    }

    if (gameWon)
    {
        cout << "\nCongratulations, you guessed the word: " << word << endl;
    }
    else
    {
        cout << "\nSorry, you ran out of guesses. The word was: " << word << endl;
    }
}






void hangman(int incorrectGuesses)
{
    switch (incorrectGuesses)
    {
        case 1:
            cout << R"(
        /  \_______________________________________
        |  |                                       |
        |  |_______________________________________|
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |__|________________________________________
        )" << endl;
        break;


        case 2:
            cout << R"(
        /  \_______________________________________
        |  |                   \                   |
        |  |____________________\__________________|
        |  |                    |
        |  |                    |
        |  |                    |
        |  |                    |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |__|________________________________________
        )" << endl;
        break;

        case 3:
            cout << R"(
        /  \_______________________________________
        |  |                   \                   |
        |  |____________________\__________________|
        |  |                    |
        |  |                    |
        |  |                    |
        |  |                 ___|___
        |  |                / __  __\
        |  |                \    _\ /
        |  |                 \_____/
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |  |
        |__|________________________________________
        )"<< endl;
        break;

        case 4:
            cout << R"(
        /  \_______________________________________
        |  |                   \                   |
        |  |____________________\__________________|
        |  |                    |
        |  |                 ___|___
        |  |                / __  __\
        |  |                \    _\ /
        |  |                 \_____/
        |  |                    |
        |  |                    |
        |  |                   /|
        |  |                  / |
        |  |                 /  |
        |  |                    |
        |  |                    |
        |  |                    |
        |  |
        |  |
        |__|________________________________________
        )"<< endl;
        break;

        case 5:
            cout << R"(
        /  \_______________________________________
        |  |                   \                   |
        |  |____________________\__________________|
        |  |                    |
        |  |                 ___|___
        |  |                / __  __\
        |  |                \    _\ /
        |  |                 \_____/
        |  |                    |
        |  |                    |
        |  |                   /|
        |  |                  / | \
        |  |                 /  |  \
        |  |                    |
        |  |                    |
        |  |                    |
        |  |
        |  |
        |__|________________________________________
        )"<< endl ;
        break;

        case 6:
             cout << R"(
        /  \_______________________________________
        |  |                   \                   |
        |  |____________________\__________________|
        |  |                    |
        |  |                 ___|___
        |  |                / __  __\
        |  |                \    _\ /
        |  |                 \_____/
        |  |                    |
        |  |                    |
        |  |                   /|
        |  |                  / | \
        |  |                 /  |  \
        |  |                    |
        |  |                    |
        |  |                    |
        |  |                   /
        |  |                  /
        |  |                 /
        |  |
        |__|________________________________________
        )"<< endl;
        break;

         case 7:
             cout << R"(
        /  \_______________________________________
        |  |                   \                   |
        |  |____________________\__________________|
        |  |                    |
        |  |                 ___|___
        |  |                / __  __\
        |  |                \    _\ /
        |  |                 \_____/
        |  |                    |
        |  |                    |
        |  |                   /|
        |  |                  / | \
        |  |                 /  |  \
        |  |                    |
        |  |                    |
        |  |                    |
        |  |                   / \
        |  |                  /   \
        |  |                 /     \
        |  |
        |__|________________________________________


        ********************************************
        *                                          *
        *               GAME OVER                  *
        *            STICK MAN DEAD :(             *
        *     STICK WIFE AND STICK CHILDREN SAD    *
        *                                          *
        ********************************************
        )" << endl;
        break;
    }

}

int main()
{

    cout << R"(
               *************************************************
               *                                               *
               *                                               *
               *            WELCOME TO HANGMAN                 *
               *                                               *
               *    YOU WILL HAVE 7 GUESSES FOR EACH WORD      *
               *                                               *
               *      FAILURE TO GUESS THE WORD CORRECTLY      *
               *                                               *
               *          WILL RESULT IN THE MURDER            *
               *                                               *
               *          OF A INNOCENT STICKMAN               *
               *                                               *
               *        (He has a family of four btw)          *
               *                                               *
               *        HIS FATE RESTS IN YOUR HANDS           *
               *                                               *
               *                                               *
               *                                               *
               *************************************************

            )";


    playGame();


    return 0;
}












