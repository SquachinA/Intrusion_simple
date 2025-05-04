# Script is built to monitor a log file for suspicious activity, such as unauthorized access attempts or failed login attempts.
# This script will read the log file line by line and check for specific patterns that indicate suspicious activity.
import os
import re

# This will define the log file to monitor, This can be any log file path
# For example, you can use "/var/log/auth.log" for authentication logs on Linux
LOG_FILE_PATH = "/var/log/auth.log"  # Replace with the path to your log file

# Define perameters of keywords or patterns to look for, this is set up for unauthroized access or failed login attems
SUSPICIOUS_PATTERNS = [
    r"failed login",
    r"unauthorized access",
    r"suspicious connection",
    r"brute force",
    r"denied"
]

# Function to monitor and analyze the log file, this will read the log file line by line and check for suspicious patterns.
# If you are monitoring a large log file, you can use the tail command to read the last few lines of the file.
def monitor_logs(file_path, patterns):
    if not os.path.exists(file_path):
        print(f"Error: Log file {file_path} does not exist.")
        return

    print(f"Monitoring log file: {file_path}")
    with open(file_path, "r") as log_file:
        # Seek to the end of the file, this will allow us to only read new lines added to the file,
        #  This is useful for large log files. If the file is large, we can skip to the end and only read new lines.
        log_file.seek(0, os.SEEK_END)
        
        try:
            while True:
                line = log_file.readline()
                if not line:
                    continue  # Wait for new log entries, this will allow us to read new lines added to the file.
                # If you want to read the entire file, you can remove this line and read the entire file.
                analyze_line(line, patterns)
        except KeyboardInterrupt:
            print("\nStopping log monitoring.")
        except Exception as e:
            print(f"An error occurred: {e}")

# Function to analyze a single line from the log file, this will check for the patterns and print alerts.
def analyze_line(line, patterns):
    for pattern in patterns:
        if re.search(pattern, line, re.IGNORECASE):
            print(f"Alert: Suspicious activity detected: {line.strip()}")
            break

if __name__ == "__main__":
    monitor_logs(LOG_FILE_PATH, SUSPICIOUS_PATTERNS)
