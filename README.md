Read Me File for Intrusion Detection Log File 
Features:
1.	Log Monitoring: Continuously monitors a specified log file for new entries.
2.	Pattern Matching: Searches for pre-defined suspicious patterns using regular expressions.
3.	Alert on Detection: Prints an alert message if a suspicious line is detected in the log file.
Usage:
1.	Replace LOG_FILE_PATH with the path to the log file you want to monitor (e.g., /var/log/syslog, /var/log/auth.log).
2.	Add or modify the SUSPICIOUS_PATTERNS list with keywords or regex patterns relevant to your use case.
3.	Run the script with sufficient permissions to read the log file (Meaning you will need file Permissions for the folders you are setting parameters for). Below is how you will run the bash script. 
bash
sudo python3 intrusion_detection.py
Notes:
•	The script is meant to be simplistic in how it will function and the commands used. It can be extended with features like email alerts, logging to a separate file, or integration with other security tools.
•	Ensure that your user has the necessary permissions to read the log file.
•	Use regular expressions carefully to avoid missing any suspicious entries.
 
1. Python Environment
•	The script is written in Python, the user will need to have python downloaded into text editor.
•	Recommended version: Python 3.7 or later.
Check Python version:
bash
python3 --version
Install Python:
•	On Ubuntu/Debian: sudo apt-get install python3
•	On MacOS: Install Python using Homebrew: brew install python
•	On Windows: Download the installer from the Python website.
2. Permissions to Access Log Files
•	The script requires read access to the log file being monitored.
•	For system logs (e.g., /var/log/auth.log), the script must be run with elevated privileges (e.g., sudo on Linux).
Example:
bash
sudo python3 intrusion_detection.py
3. Regular Expressions Module
•	The re module is used in the script for pattern matching and is a built-in Python library. No additional installation is required.
4. Text Editor or IDE (Optional)
•	A text editor like VS Code, Sublime Text, or even Nano/Vi can be used to edit the script.
•	For easier debugging, an IDE like PyCharm or VS Code is recommended.
5. Dependencies
•	No external Python libraries are used in this script, so no need for pip to install additional packages.
6. Log File Location
•	The user must know the exact path to the log file they want to monitor (e.g., /var/log/auth.log).
•	If the log file does not exist or the path is incorrect, the script will not work.
Verify log file access:
bash
sudo cat /var/log/auth.log
 
Optional Enhancements:
If you wish to extend the script with additional features, you might need to install additional libraries:
•	For Email Notifications: smtplib (built-in module) or third-party libraries like yagmail.
•	For File Monitoring: Libraries like watchdog can be used for more efficient log monitoring.
