# backup_iptables
It is useful if you want to keep a backup of your existing iptables rules and it's very useful option if you want a backup the current iptables rules prior to make any changes on it.
Here is an Ansible playbook which gives you an idea about ‘how to backup existing iptables rules‘ into a text file with hostname server, and copy iptables backup to "your local system".

***To save a file with the server name, you must first enter the server's IP address and name server in the /etc/hosts file of your system.

If anything happened wrongly while editing the iptables rules we can simply restore the backup and lift the iptables as a working one.
```
# iptables -L -nv --line-number 
Switches:
L -> List rules
n -> List rules with port number
v -> verbose mode
--line-number -> List rules with rule number
```
Chain INPUT (policy ACCEPT 80 packets, 5562 bytes)
num pkts bytes target prot opt in out source destination
1 0 0 ACCEPT tcp -- * * xx.xx.xx.xx 0.0.0.0/0 tcp dpt:22
2 0 0 ACCEPT tcp -- * * xx.xx.xx.xx 0.0.0.0/0 tcp dpt:25
3 0 0 ACCEPT tcp -- * * xx.xx.xx.xx 0.0.0.0/0 tcp dpt:80
4 0 0 ACCEPT tcp -- * * xx.xx.xx.xx 0.0.0.0/0 tcp dpt:110
5 0 0 ACCEPT tcp -- * * xx.xx.xx.xx 0.0.0.0/0 tcp dpt:143

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
num pkts bytes target prot opt in out source destination

Chain OUTPUT (policy ACCEPT 60 packets, 10834 bytes)
num pkts bytes target prot opt in out source destination
```
1. iptables-save (Save current/existing rules to a file)
2. iptables-restore (Restore back the saved rules from the file)
```
