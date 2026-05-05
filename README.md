# 3F: FIA Flight Following program
Potential alternative to crewman
3F is a flight following program for FIA in Interior Alaska. It is reformated from an original program called Crewman. It is using Excel to record, store and report data, and python (using python in excel add-in) to process the data.
This program runs exclusively online. You need an active internet connection to make it work.

## Structure:
The excel file has multiple sheets that are color coded:\
1- Green sheet(s): are edited on a daily basis.\
2- Purple sheet(s): are edited on a seasonal basis.\
3- Red sheet(s): are edited never.

On editable sheets (green and purple), not all cells are modifiable. Cells are blocked because (1) they already contain a formula that shouldn't be changed, or (2) are not included in the processing programs. If you try to edit a blocked cell, you'll receive a message like this: "This cell or chart you're trying to change is on a protected sheet [...]". Click OK and move to an editable sheet.

If for some reason, you need to unblock a sheet, contact me to learn how to.

As a general rule, all cells that are outline with a black border are editable.

## Data recording
### Seasonal datasheets (purple sheet)
ALL the tables mentioned bellow will have to be completed for the program to work. The largest table will likely be the plot table. Below, is a list of these required tables, and a description of their content.

1- the list of FIA plots that will be inventoried during the season is located in the sheet named "List_plots". Followind is the list of required and optional headers for this table, and their description.\
1.1- plot number	: FIA plot number\
1.2- county: Name of the county where the plot is located **[REQUIRED]**\
1.3- owner: name of the owner of the land where the plot is located **[REQUIRED]**\
1.4- plot latitude (decimal degree): ACTUAL latitude of the plot in decimal degree and WGS1984 projection **[REQUIRED]**\
1.5- plot longitude (decimal degree): ACTUAL longitude of the plot in decimal degree and WGS1984 projection **[REQUIRED]**\
1.6- landing zone latitude (decimal degree): latitude of the potential landing zone in degree (optional)\
1.7- landing zone longitude (decimal degree): longitude of the potential landing zone in degree (optional)\
1.8- elevation	: elevation at the plot in feet\

2- the list of hubs (main camps) that will be used during the season is located in the sheet named "List_hub". In this table, you'll need to list plot names and associated latitude and longitude in decimal degree and WGS1984 projection. 

3- the lists of crew leaders and crew members are located in the sheet named "List_crew_leaders" and "List_crew_members" respectively. In each table, list leads or members name and flight weight in pounds (i.e. fully clothed with flight attire one).

4- the list of helicopter managers is encoded in the sheet "List_helo_managers". Because a helicopter manager is rather a crew lead or a crew member, you just need to select the names in a drop-down list composed of all crew leads and members. You'll notice two greyed-out lists on the side of the main table: don't change or delete these lists.

5- the list of pilots is located in "List_pilots". You can list all pilots and optionally, their flight weight. NOTE that pilots weight in not included in the manifests (see below for more details).

6- the list of gears that are included during flights to and from plots are listed in the sheet "List_gears".\
6.1- Name: You'll list the typical set of gears that are brought in an helicopter on an inventory day.\
6.2- Number per ...: For every gear item listed, you'll indicate the number of unit typically needed per flight/ drop-off or passenger.\
6.3- Attribution: For every gear item, indicate its attribution: is the gear attributed to a flight (e.g. a sachel), to a drop-off (e.g. a bivi bag) or for a passenger (e.g. personal back-pack). The python code will computer the total load depending on the number of flights, drop-offs and passengers, so you don't have to do the math.\
6.4- Flight weight (lbs): [individual] gear weight (in pounds) will have to be set every season. 

7- the list of phones by color are listed in the sheet "List_phones". For each phone, please indicate associated color and number. 

### Daily datasheet (green sheet)
The only sheet to edit daily right now is named "Flight_inventory". This data table is organized in two part: the left part records flight information, and the right side includes information for every drop-off. The table can store data for up to ten flights. A flight can include up to 5 drop-offs. 

1- Flight information:\
1.1- Date: calendar date of the flight, e.g. 7/4/2026\
1.2- Hub: drop-down where you can choose the hub from where the helicopter will take off and come back.\
1.3- Flight number: don't edit - this is just a serial number.\
1.4- Pilot: select pilot's name from the drop-down table.\
1.5- Heli manager: select helicopter manager's name from the drop-down table.\
1.6- Going to the plot?: Indicate (yes/no) if the helicopter manager is planned to flight to the plot with the rest of the crew.\
1.7- Extra-weight?: Indicate any extra weight that has to be brought to the helicopter, and that is not listed in the fixed weight gears in the "List_gears" sheet (e.g. water jugs).\
1.8- Hazardous materials: List every haz. mat. that will be brought to the helicopter as part of the crew gears.\

2- Drop-off information:\
2.1- Drop-off number: don't edit - this is just a serial number.\
2.2- Plot number: select plot number that will be checked/inventoried from the drop-down list.\
2.3- Phone: Select the phone color that the team will take with them.\
2.4- Crew leader: Select the name of the crew lead for that crew from the drop-down list.\
2.5- Crew member 1-4: Select the name of the crew members that will compose the team for that crew from the drop-down list.\
2.6- Notes: anything that can be useful to appear in the daily schedule report.

## Reporting (red sheet)
Two reports are produced as part of this program: the daily schedule (stored in the Daily_Schedule sheet) and the manifest (stored in the Manifest sheet). These two reports are populated thanks to a python program that is stored in specific cells: the green cell located in [A4] in the Daily_Schedule sheet and in [A3] in the Manifest sheet.\
Once your completed a new data entry, you can run the python programs by clicking on the **"Reset"** item located in the Formulas menu / Python submenu. If you try to run the python code but lost your internet connection, you might get the error **#CONNECT!** visible in the green cells. When you recover your connection, retry to generate the report by clicking on **"Reset Runtime"** which is part of a drop-down menu within the reset item (Formulas -> Python -> Reset -> Reset runtime)



