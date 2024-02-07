#include <iostream>
#include <cstdlib>
#include <ctime>
#include <stdio.h>
#include <algorithm>
#include <vector>

// Function to generate a random index within the range of the array
int getRandomIndex(int size) {
    return rand() % size;
}

// ANSI escape codes for text color
const char* ANSI_BLUE = "\033[34m";
const char* ANSI_GREEN = "\033[32m";
const char* ANSI_CYAN = "\033[36m";
const char* ANSI_RED = "\033[31m";
const char* ANSI_YELLOW = "\033[93m";
const char* ANSI_MAGENTA = "\033[35m";
const char* ANSI_PURPLE = "\033[95m";
const char* ANSI_UNDERLINE = "\033[4m";
const char* ANSI_BOLD = "\033[1m";
const char* ANSI_UNDO = "\033[0m";

//the suffle array feature, so it can shuffle the arrays before selecting a random element and adjust the randomization to make the selection more evenly distributed
//actually, I am now using vectors, so that I can make my code more flexible if I want to add more things to strings
void shuffleVector(std::vector<std::string>& vec) {
    std::random_shuffle(vec.begin(), vec.end());
}


void generateRandomPrompt() {
    // Sample arrays for characters, settings, plot ideas, and personality traits
    std::vector<std::string> characters = { "kid", "adult", "toddler", "stay at home mother", "overworked mother", "child genius", "detective", "baby","game developer", "teenage queen bee", "teenager", "writer", "song writer", "dancer", "artist", "auto mechanic", "chef", "waiter", "waitress", "prince", "princess", "elderly woman", "elderly man", "prisoner", "child", "nerdy teen", "college student", "overworked father", "stay at home father", "scientist", "wizard", "alien", "time traveler", "football player", "soccer player", "doctor", "high school dropout", "pop star",  "teenage girl", "teenage boy", "ballerina", "construction worker", "mechanic", "teacher", "professor", "supermodel", "fairy", "mermaid", "vampire", "warewolf", "dog", "cat", };
    std::vector<std::string> settings = { "abandoned castle", "restaurant", "downtown", "outer space", "enchanted kingdom", "small rural town", "grocery store", "enchanted forest", "middle school", "underwater city", "elevator", "beach", "high school", "doctor's office", "dentist's office", "subway train", "desert", "train station", "tropical island", "ghost town", "school bus", "deserted island", "haunted house", "castle", "elementary school", "tall tower", "park", "forest", "ocean", "lake", "suburban neighborhood", "religious building", "barn", "ranch", "library", "toy store", "college campus", "apartment building", "magic toy store" ,"magic school", "magic library", "child's bedroom", "mansion", "haunted mansion", "daycare", "mall", "clothing store", "department store", "maze", "hotel", "motel", "museum" , "carnival","haunted castle", "toy factory", "daycare", "Mars", "underwater city", "North Pole", "Small rural town" };
    std::vector<std::string> conflict1 = { "solve a murder mystery", "feels trapped and wants to escape", "start a heist", "is lost", "discover a dead body", "can't escape the dream world", "survive a disaster", "is trying to become famous", "is kidnapped", "is suffering with loneliness", "meet their real parents for the first time", "start a business", "has to overcome a health issue", "suffer an injury", "is trapped and trying to escape", "is trapped in a video game", "family member says something embarrassing about the protagonist", "need to find treasure", "need to break a family curse", "need to break the town's curse", "has a cursed item", "is trying to escape a murderer", "lost their memory", "important item is lost", "has their phone stolen", "is trying to hide secret identity”, “is turned into an animal", "is shrunk down", "has everyone turn against them", "wants to be leader", "wants to own a business", "is trying to get a job", "is trying to get into a good school", "parent is kidnapped", "parents are kidnapped", "died and is trying to come back to life", "died and is a ghost", "is threatened with violence", "solve a heist mystery", "is stranded in space", "has accidentally built a dangerous invention", "accidentally discover a bag is with a weapon and a  ton of money", "has to attempt to break into some building to find something", "think that something/place is haunted/cursed", "has to go to war and fight someone", "tracks down a criminal" };
    std::vector<std::string> conflict2 = { "is turned into a toy", "is being chased by someone who wants to eat them", "is trying to think of an idea of what to make their work about (like a book, song, painting, etc.)", "falls in love with someone who doesn't love them back", "switches bodies with sibling", "switches bodies with their child", "is  trying to make a movie",  "is dealing with writer's block", "is tasked with helping other people get ready for a contest", "has to help overthrow the government", "apocalypse", "pandemic", "natural disaster”, “is forced to work with someone they hate", "turns into a different creature", "accidentally travels back in time", "accidentally travels forward in time", "switches bodies with parent", "switches body with worst enemy", "tries to win the approval of someone", "job loss", "is forced to do a dare", "is forced to do something embarrassing on stage", "has to learn to overcome stage fright", "tries to follow the dream they've had their whole life", "wants to do something that their parents do not approve of", "has some trip cancelled on them", "is short on money and is desperate to make some”, “accidentally kills someone", "navigate a forbidden romance", "discovers a ghost", "battle a supernatural force", "has to overthrow the government", "have to babysit someone but manage to lose them in the blink of an eye", "is trying to win a contest", "is trying to make new friends and get out more", "is separated from loved one" };
    std::vector<std::string> conflict3 = { "plays magic board game", "has to return something, but it is lost or damaged", "thinks of imaginary world", "a park is about to get torn down, and a group of kids try to save it", "someone's idea was stolen", "protagonist tries to rob a bank, looking for the money needed for financing the cure of a dying relative", "protagonist goes on a cross-country adventure to return an important item", "protagonist starts getting revenge on all the people who have wronged them", "protagonist is trapped with a dangerous person", "thinks of imaginary world that becomes real", "is sick", "protagonist gets broken up with and tries to win him/her back" };
    std::vector<std::string> traits1 = { "funny", "arrogant", "brave", "resilient", "logical", "shy", "outgoing", "vain",  "passive", "passive aggressive", "aggressive", "honest", "blunt", "dishonest", "cowardly", "creative", "kind", "neurotic", "ambitious", "awkward", "stubborn", "compassionate", "selfish", "rude", "humble", "inconsiderate", "selfless", "polite", "confident", "sassy", "apathetic", "callous", "trustworthy", "conceited", "nurturing" };
    std::vector<std::string> traits2 = { "funny", "arrogant", "brave", "resilient", "logical", "shy", "outgoing", "vain",  "passive", "passive aggressive", "aggressive", "honest", "blunt", "dishonest", "cowardly", "creative", "kind", "neurotic", "ambitious", "awkward", "stubborn", "compassionate", "selfish", "rude", "humble", "inconsiderate", "selfless", "polite", "confident", "sassy", "apathetic", "callous", "trustworthy", "conceited", "nurturing" };
    std::vector<std::string> hobby = { "writing", "playing guitar", "playing the drums", "painting", "singing", "knitting", "sewing", "football", "basketball", "video games", "make up", "making videos", "doing magic spells", "playing sports", "playing music", "woodworking", "gardening", "photography", "building websites", "reading", "reading comic books", "reading romance novels", "hiking", "board ganes", "card games", "roleplay games", "puzzles", "cooking", "baking", "camping", "making jewelry", "writing poems", "writing stories", "learning languages" };

    // For shuffling the vectors for more randomness
    shuffleVector(characters);
    shuffleVector(settings);
    shuffleVector(conflict1);
    shuffleVector(conflict2);
    shuffleVector(conflict3);
    shuffleVector(traits1);
    shuffleVector(traits2);
    shuffleVector(hobby);


    // Generate random prompts
    std::cout << ANSI_GREEN << "\n \nRandom Prompt: \n" << ANSI_PURPLE << "\n \nRandom Character: " << ANSI_CYAN << characters[getRandomIndex(characters.size())] << "\n";
    std::cout << ANSI_PURPLE << "Setting: " << ANSI_CYAN << settings[getRandomIndex(settings.size())] << "\n";
    std::cout << ANSI_RED << "Choose one of two plots (or both).\n" << ANSI_PURPLE << "Plot Idea 1: " << ANSI_CYAN << conflict1[getRandomIndex(conflict1.size())] << "\n";
    std::cout << ANSI_PURPLE << "Plot Idea 2: " << ANSI_CYAN << conflict2[getRandomIndex(conflict2.size())] << "\n";
    std::cout << ANSI_PURPLE << "Plot Idea 3: " << ANSI_CYAN << conflict3[getRandomIndex(conflict3.size())] << "\n";
    std::cout << ANSI_PURPLE << "Personality Traits: " << ANSI_CYAN << traits1[getRandomIndex(traits1.size())];
    std::cout << ANSI_CYAN << " and " << traits2[getRandomIndex(traits2.size())] << "\n";
    std::cout << ANSI_PURPLE << "Hobby: " << ANSI_CYAN << hobby[getRandomIndex(hobby.size())] << ANSI_RED << " \n \nNote: If you get two opposite traits (example: ''brave'' and ''cowardly''), you can make the story have a character arc where the person has one trait but changes and eventually gets the other.\n \n" << ANSI_BLUE << "\n \n";
    

}

