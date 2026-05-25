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
P
## PROGRAM - ARP
## CLIENT
```
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()
address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## SERVER
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))
while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address", s.recv(1024).decode())
```
## OUPUT - ARP
## OUTPUT 1
<img width="1310" height="235" alt="ARP CLIENT" src="https://github.com/user-attachments/assets/629b619a-510e-4afd-81e5-037eba30a306" />

## OUTPUT 2
<img width="1247" height="228" alt="ARP SERVER" src="https://github.com/user-attachments/assets/96d097ef-25a1-4de3-888e-bed83c6fd0a9" />

## PROGRAM - RARP
## CLIENT
```
import socket
s = socket.socket()
s.bind(('localhost', 9000))
s.listen(5)
c, addr = s.accept()
address = {
    "6A:08:AA:C2": "192.168.1.100",
    "8A:BC:E3:FA": "192.168.1.99"
}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## SERVER
```
import socket
s = socket.socket()
s.connect(('localhost', 9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address", s.recv(1024).decode())
```
## OUPUT -RARP
## OUTPUT 1

<img width="1306" height="179" alt="RARP CLIENT" src="https://github.com/user-attachments/assets/25df2872-881b-42ba-9047-e3e0234a0fc8" />

## OUTPUT2

<img width="1235" height="210" alt="RARP SERVER" src="https://github.com/user-attachments/assets/bd20c8a9-c46b-4c14-b2c5-9bf8c8310c81" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
