# Connect android device to openbsd using SSH

I recently switched to openbsd from arch linux after realising that it is the most robust and true unix.
However it sometimes fails short when it comes to connect new technologies like Android device. 
( Did try using simple-mtpfs. At-least I could not get it working )

So I found workaround using sshd

Commands 
* Check if sshd is already running.</br>
   ```unix
   ps -A | grep sshd
   ```
* enable sshd</br>
  ```unix
  sudo rcctl enable sshd
  ```
  </br> You should get reply something like this ```(sshd) ok ```
* start sshd</br>
  ``` sudo rcctl start sshd ```
* check if sshd is running
  ``` netstat -al | grep sshd ```
* know your ip
* install ftp client on android.
