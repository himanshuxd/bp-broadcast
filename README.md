# bp-broadcast
A simple Script to broadcast battery percentage from your Android device to the internet.

# Installation & Usage

First off install Termux and Termux-api apps from playstore on your device.

We make use of `git` `ruby` `termux-api` `jq` so we install all of those packages on termux next.

I was using `termux-battery-status | grep percentage | grep -oP '\: (.*?)\,' | grep -Eo '[0-9]{1,3}` to get battery percentage values previously but `jq` is an even more elegant method to parse json.

Install defunkter's gist by using `gem install gist` or any of the given methods in https://github.com/defunkt/gist login into your account and generate a token as instructed.

Once your done with above, place the `bp.sh` file in your home directory of termux using `git clone` and `mv` and generate a gist file for usage with the name you desire for usage with `bp.sh` replace those values in the script with the generated ones.

Apply suitable execution permissions for the script using `chmod +x bp.sh` and add it to your cronjob tasks using `cronjob -e` I run it every minute so it looks like :
`* * * * * ~/bp.sh`

Finally start the job using `crond` and make sure it is running using `pidof crond`

# Additional Information

In case you want this script to run automatically and even across restarts etc take a look at modifying `init.d` more information can be found here : https://stackoverflow.com/questions/16747880/how-to-use-crontab-in-android and https://wiki.termux.com/wiki/Termux:Boot 
