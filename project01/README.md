# Introduction
In this project, we are focused on parsing a Variant Call Format (VCF) file (`clinvar_20190923_short.vcf`) to analyze genetic variations and their associated phenotypes. The target is to write a Python script that reads the file. 

The project included the script `project01.py`,  and the program extracts specific value pairs from the `INFO` column to identify rare variants, which are defined as having an ExAC allele frequency (`AF_EXAC`) of less than 0.0001. For these rare variants, the code extracts the associated diseases from the `CLNDN` key, and excluding any entries marked as "not_specified" or "not_provided". Then,  it counts the number of times each disease occurs and outputs the results using the `pprint` module.


# Pseudocode


```
FUNCTION parse_line(line):
   columns ← SPLIT(line, "\t")
   pairs   ← SPLIT(columns[INFO], ";")
   lookup  ← {}                       # empty dictionary

   FOR each pair IN pairs:
       key, value ← SPLIT_FIRST(pair, "=")
       IF key is missing OR value is missing:
           CONTINUE
       lookup[key] ← value

   IF "AF_EXAC" NOT IN lookup:
       RETURN []

   af ← TO_NUMBER(lookup["AF_EXAC"])
   IF af ≥ 0.0001:
       RETURN []

   diseases ← SPLIT(lookup["CLNDN"], "|")
   result   ← []

   FOR each d IN diseases:
       IF d ≠ "not_specified" AND d ≠ "not_provided":
           APPEND d TO result

   RETURN result
```
```
FUNCTION read_file(file):
   counts ← {}
   OPEN file



   FOR each line IN file:
       IF line STARTS WITH "#":
           CONTINUE                   # header line



       diseases ← parse_line(line)



       FOR each d IN diseases:
           IF d IN counts:
               counts[d] ← counts[d] + 1
           ELSE:
               counts[d] ← 1



   RETURN counts
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
