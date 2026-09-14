# Introduction
In this project, we are focused on parsing a Variant Call Format (VCF) file (`clinvar_20190923_short.vcf`) to analyze genetic variations and their associated phenotypes. The target is to write a Python script that reads the file. 

The project included the script `project01.py`,  and the program extracts specific value pairs from the `INFO` column to identify rare variants, which are defined as having an ExAC allele frequency (`AF_EXAC`) of less than 0.0001. For these rare variants, the code extracts the associated diseases from the `CLNDN` key, and excluding any entries marked as "not_specified" or "not_provided". Then,  it counts the number of times each disease occurs and outputs the results using the `pprint` module.


# Pseudocode
FUNCTION parse_line(a line of text):
    1. <SPLIT the line into the columns using tabs.>
    2. <EXTRACT the INFO column and split it into semicolon-separated pairs.>
    3. <CREATE an empty lookup dictionary.>
    4. <FOR each pair in the INFO column:>
            <SPLIT the pair at the first "=".>
            <IF the pair does not contain both a key and a value:>
                <CONTINUE to the next pair.>
            <STORE the Key and Value in the lookup dictionary.>
    5. <IF "AF_EXAC" is not in the lookup dictionary:>
            <RETURN an empty list.>
    6. <CONVERT the value of "AF_EXAC" to a number.>
    7. <IF "AF_EXAC" is greater than or equal to 0.0001:>
            <RETURN an empty list.>
    8. <SPLIT the "CLNDN" value into disease names using "|".>
    9. <CREATE an empty final disease list.>
    10.<FOR each disease:>
            <IF the disease is not "not_specified" and not "not_provided":>
                <ADD the disease to the final disease list.> 
    11. <RETURN the final disease list.>

FUNCTION read_file(file):
    1. <CREATE an empty counts dictionary.>
    2. <OPEN the file.>
    3. <FOR each line in the file:>
            <IF the line begins with "#":>
                <CONTINUE to the next line.>
            <CALL parse_line(line) to obtain a list of rare-variant diseases.>
            <FOR each disease in the returned list:>
                <IF the disease already exists in the counts dictionary:>
                    <INCREASE its count by 1.>
                <ELSE:>
                    <ADD the disease to the dictionary with a count of 1.>
    4. <RETURN counts dictionary.>

```
Some pseudocode here
```

# Successes
- Read line by line: The program uses a line-by-line reading method (`for line in f:`). This avoids loading the entire VCF file into memory with `readlines()`, allowing it to handle massive genomic datasets.
- GitHub Collaboration: As a team, we managed the fork-and-pull-request workflow. Collaborators successfully forked the leader's repository and committed changes directly to their `project01_PR` branches. We then successfully opened pull requests and merged the collaborators' code into the project leader's repository after review.

# Struggles
Description of the stumbling blocks the team experienced

# Personal Reflections
## Group Leader
Because I am not very familiar with GitHub, setting up the repository infrastructure was a bit of a struggle for me.  I had some difficulty understanding the workflow for creating the `project01_start` bookmark branch and the `project01_PR` branch. Also, due to some missteps during the branch creation and commit process, my branch ended up being 2 commits ahead of main instead. It took me some time to solve these problems, but it gave me a much clearer understanding of how commits and branching actually work in a collaborative environment.

## Other member
Other members' reflections on the project

# Generative AI Appendix
As per the syllabus