void generateStoryPrompt() {
    // Sample vectors for story beginning, middle, and end
    std::vector<std::string> exposition = { "protagonist and their family has lived in stagnent lives and has never had any adventures", "something is being brought back to life", "there is an apocalypse", "protagonist is forced to do something", "the protagonist is a bad person", "Character is rude and needs to be taught a lesson", "protagonist is a recently divorced person or was broken up with", "protagonist is making an invention", "protagonist has just finished creating a new invention", "protagonist feels like they are not able to be themselves and are only doing things that other people want them to do", "protagonist is unconfident", "protagonist finds out they are pregnant or that someone else is", "protagonist needs to get a rare item", "protagonist wants/needs the approval for something", "protagonist had just lost a loved one and is in mourning", "protagonist has a dream to become famous", "protagonist used to have an amazing glorious life, but they don't anymore", "protagonist is an an abusive relationship with significant other/friend/family member", "protagonist desperately wants a friend or significant other", "protagonist's friend/family member has moved far away", "protagonist just moved to a new place", };
    std::vector<std::string> wayToGiveExposition = { "through dialogue between characters", "through media (TV, online, newspapers, phone call, text, letter, book, etc.)", "saying it outright", "disguise the information, perhaps by distracting the audience", "dely the information and give the context little by little until around the climax", "mise en scène (meaning it shows from used through showing props, environment, feeling, and scenery for specific story, interaction, or chapter)" };
    std::vector<std::string> middle = { "the protagonist faced challenges", "the character goes on a quest", "the character trains", "unexpected events unfolded", "a mysterious stranger appeared", "the tension reached its peak" };
    std::vector<std::string> climax = { "hang off the edge of building as the villain at them in an attempt to have them killed, then to his death", "discovers the treasure", "protagonist finds the someone they were looking for", "the (person in charge, such as a boss, recruiter, coach, teacher, etc.) has posted a list of people who get to participate or compete. The protagonists walks forward to look at the list", "kills the villain", "the protagonist wins something", "protagonist and other characters team up to defeat the villain", "protagonist confesses their love", "another character confesses their love for the protagonist", "the protagonist's relationship (romantic or platonic) ends", "They call the protagonist to talk with them about their decision", "exposes the villain", "hero saves the victim", "main character escapes", "the main character comes face to face with the final villain, and they win", };
    std::vector<std::string> end = { "and they lived happily ever after", "the world was forever changed", "a new adventure began", "the mystery was finally solved", "the main character gets killed", "the villain is killed", "two characters go their seperate ways", "main character has a child", "the main character gets an award", "friend/loved one dies" };

    // Shuffle arrays for more randomness
    shuffleVector(exposition);
    shuffleVector(wayToGiveExposition);
    shuffleVector(middle);
    shuffleVector(climax);
    shuffleVector(end);

    // Generate random story prompts
    std::cout << ANSI_GREEN << "\n \nRandom story with entire plot from start to finish: \n \n" << ANSI_PURPLE << "Exposition: " << ANSI_CYAN << exposition[getRandomIndex(exposition.size())] << ANSI_BLUE << "\n";
    std::cout << ANSI_PURPLE << "Way to give the exposition: " << ANSI_CYAN << wayToGiveExposition[getRandomIndex(wayToGiveExposition.size())] << "\n";
    std::cout << ANSI_PURPLE << "Middle: " << ANSI_CYAN << middle[getRandomIndex(middle.size())] << ANSI_BLUE << "\n";
    std::cout << ANSI_PURPLE << "Climax: " << ANSI_CYAN << climax[getRandomIndex(climax.size())] << ANSI_BLUE << "\n";
    std::cout << ANSI_PURPLE << "End: " << ANSI_CYAN << end[getRandomIndex(end.size())] << ANSI_BLUE << "\n \n";
}

int main() {
    srand(static_cast<unsigned>(time(0))); // Seed the random number generator

    int choice;

    do {
        

        std::cout << ANSI_GREEN << ANSI_UNDERLINE << ANSI_BOLD << "Menu:\n" << ANSI_UNDO; //the "\033[1m" part made everything bold
        std::cout << ANSI_BLUE << ANSI_BOLD << "1. Random Prompt Generator\n";
        std::cout << ANSI_BLUE << "2. Story Prompt Generator\n";
        std::cout << ANSI_BLUE << "3. Exit\n";
        std::cout << ANSI_BLUE << ANSI_RED << "Enter your choice: ";
        std::cin >> choice;

        // Process user choice
        switch (choice) {
        case 1:
            generateRandomPrompt();
            break;
        case 2:
            generateStoryPrompt();
            break;
        case 3:
            std::cout << ANSI_YELLOW << "Leaving program. Happy writing!\n";
            break;
        default:
            std::cout << ANSI_YELLOW << "Invalid choice. That is not an option. Please try again.\n";
        }

    } while (choice != 3);

    return 0;
}




