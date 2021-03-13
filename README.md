# Script to generate playtime reports using Autorank backups

This script is made to format Autorank backups into an easy to read format.  

### EXAMPLE

In the examples/ directory in this repository, there are fake backups, userdata files and the output files which this script generated.  

### HOW TO USE

Run `pip install -r requirements.txt` before continuing.  
Modify the .env file in this directory and change the values to the proper locations for your setup.  You can then run the command, it'll run on the latest files.  
I would recommend scheduling your server to take a backup a bit before midnight, and having this script run when it's done. This script will automatically check if it should create reports other than the daily one.  
If the day is a saturday, the script will also generate a weekly report. If it is the last day of the month, it will generate a monthly report.  

You can also manually force it to generate a specific report by passing "Daily", "Weekly", "Monthly" or "Total" to the script, like so:  
`./format-report.py Weekly`  

### HOW IT WORKS

This script reads the latest backup from autorank starting with the time period you want. Per line it goes through every UUID and looks these up in the Essentials userdata directory to get the username. It then formats the minutes played into a human readable format. It stores these in a list which is sorted and then written to a file.  