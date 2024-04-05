# 2c.SIMULATING ARP /RARP PROTOCOLS
Name: T. Gayathri Reg.No: 212223100007

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
## SERVER
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
## CLIENT
![Screenshot 2024-04-05 110944](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/149037327/460c800b-6d72-43e3-9a0b-bbe1b3df8aaf)

## SERVER
![Screenshot 2024-04-05 110938](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/149037327/f9c04c17-289a-4363-996b-cbcc87956dec)

## PROGRAM - RARP
## CLIENT
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
## SERVER
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
## CLIENT
![Screenshot 2024-04-05 111341](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/149037327/d7b50f56-697b-4819-b21a-c4a2bd61e7ee)

## SERVER
![Screenshot 2024-04-05 111332](https://github.com/NaliniG007/2c.ARP_RARP_PROTOCOLS/assets/149037327/6f65c611-4b76-40d7-92d5-4104ed5fc192)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
