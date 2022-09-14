# Election_Analysis

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

'''

 # Add our dependencies.
import csv
import os

# Add a variable to load a file from a path.
file_to_load = os.path.join("election_results.csv")
# Add a variable to save the file to a path.
file_to_save = os.path.join("election_analysis.txt")

# Initialize a total vote counter.
total_votes = 0

# Candidate Options and candidate votes.
candidate_options = []
candidate_votes = {}

# 1: Create a county list and county votes dictionary.
county_list = []
county_votes = {}


# Track the winning candidate, vote count and percentage
winning_candidate = ""
winning_count = 0
winning_percentage = 0

# 2: Track the largest county and county voter turnout.
winning_county = ""
winning_county_votes = 0
winning_county_percentage = 0


# Read the csv and convert it into a list of dictionaries
with open(file_to_load) as election_data:
    reader = csv.reader(election_data)

    # Read the header
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

        # Get the candidate name from each row.
        candidate_name = row[2]

        # 3: Extract the county name from each row.
        county_name = row[1]


        # If the candidate does not match any existing candidate add it to
        # the candidate list
        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1

        # 4a: Write an if statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in county_list:


            # 4b: Add the existing county to the list of counties.
            county_list.append(county_name)


            # 4c: Begin tracking the county's vote count.
            county_votes[county_name] = 0


        # 5: Add a vote to that county's vote count.
        county_votes[county_name] += 1


# Save the results to our text file.
with open(file_to_save, "w") as txt_file:

    # Print the final vote count (to terminal)
    election_results = (
        f"\nElection Results\n"
        f"-------------------------\n"
        f"Total Votes: {total_votes:,}\n"
        f"-------------------------\n\n"
        f"County Votes:\n")
    print(election_results, end="")

    txt_file.write(election_results)

    # 6a: Write a for loop to get the county from the county dictionary.
    for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        county_vote = county_votes.get(county_name)
        # 6c: Calculate the percentage of votes for the county.
        county_percent = float(county_vote) / float(total_votes)* 100
         # 6d: Print the county results to the terminal.
        county_results = (
            f"{county_name}: {county_percent:.1f}%: {county_vote}\n")
        print(county_results)
         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)


         # 6f: Write an if statement to determine the winning county and get its vote count.
        if (county_vote > winning_county_votes) and (county_percent > winning_county_percentage):
            winning_county_votes = county_vote
            winning_county = county_name
            winning_county_percentage = county_percent

    # 7: Print the county with the largest turnout to the terminal.
    winning_county_summary = (
        f"----------------------\n"
        f"Largest County Turnout: {winning_county}\n"
        f"-----------------------\n"
    )
    print(winning_county_summary)

    # 8: Save the county with the largest turnout to a text file.
    txt_file.write(winning_county_summary)


    # Save the final candidate vote count to the text file.
    for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the
        # terminal.
        print(candidate_results)
        #  Save the candidate results to our text file.
        txt_file.write(candidate_results)

        # Determine winning vote count, winning percentage, and candidate.
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

    # Print the winning candidate (to terminal)
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)

    # Save the winning candidate's name to the text file
    txt_file.write(winning_candidate_summary)
'''

However, certain changes are recommended when running the script for other elections. These are:
    
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
