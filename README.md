# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP
```
Developed by: Rougith D
Register No: 212225220087
```
## Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"169.254.13.175":"70:68:71:53:4E:21"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```

## Server 
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

```

## OUPUT - ARP
<img width="1739" height="256" alt="{B74C2839-138A-4989-984F-F1D2C61D8CCE}" src="https://github.com/user-attachments/assets/bfad56f6-100a-4527-a32e-d6d67ddf8af1" />

## PROGRAM - RARP
## Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"70:68:71:53:4E:21":"169.254.13.175"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```

## Server 
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())

```
## OUPUT -RARP
<img width="1691" height="259" alt="{DA5711DF-B3A2-44FA-9922-B378CD61C7D5}" src="https://github.com/user-attachments/assets/41170d68-d3a7-4048-aff2-b0627b88e44b" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
