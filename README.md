# Windows Registry Change Monitoring System
 
## Overview
A Windows Registry monitoring tool that detects unauthorized registry modifications, persistence mechanisms, and suspicious security-related changes.
 
## Features
- Monitor Run and RunOnce registry keys
- Baseline snapshot creation
- Registry integrity checking
- Real-time change monitoring
- Malware-like behavior detection
- Alert generation
- CSV report generation
 
## Project Structure
 
src/
- cli.py
- config.py
- detector.py
- monitor.py
- registry.py
- reporting.py
 
## Installation
 
pip install -r requirements.txt
 
## Usage
 
Create baseline:
 
python -m src.cli baseline
 
Check integrity:
 
python -m src.cli check
 
Start monitoring:
 
python -m src.cli monitor
 
Generate report:
 
python -m src.cli report
 
## Monitored Registry Locations
 
- HKCU\Software\Microsoft\Windows\CurrentVersion\Run
- HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce
- HKLM\Software\Microsoft\Windows\CurrentVersion\Run
- HKLM\Software\Microsoft\Windows\CurrentVersion\RunOnce
 
## Output
 
- Baseline snapshot
- Registry change logs
- Detection alerts
- CSV analysis reports