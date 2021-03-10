# BSD-Asterisk
create a asterisk VoIP-Server in FreeBSD

1. Install Asterisk
   ```pkg install asterisk13```
   ```/usr/local/etc/rc.d/asterisk start```
   check if server is running:
   ```ps ax | grep asterisk```
   run server automatically on startup:
   ```nano /etc/rc.conf```
   add the following line:
   ```asterisk_enable="YES"```
3. Initial Configuration
  
5. 
