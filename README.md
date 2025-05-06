#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_VOTERS 100
#define CANDIDATE_COUNT 3

// Candidate names
char candidates[CANDIDATE_COUNT][50] = {
    "Janasena",
    "Ysrcp",
    "Tdp"
};

// Votes array
int votes[CANDIDATE_COUNT] = {0};

// Function to display the voting menu
void castVote() {
    int choice;

    printf("\nVote for your candidate:\n");
    for (int i = 0; i < CANDIDATE_COUNT; i++) {
        printf("%d. %s\n", i + 1, candidates[i]);
    }

    printf("Enter your choice (1 - %d): ", CANDIDATE_COUNT);
    scanf("%d", &choice);

    if (choice >= 1 && choice <= CANDIDATE_COUNT) {
        votes[choice - 1]++;
        printf("Thank you for voting!\n");
    } else {
        printf("Invalid choice. Vote not counted.\n");
    }
}

// Function to show the vote count
void showResults() {
    printf("\n--- Voting Results ---\n");
    for (int i = 0; i < CANDIDATE_COUNT; i++) {
        printf("%s: %d votes\n", candidates[i], votes[i]);
    }

    // Finding the winner
    int maxVotes = votes[0];
    int winnerIndex = 0;
    for (int i = 1; i < CANDIDATE_COUNT; i++) {
        if (votes[i] > maxVotes) {
            maxVotes = votes[i];
            winnerIndex = i;
        }
    }

    printf("\nWinner: %s🎉\n", candidates[winnerIndex]);
}

// Main function
int main() {
    int n, i;
    printf("Enter number of voters: ");
    scanf("%d", &n);

    if (n <= 0 || n > MAX_VOTERS) {
        printf("Invalid number of voters.\n");
        return 1;
    }

    for (i = 0; i < n; i++) {
        printf("\nVoter %d:\n", i + 1);
        castVote();
    }

    showResults();
    return 0;
}
