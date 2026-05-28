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
## PROGRAM - ARP:

Server_ARP.py:

```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c, addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2", "165.165.79.1":"8A:BC: E3:FA"};
while True:
        ip=c.recv(1024).decode()
        try:
                c.send(address[ip].encode())
        except KeyError:
                c.send("Not Found".encode())
```

Client_ARP.py:

```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
        ip=input("Enter logical Address : ")
        s.send(ip.encode())
        print("MAC Address", s.recv(1024).decode())
```

## OUPUT - ARP:

Server_ARP.py:

<img width="1912" height="973" alt="server2c(1)" src="https://github.com/user-attachments/assets/a2b47668-7655-4224-9e7e-b0cc958ea4b3" />

Client_ARP.py:

<img width="1918" height="966" alt="client2c(1)" src="https://github.com/user-attachments/assets/69e6f0f6-0b34-4a63-b346-edc9416db410" />

## PROGRAM - RARP:

Server_RARP.py:

```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100", "8A:BC: E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

Client_RARP.py:

```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address", s.recv(1024).decode())
```

## OUPUT -RARP:

Server_RARP.py:

<img width="1919" height="960" alt="server2c(2)" src="https://github.com/user-attachments/assets/f6fb5feb-bb66-4b8c-8daa-f34e0b13fd6e" />

Client_RARP.py:

<img width="1912" height="970" alt="client2c(2)" src="https://github.com/user-attachments/assets/0d8da5c6-4a1e-4254-a7e9-5c985646fad1" />

## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
