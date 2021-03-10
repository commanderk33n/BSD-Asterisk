# BSD-Asterisk
create a asterisk VoIP-Server in FreeBSD

1. Install Asterisk<br>
   ```pkg install asterisk13```<br>
   ```/usr/local/etc/rc.d/asterisk start```<br>
   check if server is running:<br>
   ```ps ax | grep asterisk```<br>
   run server automatically on startup:<br>
   ```nano /etc/rc.conf```<br>
   add the following line:<br>
   ```asterisk_enable="YES"```<br>
3. Initial Configuration
  
5. 
