# mfa-cscs-access


The repository contains a simple Python script [cscs-keygen.py] and a shell script [cscs-keygen.sh] which can be used as command line tool for fetching public and private keys signed by CSCS'S CA after authenticating using MFA. You can then use those keys to ssh to CSCS'login nodes.

For using the python script, these are the steps:

- git clone <repo>
- cd <repo>
- pip install virtualenv (if you don't already have virtualenv installed)
- virtualenv venv to create your new environment (called 'venv' here)
- source venv/bin/activate to enter the virtual environment
- pip install -r requirements.txt to install the requirements in the current environment
- python cscs-keygen.py

For using the shell script, these are the steps:
- git clone <repo>
- cd <repo>
- bash cscs-keygen.sh

To setup the username and password, modify cscs-keygen.py, and replace the Python in the first line with the exact version you want to run (normally in a virtualenv)
Run this python and set the username, password and TOTP

import keyring
keyring.set_password('cscs-keygen','username','YOUR-CSCS-USERNAME')
keyring.set_password('cscs-keygen','password','YOUR-CSCS-PASSWORD)
keyring.set_password('cscs-keygen','TOTP','YOUR-CSCS-MFA-TOKEN')

On OS/X, edit path inside cscs-key.plist and copy to ~/Library/LaunchAgents to run every night.
