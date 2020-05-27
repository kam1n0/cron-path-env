# cron-path-env

*Credit to Tib3rius* | https://tryhackme.com/room/linuxprivesc

A given cron job runs a shell script overwrite.sh that does not have a specified directory path.

When the cron job runs and executes overwrite.sh, the system runs through the listed directories in the PATH variable.

This can be exploited if the user has writeable access to a directory listed before the directory where overwrite.sh is located.

1) View the contents of the system-wide crontab:

![Image of cron_tab](https://github.com/kam1n0/cron-path-env/blob/master/tmp_upload/crontab.png)

* Note the PATH variable starts with /home/user which is the current "user's" home directory.
* By placing an 'overwrite.sh' script in the /home/user directory, the system will run this malcious shell script instead of the original overwrite.sh.

2) Create a file named 'overwrite.sh' in the "user's" home directory with the following contents:

![Image of bin_bash](https://github.com/kam1n0/cron-path-env/blob/master/tmp_upload/bin_bash.png)

3) Make overwrite.sh executable:

![Image of overwrite](https://github.com/kam1n0/cron-path-env/blob/master/tmp_upload/overwrite.png)

4) Wait for the cron job to run then execute '/tmp/rootbash -p' to gain a shell running with root privileges:

![Image of rootbash](https://github.com/kam1n0/cron-path-env/blob/master/tmp_upload/rootbash.png)
