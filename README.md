# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
Server
```
import socket
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(('localhost', 9999))
server.listen(1)

print("Server waiting for connection...")

conn, addr = server.accept()
print("Connected to", addr)

file = open("sample.txt", "rb")
data = file.read()
conn.sendall(data)

print("File sent successfully")

file.close()
conn.close()
server.close()
```
Client
```
import socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(('localhost', 9999))

file = open("received.txt", "wb")

while True:
    data = client.recv(1024)
    if not data:
        break
    file.write(data)

file.close()
print("File received successfully")

file = open("received.txt", "r")
content = file.read()
print("File Content:")
print(content)

file.close()
client.close()
```
## OUPUT
Server

<img width="591" height="195" alt="image" src="https://github.com/user-attachments/assets/72149e6a-6e71-4b8f-b011-24d05fc02cf7" />

Client

<img width="624" height="182" alt="image" src="https://github.com/user-attachments/assets/2836578e-857d-449d-ad1d-13ba8e628f34" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
