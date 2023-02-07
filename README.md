# mfa-cscs-access


The repository contains a simple Python script [cscs-keygen.py] and a shell script [cscs-keygen.sh] which can be used as command line tool for fetching public and private keys signed by CSCS'S CA after authenticating using MFA. You can then use those keys to ssh to CSCS'login nodes.

For using the python script, these are the steps:

- git clone <repo>
- cd <repo>
- pip install virtualenv (if you don't already have virtualenv installed)
- virtualenv venv to create your new environment (called 'venv' here)
- source venv/bin/activate to enter the virtual environment
- pip install -r requirements.txt to install the requirements in the current environment
- <s>python cscs-keygen.py</s>

<s>For using the shell script, these are the steps:

- git clone <repo>
- cd <repo>
- bash cscs-keygen.sh</s>

To setup the username and password, make the following change:

- modify **cscs-keygen.py**, and replace the python in the first line with the exact version you want to run (normally in a virtualenv)

Run this python and set the username, password, and TOTP.

    import keyring
    keyring.set_password('cscs-keygen','username','YOUR-CSCS-USERNAME')
    keyring.set_password('cscs-keygen','password','YOUR-CSCS-PASSWORD)
    keyring.set_password('cscs-keygen','TOTP','YOUR-CSCS-MFA-TOKEN')

On OS/X you can set this up to run nightly:

- edit the **path** and **username** to **cscs-keygenn.py** inside **cscs-key.plist**.
- optionally change **StartCalendarInterval**. This only runs if you are logged on or after waking from sleep.
- copy **cscs-key.plist** to **~/Library/LaunchAgents/** to run every night.

For other any other OS refer to the scheduler documentation (e.g. **cron**). For information on using keyring on other systems visit <https://pypi.org/project/keyring/>.