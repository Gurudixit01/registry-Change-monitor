Windows Registry Change Monitoring System
Overview
The Windows Registry Change Monitoring System is a cybersecurity project designed to monitor critical Windows Registry locations, detect suspicious modifications, generate alerts, and create detailed reports for security analysis.

The project focuses on identifying malware persistence techniques, unauthorized registry modifications, and security-related configuration changes.

Features
Monitor Windows Registry autorun locations
Create registry baseline snapshots
Perform registry integrity verification
Detect added, modified, and deleted registry values
Detect malware-like registry behavior
Generate real-time alerts
Create CSV-based analysis reports
Continuous monitoring at configurable intervals
Project Structure
src/
├── cli.py
├── config.py
├── detector.py
├── monitor.py
├── registry.py
├── reporting.py
└── __init__.py

data/
logs/
tests/
Requirements
Windows Operating System
Python 3.8+
Administrator privileges (recommended)
Install dependencies:

pip install -r requirements.txt
Running the Project
Step 1: Create Baseline Snapshot
Generate an initial registry snapshot that will act as the trusted baseline.

python -m src.cli baseline
Output:

data/baseline.json
The baseline stores the current state of monitored registry keys.

Step 2: Verify Registry Integrity
Compare the current registry state with the saved baseline.

python -m src.cli check
The system will identify:

Added values
Modified values
Deleted values
Step 3: Start Real-Time Monitoring
Launch the registry monitoring engine.

python -m src.cli monitor
The monitor performs the following operations:

Reads all configured registry keys.
Captures a snapshot of the current registry state.
Waits for the configured polling interval.
Captures a new snapshot.
Compares both snapshots.
Detects additions, modifications, and deletions.
Generates alerts and log entries.
Default monitoring interval:

10 Seconds
Step 4: Generate Analysis Report
Generate a detailed CSV report from recorded monitoring events.

python -m src.cli report
Output:

logs/registry_report.csv
The report includes:

Timestamp
Registry Path
Registry Value Name
Action Type
Previous Value
New Value
Severity Level
Detection Reason
Monitored Registry Locations
Autorun Keys
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce
HKLM\Software\Microsoft\Windows\CurrentVersion\Run
HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce
Security Related Keys
HKLM\SOFTWARE\Policies\Microsoft\Windows Defender
HKLM\SYSTEM\CurrentControlSet\Services\SharedAccess
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System
Project Workflow
Registry Keys
      │
      ▼
Snapshot Collection
      │
      ▼
Baseline Creation
      │
      ▼
Continuous Monitoring
      │
      ▼
Change Detection
      │
      ▼
Malware Behavior Analysis
      │
      ▼
Alert Generation
      │
      ▼
Report Generation
Module Description
registry.py
Responsible for:

Reading registry keys
Creating snapshots
Loading baseline data
Saving baseline data
monitor.py
Responsible for:

Continuous monitoring
Snapshot comparison
Event generation
detector.py
Responsible for:

Detecting suspicious changes
Identifying persistence mechanisms
Security configuration analysis
Severity classification
reporting.py
Responsible for:

Processing monitoring events
Generating CSV reports
Exporting security findings
config.py
Responsible for:

Registry path configuration
Monitoring interval configuration
System settings
cli.py
Provides command-line functionality:

baseline
check
monitor
report
Example Test
Start monitoring:

python -m src.cli monitor
Create a test registry value:

HKCU\Software\Microsoft\Windows\CurrentVersion\Run

Name:
RegistryMonitorTest

Value:
C:\Windows\System32\notepad.exe
Wait for the next monitoring cycle.

Expected Result:

New registry value detected
Alert generated
Event logged
Report entry created
Project Objectives Achieved
✅ Monitor autorun registry keys for persistence mechanisms

✅ Detect malware-like registry changes

✅ Create a registry integrity checker using baseline comparison

✅ Provide real-time or scheduled alerts on modifications

✅ Generate detailed registry change reports for analysis

Conclusion
The Windows Registry Change Monitoring System provides continuous monitoring of critical registry locations, detects suspicious modifications, alerts users about unauthorized changes, and generates detailed reports for security analysis. The project helps improve system security by identifying registry-based persistence mechanisms and potential malware activity.