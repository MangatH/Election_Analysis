# Election_Audit

## Overview of Election Audit
The overall purpose of the election audit analysis is to fulfill the following tasks to complete the election audit of a recent local congressional election.

1. Calculate the total number of votes cast.
2. Get a complete list of candidates who received votes.
3. Calculate the total number of votes each candidate received.
4. Calculate the percentage of votes each candidate won.
5. Determine the winner of the election based on popular vote.
6. The voter turnout for each county.
7. The percentage of votes from each county out of the total count.
8. The county with the highest turnout.

## Election-Audit Results

The analysis of the election show that:
* There were 369,711 votes cast in the election.
* The counties were:
    1. Jefferson
    2. Denver
    3. Arapahoe
* Number of votes and the percentage of total votes for each county:
    1. Jefferson: 38,855 votes (10.5%)
    2. Denver: 306,055 votes (82.8%)
    3. Arapahoe: 24,801 votes (6.7%)
* The county Denver had the largest number of votes.
* The candidates were:
    1. Candidate 1: Charles Casper Stockham
    2. Candidate 2: Diana DeGette
    3. Candidate 3: Raymon Anthony Doane
* The candidate results were:
    1. Candidate 1:Charles Casper Stockham, received 23% of the vote and 85,213 number of votes.
    2. Candidate 2:Diana DeGette received, 73.8% of the vote and 272,892 number of votes.
    3. Candidate 3:Raymon Anthony Doane ,received 3.1% of the vote and 11,606 number of votes.
* Candidate 2: Diana DeGette had the largest number of votes i.e. 272,892.
* The winner of the election was:
    -Candidate 2:Diana DeGette, who received 73.8% of the vote and 272,892 number of votes.

## Election-Audit Summary
The challenge revolved around writing a python script to show the election result by running an election audit ,as what is expected by the Colorado Board of Elections employee and then writing the election results to a text file, in order to have a clear glance on the election results. It will make things more convenient, as for someone to just know the results by looking at the text file and not inspecting and looking at the code all over again,it is quite time saving. 
The same python script can be used to analyse the results of various elections.
However, certain changes are recommended when running the script for other elections. Some examples are:
    
    1.'''
      # Add a variable to load a file from a path.
      file_to_load = os.path.join("election_results.csv")
      # Add a variable to save the file to a path.
      file_to_save = os.path.join("election_analysis.txt")
      '''
    The code can be modified by updating the name of the file to be loaded, which is "election_results.csv" here, it can have other name too, depending on type of election. Further, the path to open the file can be modified as per the location of the file in the system.

    2. '''
        # Print the final vote count (to terminal)
       election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    print(election_results, end="")
    '''
    The print function can be modified depending on what is the desired outcome that one wants to print.

## Conclusion:
Through this challenge, it was found evident that the **Candidate 2: Diana DeGette**, won the election by receiving **73.8% votes**. This analysis was possible by using functions such as **'for'** to iterate through the data and knowing the total votes. Furthermore, using an **'if'** function to check certain conditions. At the end using the **'print'** function to print the results to the terminal. 

Taking one step further, by writing the outcomes to a text file by using the function **'write'**, in order to make the results readable for everyone without going through the code again and again.
<img width="539" alt="Screen Shot 2022-09-13 at 9 08 23 PM" src="https://user-images.githubusercontent.com/111387025/190036347-ed368f3c-0ccf-413c-803f-d169faf5ae25.png">
