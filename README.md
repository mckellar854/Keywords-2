# Keywords-2
/*
Zechariah McKellar
11/22/2020
Program to randomly pick 3 words out of 10 to guess without hints.
*/
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
#include <ctime>
#include <cctype>

using namespace std;
string user;

int main()
{   // Display Title of the program to the user
	cout << "Code Breaker Training Simulation" << endl;
	// Ask the recruit to log in using their name
	cout << "Log in using your name" << endl;
	// Hold the recruit's name in a var, and address them by it throughout the simulation.
	cin >> user;
	// set-up
	const int MAX_WRONG = 8;  // maximum number of incorrect guesses allowed

	cout << "Now your bosses at the CIA want you to build a more challenging version for the CIA recruits. " << endl; // Display an overview of what Keywords II is to the recruit
	cout << "Those recruits which made it past the first round of cuts in their training. " << endl;
	cout << "You remember what that was like when you joined the CIA. " << endl;
	
	cout << "To play guess the word" << endl; // Display directions to the recruit on how to use Keywords
	cout << "To guess type in a letter" << endl;
	
	vector<string> words;  // Create a collection of 10 words you had written down manually
	words.push_back("SPY");
	words.push_back("ASSET");
	words.push_back("EYEWASH");
	words.push_back("BACKDROP");
	words.push_back("ILLEGAL");
	words.push_back("ACTIVE");
	words.push_back("AGENT");
	words.push_back("BLACK");
	words.push_back("COVER");
	words.push_back("ELITE");

	srand(static_cast<unsigned int>(time(0)));
	random_shuffle(words.begin(), words.end()); 
	const string THE_WORD = words[0];            // Pick new 3 random words from your collection as the secret code word the recruit has to guess.
	int wrong = 0;                               // number of incorrect guesses
	int count = 1;                               // Create an int var to count the number of simulations being run starting at 1
	string soFar(THE_WORD.size(), '-');          // word guessed so far
	string used = "";                            // letters already guessed
	char again = 'y';

	// main loop
	while (again == 'y')
	{
		while ((wrong < MAX_WRONG) && (soFar != THE_WORD))  // While recruit hasn’t made too many incorrect guesses and hasn’t guessed the secret word
		{
			cout << "Simulation # " << count << endl;   // Create an int var to count the number of simulations being run starting at 1
														// Display the simulation # is starting to the recruit.
			cout << "\n\nRecruit " << user << "you have" << (MAX_WRONG - wrong);  // Tell recruit how many incorrect guesses he or she has left
			cout << " incorrect guesses left.\n";
			cout << "\nYou've used the following letters:\n" << used << endl; // Show recruit the letters he or she has guessed
			cout << "\nSo far, the word is:\n" << soFar << endl; // Show player how much of the secret word he or she has guessed

			char guess;
			cout << "\n\n" << user << "Enter your guess: "; // Get recruit's next guess
			cin >> guess;
			guess = toupper(guess); //make uppercase since secret word in uppercase
			while (used.find(guess) != string::npos) // While recruit has entered a letter that he or she has already guessed
			{
				cout << "\nRecruit You've already guessed " << guess << endl;
				cout << "" << user << "Enter your guess: "; // Get recruit’s guess
				cin >> guess;
				guess = toupper(guess); // Add the new guess to the group of used letters
			}

			used += guess;

			if (THE_WORD.find(guess) != string::npos)
			{
				cout << "That's right! " << guess << " is in the word.\n"; // If the guess is in the secret word
				cout << "You are correct" << endl; // Tell the recruit the guess is correct
				// update soFar to include newly guessed letter
				for (unsigned int i = 0; i < THE_WORD.length(); ++i)
				{
					if (THE_WORD[i] == guess)
					{
						soFar[i] = guess;
					}
				}
			}
			else     // Otherwise
			{
				cout << "Sorry, " << user << " " << guess << " isn't in the word.\n"; // Tell the recruit the guess is incorrect
				cout << "This is incorrect" << endl;
				++wrong; // Increment the number of incorrect guesses the recruit has made
			}
		}
		++count;

		// shut down
		if (wrong == MAX_WRONG) // If the recruit has made too many incorrect guesses
			cout << "\nYou've failed the keywords 2 course"; // Tell the recruit that he or she has failed the Keywords II course.
		else      // Otherwise
			cout << "\nYou guessed it!";   // Congratulate the recruit on guessing the secret words

		cout << "\nThe word was " << THE_WORD << endl;

		srand(static_cast<unsigned int>(time(0)));
		random_shuffle(words.begin(), words.end());
		const string WORD = words[0];            // Pick new 3 random words from your collection as the secret code word the recruit has to guess.
		int wrong1 = 0;                               // number of incorrect guesses
		string Far(WORD.size(), '-');          // word guessed so far
		string used1 = "";                            // letters already guessed

		cout << "Welcome to Hangman.  Good luck!\n";

		// main loop
		while ((wrong1 < MAX_WRONG) && (Far != WORD))
		{
			cout << "Simulation # " << count << endl;
			cout << "\n\nRecruit " << user << "you have" << (MAX_WRONG - wrong);
			cout << " incorrect guesses left.\n";
			cout << "\nYou've used the following letters:\n" << used1 << endl;
			cout << "\nSo far, the word is:\n" << Far << endl;

			char guess;
			cout << "\n\n" << user << "Enter your guess: ";
			cin >> guess;
			guess = toupper(guess); //make uppercase since secret word in uppercase
			while (used1.find(guess) != string::npos)
			{
				cout << "\nRecruit You've already guessed " << guess << endl;
				cout << "" << user << "Enter your guess: ";
				cin >> guess;
				guess = toupper(guess);
			}

			used1 += guess;

			if (WORD.find(guess) != string::npos)
			{
				cout << "That's right! " << guess << " is in the word.\n";

				// update soFar to include newly guessed letter
				for (unsigned int i = 0; i < WORD.length(); ++i)
				{
					if (WORD[i] == guess)
					{
						Far[i] = guess;
					}
				}
			}
			else
			{
				cout << "Sorry, " << user << " " << guess << " isn't in the word.\n";
				cout << "This is incorrect" << endl;
				++wrong1;
			}
		}

		++count;
		// shut down
		if (wrong1 == MAX_WRONG)
			cout << "\nYou've failed the keywords 2 course";
		else
			cout << "\nYou guessed it!";

		cout << "\nThe word was " << WORD << endl;


		srand(static_cast<unsigned int>(time(0)));
		random_shuffle(words.begin(), words.end());
		const string WORD2 = words[0];            // Pick new 3 random words from your collection as the secret code word the recruit has to guess.
		int wrong2 = 0;                               // number of incorrect guesses
		string Far2(WORD2.size(), '-');          // word guessed so far
		string used2 = "";                            // letters already guessed

		cout << "Welcome to Hangman.  Good luck!\n";

		// main loop
		while ((wrong2 < MAX_WRONG) && (Far2 != WORD2))
		{
			cout << "Simulation # " << count << endl;
			cout << "\n\nRecruit " << user << "you have" << (MAX_WRONG - wrong);
			cout << " incorrect guesses left.\n";
			cout << "\nYou've used the following letters:\n" << used2 << endl;
			cout << "\nSo far, the word is:\n" << Far2 << endl;

			char guess;
			cout << "\n\n" << user << "Enter your guess: ";;
			cin >> guess;
			guess = toupper(guess); //make uppercase since secret word in uppercase
			while (used2.find(guess) != string::npos)
			{
				cout << "\nRecruit You've already guessed " << guess << endl;
				cout << "" << user << "Enter your guess: ";
				cin >> guess;
				guess = toupper(guess);
			}

			used2 += guess;

			if (WORD2.find(guess) != string::npos)
			{
				cout << "That's right! " << guess << " is in the word.\n";

				// update soFar to include newly guessed letter
				for (unsigned int i = 0; i < WORD2.length(); ++i)
				{
					if (WORD2[i] == guess)
					{
						Far2[i] = guess;
					}
				}
			}
			else
			{
				cout << "Sorry, " << user << " " << guess << " isn't in the word.\n";
				cout << "This is incorrect" << endl;
				++wrong2;
			}
		}

		++count;
		// shut down
		if (wrong2 == MAX_WRONG)
			cout << "\nYou've failed the keywords 2 course";
		else
			cout << "\nYou guessed it!";

		cout << "\nThe word was " << WORD2 << endl;
		cout << "Do you wish to replay the simulation  (y/n)" << endl;  // Ask the recruit if they would like to run the simulation again
																		// If the recruit wants to run the simulation again
		cin >> again;
	}
	cout << "End Simulation" << endl;
	cout << "The nummber of simulations " << count << endl;
	return 0;
}
