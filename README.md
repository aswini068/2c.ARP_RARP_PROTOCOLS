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
## CLIENT:
```
CLIENT: 
 import socket
s=socket.socket()
s.bind(('localhost',8880))
s.listen(5)
c,addr=s.accept()
address={"192.168.144.56":" AC:50:DE:1B:DE:65"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

```
## SERVER:
```
SERVER:
import socket
s=socket.socket()
s.connect(('localhost',8880))
while True:
    ip=input("Enter Logical Address:")
    s.send(ip.encode())
    print("MAC address",s.recv(1024).decode())
```

## OUPUT - ARP
## CLIENT:
![image](https://github.com/user-attachments/assets/1727243f-744b-4902-a8b6-0b5181e4fdc3)

## SERVER:
![image](https://github.com/user-attachments/assets/defe34c2-fe61-4d75-a853-41397410c444)

## PROGRAM - RARP:
## CLIENT:
```
CLIENT: 
 
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
## SERVER:
```
SERVER: 
 
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP:
## CLIENT:
![image](https://github.com/user-attachments/assets/79c64b58-8dd0-448c-b2b7-82ada1488f83)

## SERVER:
![image](https://github.com/user-attachments/assets/75f14944-e9d1-4bd1-b7ee-8fc4251af5c6)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
