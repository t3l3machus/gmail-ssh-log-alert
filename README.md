## Scope
Fail2ban is dope and SSH is quite secure, but what if someone still manages to authenticate to your machine e.g. by using saved/harvested credentials? Receive email alerts on successful ssh logins based on a predefined IP whitelist OR a predefined IP country origin whitelist.  
**Essentially:** IF (ssh successful authentication ip address NOT IN ip whitelist) OR (ssh successful authentication ip address country of origin NOT IN country whitelist); then send email notification;

## Notification
![Notification example.png](https://i.ibb.co/550xtBv/logalert.png)

## Requirements
1. python3
2. `sudo apt install geoip-bin`
3. An existing or preferably a new and dedicated gmail account for sending the alerts. The account must be configured to accept Less secure app access (go to --> Manage your google account/Security/Less secure app access/turn on).

## Configuration
Edit the script and:
1. replace your gmail authentication data and recipient email address.
2. edit variables `country_whitelist` OR `ip_whitelist` to suit your needs.

## Usage
`sudo chmod +x ssh-log-alert.sh`  

There are two ways to use this script:
1. Simply run the script (as root) which will result in a live log of every succesfull ssh authentication as well as an indication of email alert trigger success/failure, when a condition is met (you should test it that way also).  
`./ssh-log-alert.sh`
2. Add script to the root crontab and have it run in the background when the machine starts:  
`crontab -e`  
then add line:  
`@reboot /bin/bash /path/to/ssh-log-alert.sh`  
reboot the machine and you are good to go (`reboot now`).

## Notes
Check [ssh-log-alert using mailgun](https://github.com/t3l3machus/ssh-log-alert) for a more secure and elegant version of this script.
