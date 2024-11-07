# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM:
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
P
## PROGRAM - ARP:
## Client-ARP:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## Server-ARP:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP:
## Client-ARP
![image](https://github.com/user-attachments/assets/8f204630-9def-4ecb-adbc-ae03927d3547)
## Server-ARP
![image](https://github.com/user-attachments/assets/09cffa8b-3f54-45a3-955f-ff611d641331)

## PROGRAM - RARP:
## Client-RARP:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## Server-RARP:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP:
## Client-RARP
![image](https://github.com/user-attachments/assets/00deff32-3e02-4968-a93e-bec283e1c89f)
## Server-RARP
![image](https://github.com/user-attachments/assets/537ae544-a13d-4007-be2c-c3a31fc4f638)

## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
