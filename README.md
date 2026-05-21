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
CLIENT:
~~~
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; 
while True: 
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode())
~~~
SERVER: 
~~~
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
~~~

## PROGRAM - RARP
CLIENT:  
~~~
import socket 
s=socket.socket() 
s.bind(('localhost',7000)) 
s.listen(5)
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}; 
while True:
    ip=c.recv(1024).decode() 
    try: 
        c.send(address[ip].encode()) 
    except KeyError: 
        c.send("Not Found".encode())
~~~
SERVER: 
~~~
import socket 
s=socket.socket() 
s.connect(('localhost',7000))
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address", s.recv(1024).decode())
~~~
## OUPUT 
CLIENT: 

<img width="509" height="178" alt="Screenshot 2026-05-21 140812" src="https://github.com/user-attachments/assets/c4efecee-10f1-4cb2-a492-39d50733a1b8" />

SERVER: 

<img width="976" height="443" alt="Screenshot 2026-05-21 140727" src="https://github.com/user-attachments/assets/40f3d732-4e42-4c6c-a4a7-4d7a1f9108da" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
