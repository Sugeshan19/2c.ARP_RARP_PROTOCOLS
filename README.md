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
```python
Client

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
```python
Server

import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
````
## OUPUT - ARP
<img width="857" height="267" alt="2c op" src="https://github.com/user-attachments/assets/1ebcdeee-e92d-465e-898e-a625177d0dda" />
<img width="863" height="302" alt="2c op1" src="https://github.com/user-attachments/assets/4cb54d55-231b-4075-9fa7-6af993c572d8" />

## PROGRAM - RARP
```python
Client

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
````
```python
Server

 
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
<img width="866" height="248" alt="image" src="https://github.com/user-attachments/assets/7b2fc2b5-6b67-41c1-84ba-96ba4196afe6" />

<img width="866" height="323" alt="image" src="https://github.com/user-attachments/assets/4de7934b-119c-4920-b6f2-ff2d66c8d3ff" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
