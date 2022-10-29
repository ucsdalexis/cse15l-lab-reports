## Week 5 Lab Report 3

### 3 Command-line Options for `find`

1. `-name` <br />
This command-line option, `-name`,  recurrsively looks through the indicated folder for files who's pathname match the specified pattern. It's useful if you want to find and search for files or a file within a large folder. 

#### Example 1

```
local skill-demo1 % find ./technical -name "chapter*.txt"
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-1.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-9.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
```

In this example, `find` recursively searched through the technical directory and looks for texts files that start with the word "chapter" and have any pattern after. It's useful to be able to find files with a specific starting pattern. 


#### Example 2

```
local skill-demo1 % find ./technical -name "*rr*.txt"
./technical/government/Media/Terrorist_Attack.txt
./technical/government/Media/Barr_sharpening_ax.txt
./technical/biomed/rr73.txt
./technical/biomed/rr74.txt
./technical/biomed/rr171.txt
./technical/biomed/rr167.txt
./technical/biomed/rr166.txt
./technical/biomed/rr172.txt
./technical/biomed/rr37.txt
./technical/biomed/rr196.txt
./technical/biomed/rr191.txt
```

In this example, `find` recursively searched through the technical directory and looks for texts files that have the phrase "rr" in the filename at all. It's useful to be able to find files with a specific saying you are looking for. 


#### Example 3

```
local skill-demo1 % find ./technical -name "*report*"
./technical/government/About_LSC/Progress_report.txt
./technical/government/About_LSC/Strategic_report.txt
./technical/government/About_LSC/Special_report_to_congress.txt
./technical/government/About_LSC/commission_report.txt
./technical/government/About_LSC/reporting_system.txt
./technical/911report
```

In this example, `find` recursively searched through the technical directory and looks for pathnames that have the phrase "report" in the name at all. It's useful to be able to find files and directories with a specific phrase you are looking for. 


---


2. `-type`  <br />
This command-line option, `-type`, recurrsively looks through the indicated folder for files who have the specified type.

#### Example 1

```
local skill-demo1 % find ./technical -type d
./technical
./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Gen_Account_Office
./technical/government/Post_Rate_Comm
./technical/government/Media
./technical/plos
./technical/biomed
./technical/911report
```

In this example, `find` recurrsively looked through the indicated folder for pathnames who have the specified type and in this case, `-type d` finds all the directories. This is useful if you are just looking for directories. 


#### Example 2

```
local skill-demo1 % find ./technical -type f
./technical/government/.DS_Store
./technical/government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
./technical/government/About_LSC/Progress_report.txt
./technical/government/About_LSC/Strategic_report.txt
./technical/government/About_LSC/Comments_on_semiannual.txt
./technical/government/About_LSC/Special_report_to_congress.txt
./technical/government/About_LSC/CONFIG_STANDARDS.txt
./technical/government/About_LSC/commission_report.txt
./technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt
./technical/government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
...
./technical/911report/chapter-8.txt
./technical/911report/preface.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
```

In this example, `find` recurrsively looked through the indicated folder for the type of just regular files and the `...` represents the rest of the files to save space. This is useful if you just want to look for files. 


#### Example 3

```
local skill-demo1 % find ./technical -type f -name "*report*"
./technical/government/About_LSC/Progress_report.txt
./technical/government/About_LSC/Strategic_report.txt
./technical/government/About_LSC/Special_report_to_congress.txt
./technical/government/About_LSC/commission_report.txt
./technical/government/About_LSC/reporting_system.txt
```

In this example, `find` recurrsively looked through the indicated folder for regular files and the with the phrase "reports" in the file name. This is useful if you want to look for spcifically files with a specific phrase. 

---


3. `-size`  <br />
This command-line option, `-size`, recurrsively looks through the indicated folder for files who fit in the specified size range. 

#### Example 1

```
local skill-demo1 % find ./technical -size +150k
./technical/government/About_LSC/commission_report.txt
./technical/government/Env_Prot_Agen/multi102902.txt
./technical/government/Env_Prot_Agen/bill.txt
./technical/government/Env_Prot_Agen/tech_adden.txt
./technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
./technical/government/Gen_Account_Office/pe1019.txt
./technical/government/Gen_Account_Office/d01591sp.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-3.txt
```

In this example, `find` recurrsively looked through the indicated folder for files and directories that are bigger than 150 kilobites. This is useful if you want to look for files that are bigger than an indicated size. 


#### Example 2

```
local skill-demo1 % find ./technical -size -1k 
./technical
./technical/government
./technical/government/About_LSC
./technical/government/Env_Prot_Agen
./technical/government/Alcohol_Problems
./technical/government/Post_Rate_Comm
./technical/plos/pmed.0020191.txt
./technical/plos/pmed.0020226.txt
./technical/911report
```

In this example, `find` recurrsively looked through the indicated folder for files and directories that are smaller than 1 kilobite. This is useful if you want to look for files that are smaller than an indicated size. 


#### Example 3

```
local skill-demo1 % find ./technical -size +120k -size -130k
./technical/government/Env_Prot_Agen/ctm4-10.txt
./technical/government/Gen_Account_Office/d0269g.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-12.txt
```

In this example, `find` recurrsively looked through the indicated folder for files and directories that are bigger than 120 kilobites and smaller than 130 kilobites. This is useful if you want to look for files that are are in a specific size range. 