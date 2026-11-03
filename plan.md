# DataForge 
  
This is a CLI tools which helps data analyst to automated some repeatative task as well as help to faster ship there code with the help of DataForge.

Features:
1) Data Processing: Loading DataSets to Check rows, columns, missing values, duplicate value. 
> Responsible for: 
- showing the provided data summary
- outline those Data points across the whole data set
Input: admin@DataForge: <file> <"User Query">
Output: 
if ("Error Occurs")then 
-    <<file>-err.json> Saved in .dataforge directory
     print(<<file>-err.json>\n this is the DataSet Error Summary)
fi
else
-    print(Data Is Already Cleaned)
     print(This is the DataSet Summary(Explaining the given data set))

DataSet Summary: This is a function in which we are sending the file as a argument and this returns us summary of that file irrespective of its a *-err.json file or a Dataset which is already cleaned.


2) Data Cleaning: Fixing Missing values, Standarizing Dates/text,handling and revising those errored data points.
> Responsible for:
- Cleaning the DataSet
- Make Data Ready for Performing Analysis
Input: admin@Dataforge: <file> -ef <*-err.json> <"user query">
Output: Fields Changes file summary <update-file.json> followed by this asked for apply these changes or not (y/N): if yes then change that respective <file> and Save the <update-file.json> in .dataforge
: if no then just save the <update-file.json> in .dataforge in both after wards print the action.

3) Database SetUp: Automating the whole database setup by giving user query in string and taking outputs as SQL queries and applied by performing prompt(yes) and Writing those shell scripts which are responsible to send data files to databases.
> Responsible for:
- Managing Database
- Writing Scripts for Automating data files traveling
Input: admin@Dataforge: -f "<file>" "<Query>" 
Output: asks for executing the suggested queries and if queries applied then .log file of changes in .dataforge   

4) DashBoard Setup: Creating Streamlit layout write code in python(streamlit) for managing dashboards by UI.
> Responsible for:
- Creating Automatic DashBoards of Python(streamlit)
Input: admin@Dataforge: -f "<file>" "<Query>"
Output: after asking for the filename giving to that streamlit file saved that file in current directory and run that streamlit file and at the end print("CheckOut the Dashboard on URL: http://localhost|<public-ip>:port/dashboard") 


- RBAC
 Two types of roles categoried: (Name)Adm, Only (name) for Analyst
 roles only created by when Admin Allows 
 Any Deletion Command is ONLY performed by ADMINS.
 
- Own Database
 Dataforge Having its own SQLdatabase on Docker Container with persistent Volumes Enabled
 And for Users use it Having Another Docker Container of SQLDatabase 
- -y prompting
 In the Queries where Agent Have to Ask from user wheather to excute further for Any thing or not in those senerios if user used -y flag so every query is executes without having user Permission
- about .dataforge/
 .dataforge divide in to 4 parts 
 - error log files 
 - updation/changes log files in data cleaning process
 - SQL Queries Executed Log files
 - About DataForge