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
```
import socket 

s = socket.socket() 

s.bind(('localhost',8000)) 

s.listen(5) 

c, addr = s.accept() 

address = {
    "165.165.80.80":"6A:08:AA:C2",
    "165.165.79.1":"8A:BC:E3:FA"
}

while True: 
    ip = c.recv(1024).decode() 
    
    try: 
        c.send(address[ip].encode()) 
        
    except KeyError: 
        c.send("Not Found".encode())
```
SERVER:
```
import socket 

s = socket.socket() 

s.connect(('localhost',8000)) 

while True: 
    ip = input("Enter logical Address : ") 
    
    s.send(ip.encode()) 
    
    print("MAC Address :", s.recv(1024).decode())
```

## OUPUT - ARP

CLIENT:

<img width="941" height="948" alt="image" src="https://github.com/user-attachments/assets/280f1fea-f9d0-40ce-9b45-fe4bb2c64981" />

SERVER:

<img width="1100" height="963" alt="image" src="https://github.com/user-attachments/assets/c811af92-0c0a-4691-9fd2-4aa11e76446a" />


## PROGRAM - RARP

CLIENT:
```
import socket 

s = socket.socket() 

s.bind(('localhost',9000)) 

s.listen(5) 

c, addr = s.accept() 

address = {
    "6A:08:AA:C2":"192.168.1.100",
    "8A:BC:E3:FA":"192.168.1.99"
}

while True: 
    ip = c.recv(1024).decode() 
    
    try: 
        c.send(address[ip].encode()) 
        
    except KeyError: 
        c.send("Not Found".encode())
```
SERVER:
```
import socket 

s = socket.socket() 

s.connect(('localhost',9000)) 

while True: 
    ip = input("Enter MAC Address : ") 
    
    s.send(ip.encode()) 
    
    print("Logical Address :", s.recv(1024).decode())
```
## OUPUT -RARP

CLIENT:

<img width="943" height="964" alt="image" src="https://github.com/user-attachments/assets/1cebc484-7a1f-445b-a196-48917d0a872d" />

SERVER:

<img width="946" height="931" alt="image" src="https://github.com/user-attachments/assets/5fd08002-93f3-42bc-b7a1-8169677901a2" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
