# 2c.SIMULATING ARP /RARP PROTOCOLS

## Name: ESWANTH KUMAR K
## REG NO: 212223040046

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
### CLIENT:
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

### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
	ip=input("Enter logical Address: ")
	s.send(ip.encode())
	print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
### CLIENT:
![image](https://github.com/Lokeshreddya31/2c.ARP_RARP_PROTOCOLS/assets/144870682/250d9af8-afd9-45cb-b00c-ff174991b986)

### SERVER:
![Screenshot 2024-04-29 213905](https://github.com/Lokeshreddya31/2c.ARP_RARP_PROTOCOLS/assets/144870682/331e5d85-d059-4d53-97cf-c33dfd7a4a98)

## PROGRAM - RARP
### CLIENT:
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

### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 	ip=input("Enter MAC Address : ")
 	s.send(ip.encode())
 	print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP
### CLIENT:
![Screenshot (39)](https://github.com/eswanth2005/2c.ARP_RARP_PROTOCOLS/assets/164656722/e422e8e7-57cf-4868-a49a-dc605a515c8d)

### SERVER:
![Screenshot (40)](https://github.com/eswanth2005/2c.ARP_RARP_PROTOCOLS/assets/164656722/6431b96f-64b9-4b57-a1f0-acbe8b1562ae)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
