# steam-qr-login
A simple python script to log into steam desktop using the qr code. 
# Dependencies
* [opencv-python](https://pypi.org/project/opencv-python/)
* [pyautogui](https://pypi.org/project/PyAutoGUI/)
* [pyautoit](https://pypi.org/project/PyAutoIt/)
* [steamguard-cli](https://github.com/dyc3/steamguard-cli)

# Quickstart
* Download and set up your steam account with [steamguard-cli](https://github.com/dyc3/steamguard-cli)
* Move the *steamguard.exe* into the same folder as *steam_qr_login.py*
* Run the script and you are done!

# Usage
Command line options:
>| *Name* | *Optional* | *Default Value* | *Description* |
>|:------------------|:---|:---|:---|
>| `--usernames` <br> `(-u)` | **required** | `NONE` | A list of usernames you want to login as. All of these accounts must be set with [steamguard-cli](https://github.com/dyc3/steamguard-cli) before usage *Note: in order to log into multiple accounts at the same time you need steam.exe to start up in some sort of a sandbox.* |
>|`--path` <br> `(-p)` | **optional** | `C:\Program Files (x86)\Steam\\Steam.exe` | The path (enclosed in " ") to where *steam.exe* is located. |
>| `--arguments` <br> `(-a)` | **optional** | `""` | Arguments (in the form "arg0" "arg1" "arg2") that will be passed to *steam.exe* on startup with out the "-".

# Example:
`py steam_qr_login.py -u first_steam_account second_steam_account last_steam_account -p "C:\Program Files\games\Steam\steam.exe" -a "applaunch 730" "nochatui" "nofriendsui" "silent" "w 480" "h 360" "exec autoexec.cfg"`
                   
