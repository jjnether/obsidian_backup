# Phenix Software

Created: 2022-03-18 10:58:13 -0500

Modified: 2022-05-12 13:37:36 -0500

---

-   Serial # 17-1836
-   Model # 6TC100-20



-   DTS has backup and restore data functions, allowing you to backup your tests and recipes, as well as restore those from a previous backup
-   There will be a history of all tests under the Test History tab. Here you can view/print the report or export the data into a .csv
-   I couldn't find an option for overcurrent or overvoltage, so that will have to be controlled on the Phenix test system itself
-   Custom Test seemed the most straightforward to setup; the Step test wasn't working as I expected it to, I can look into it further if I need to
-   The manual we have is slightly outdated with some of the options shown in the manual being missing
-   Can enter notes for a test
-   Can change data path (to a network drive)
-   Data logger just keeps a log of everything based on a set interval
    -   C:ProgramDataPhenixDIEnetExcel.csv (example)







Operator steps (other than normal)

-   On Phenix system, hit view menu (bottom right) and set to remote control
-   Open Software (DTS)
-   Under Test Results, fill out fields (Test ID, Operator, Sample ID)
-   Under Test Recipes, select the recipe "128kV 1m"
-   Hit Run Test
-   Select time interval, then 1 sec interval, then hit ok
-   On the Phenix system, press output ON to begin test
-   Under Test Results, hit Save Test
-   Under Test History, select test and hit Report (may need to sort by date/time on the left)
-   Sign the printed report
-   Repeat for each test (Closed gap, OG z-side, OG y-side)

Connect to database?



![Machine generated alternative text: Data Path: This setting determines where DTS data files are located. For instance, you can change this setting to move your DTS data to a network server. You are responsible for moving the data files. If you change this setting without moving the files, DTS will create empty data files in the new location. ](Quick-Notes-Phenix-Software-image1.png){width="10.708333333333334in" height="0.90625in"}![Machine generated alternative text: #0077c8 RG8 o, 119, 200 100%, 41%, 0%, 22% 204', 100%, 78% HSL 204% 100%, ](Quick-Notes-Phenix-Software-image2.png){width="10.125in" height="5.979166666666667in"}

List of questions to ask Phenix?

-   Fix A to mA on graph
    -   Emailed about it



![Machine generated alternative text: O RG8 116, 170, 80 32%, 53%, 33% #74aa50 96', 53%, 67% HSL goa , 36%, ](Quick-Notes-Phenix-Software-image3.png){width="9.375in" height="5.489583333333333in"}



