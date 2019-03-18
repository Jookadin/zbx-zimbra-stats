# zbx-zimbra-stats
Zabbix Template and script for monitoring Zimbra statistics (traffic and stats)

## Template

Uses two scripts to populate item:  

 * zimbraTrafficStats.sh - Script using /opt/zimbra/common/bin/pflogsumm.pl
   * userparameter_zimbra.traffic.conf - Zabbix UserParameter  
 * zimbraGetStats.sh - Script using /opt/zimbra/bin/zmsoap and zabbix_sender
    * crontab.txt - cron configuration

## Scripts

Grabs info from these providers (Zimbra related tools):  

 * /opt/zimbra/bin/zmsoap -z -t admin GetServerStatsRequest  
 * /opt/zimbra/common/bin/pflogsumm.pl
 
## Prerequisites

 * zabbix_sender
 * Grant the zabbix user sudo permissions to execute /opt/zimbra/common/bin/pflogsumm.pl
 * Replace Hostname in cron line to monitored hostname (has to match in Zabbix).
 
## Screens
![alt_text](https://github.com/GOID1989/zbx-zimbra-stats/blob/master/stats.png)
![alt_text](https://github.com/GOID1989/zbx-zimbra-stats/blob/master/traffic.png)

## HOWTO 

1. Import Template Zimbra Statistics.xml on the Zabbix Server.
2. Copy all files to the monitored host.
3. Copy userparameter file into the includes folder (Default: /etc/zabbix/zabbix_agentd.d/)
4. Copy the script files into your Zabbix folder (Default: /etc/zabbix)
   1. Make sure the scripts are executable.
   2. Optional: create a scripts directory inside /etc/zabbix/
5. Grant the zabbix user sudo permissions to execute /opt/zimbra/common/bin/pflogsumm.pl
   1. Make sure that the zabbix user can use passwordless sudo.
6. Add the line from crontab.txt to the end of the zimbra users crontab.
   1. Remember to change the hostname.

## Notes

There's nothing here yet. :)
