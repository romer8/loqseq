- Connect to Windows
  id:: 624f0859-51e8-4a92-88a2-20ecc64bdf67
  background-color:: #497d46
  ```bash
    xfreerdp /f /u:USERNAME /p:PASSWORD /v:HOST[:PORT]
  ```
  
  In this command:
  
  /f is option means to open the remote desktop in full screen mode
  /u:USERNAME is a name of the account on the computer to which we are connecting
  /p:PASSWORD is a password of the specified account
  /v:HOST[:PORT] is an IP address or name of the computer to which the remote table is connected. PORT optional (recommended: “Windows Computer