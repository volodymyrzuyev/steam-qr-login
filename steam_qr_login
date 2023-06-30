from cv2 import imread, QRCodeDetector
from os import popen, remove
from pyautogui import screenshot
from autoit import win_wait, win_activate
import argparse
import time

global path_to_steam
global steam_args

def parse_args():
    parser = argparse.ArgumentParser(
                    prog='account_opener',
                    description='Logs into accounts with supplied username using steamguard-cli. If multiple accounts are needed, set up steam to lunch in some sort of a sandbox',
                    usage='account_opener.py -p "path/to/steam.exe" -u username,username1,... -a "-args -for -steam"',)
    parser.add_argument("--usernames","-u", nargs="+",required=True,
                        help="Input a list of usernames (sperated by a camma nd) that you want logged in")
    parser.add_argument("--path", "-p", required=False,
                        help="Input the path to where steam.exe is located",default="C:\Program Files (x86)\Steam\\Steam.exe")
    parser.add_argument("--arguments", "-a", required=False,
                        help='Input option arguments for steam ex:"-applaunch 730 -silinet"',default="")
    
    global path_to_steam
    path_to_steam = parser.parse_args().path
    
    global steam_args
    steam_args = parser.parse_args().arguments
    
    return parser.parse_args().usernames

def start_steam():
    lunch_string = f'"{path_to_steam}" {steam_args} -login'
    popen(lunch_string)

def get_qr_link():
    win_wait("Sign in to Steam")
    time.sleep(3)
    win_activate("Sign in to Steam")
    screenshot().save(r'temp.png')
    data, _, _ = QRCodeDetector().detectAndDecode(imread('temp.png'))
    remove('temp.png')
    return data
    
def confirm_login(username, data):
    confirm_string = f'steamguard -u {username} qr-login --url {data}'
    popen(confirm_string)
    
def log_into_account(username):
    start_steam()
    data = get_qr_link()
    if data == "":
        print("test")
        log_into_account(username)
        return
    confirm_login(username,data)


username_list = parse_args()
for username in username_list:
    log_into_account(username)
