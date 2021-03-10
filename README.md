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
   location of the config-files:<br>
   ```/usr/local/etc/asterisk/```<br>
   basic sip.conf example:
   ```
   [general]
   context=unauthenticated ; default context for incoming calls
   allowguest=no ; disable unauthenticated calls
   srvlookup=yes ; enabled DNS SRV record lookup on outbound calls
   udpbindaddr=0.0.0.0 ; listen for UDP requests on all interfaces
   tcpenable=no ; disable TCP support

   [office-phone](!) ; create a template for our devices
   type=friend ; the channel driver will match on username first, IP second
   context=LocalSets ; this is where calls from the device will enter the dialplan
   host=dynamic ; the device will register with asterisk
   nat=yes ; assume device is behind NAT
   secret=zgb; a secure password for this device -- DON'T USE THIS PASSWORD!
   dtmfmode=auto ; accept touch-tones from the devices,
   negotiated automatically
   disallow=all ; reset which voice codecs this device will accept or offer
   allow=ulaw ; which audio codecs to accept from, and request to, the device
   allow=alaw ; in the order we prefer
   allow=all
   textsupport=yes
   [alice](office-phone)
   [bob](office-phone) 
   ```
   basic extension.conf example:
   ```
   [general]
   [LocalSets]
   exten => 99,1,VoiceMailMain()
   exten = 1337,1,Answer()
   same = n,Wait(1)
   same = n,Playback(hello-world)
   same = n,Hangup()

   exten = 2000, 1, Dial(SIP/alice)
   exten = 2001, 1, Dial(SIP/bob)
   ```
5. Monitoring<br>
   enter asterisk CLI
6. iax.conf<br>
