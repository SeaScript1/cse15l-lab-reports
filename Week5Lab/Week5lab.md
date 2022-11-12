# Researching Commands: find

1. find -name

find -name returns the path of the file specified in the command. This is useful simply for obtaining the path of the file, which in turn can be used to identify its location within a directory. 

- Example 1:

```
find ./911report -name  chapter-1.txt

Output:

./911report/chapter-1.txt
```

This commands searches in the 911report folder for a file called chapter-1.txt

- Example 2:

```
find . -name diversity_priorities.txt

Output:

./government/About_LSC/diversity_priorities.txt
```

This command searches in the current directory (technical) for a file named diversity_priorities.txt, which is located two directories downstream. 

- Example 3:

```
find ./government -name bill.txt

Output:
./government/Env_Prot_Agen/bill.txt
```

This command searches in the government folder within technical for a file named bill.txt.

2. find -mtime 

find -mtime returns the path of all files that have been modified in the specified time condition in number of days. A **+** operator is used before the number of days to specify greater than and a **-** operator is used to specify less than. No operator specifies exact number of days. 

- Example 1:

Altering the chapter-1.txt file by adding a few characters and then running the following command produces the following output:

```
find ./911report -mtime -1

Output:
./911report/chapter-1.txt
```

- Example 2:

If we also alter the bill.txt file in Env_Prot_Agen and run the same command for the entire technical directory, we will get:

```
find . -mtime -1

Output:
 ./government
./government/.DS_Store
./government/Env_Prot_Agen/bill.txt
./911report/chapter-1.txt
```

So, the command can be useful to see if other files change when you make changes to a certain file. 

- Example 3:

Bounds can also be applies to the command:

```
find . -mtime +1 -mtime -5

#This command finds files that were modifed more than 1 day ago but less than 5 days ago. 

Output:
No output since there are no files int he directory that were altered more than 24 hours ago. 
```

3. find -size

find -size finds files in a directory that are related to a specified size. The same + and - operators can be used as in mtime to specify greater than and less than, while the unit for file size is specified after the number. A couple of examples are k for kb and G for Gb. 

- Example 1: 

If we needed to search for files in the technical directory that are larger than 200 kb, we would use the following command:

```
find . -size +200k

Output:
./government/About_LSC/commission_report.txt
./government/Env_Prot_Agen/bill.txt
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
./government/Gen_Account_Office/d01591sp.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-3.txt
```

- Example 2:

Bounds can be applied to this command as well. In order to search for files that are larger than 150 kb but smaller than 200 kb, we would use the followoing command:

```
find . -size +150k -size -200k

Output:
./government/Env_Prot_Agen/multi102902.txt
./government/Env_Prot_Agen/tech_adden.txt
./government/Gen_Account_Office/pe1019.txt
```

- Example 3:

What if we tried a larger unit of file size? 

```
find . -size +1G 

# The above command searches for files that are larger than 1 gigabyte. 

Output:
No output since there are no files in the directory that are larger than 1 gigabyte. 
```