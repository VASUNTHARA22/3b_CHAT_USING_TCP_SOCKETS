# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
client:
```
import socket

HOST = '127.0.0.1'  # same as server
PORT = 5000

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((HOST, PORT))
print(f"Connected to server at {HOST}:{PORT}")

try:
    while True:
        # Send message to server
        message = input("Client: ")
        client_socket.sendall(message.encode())
        # Receive reply from server
        data = client_socket.recv(1024).decode()
        print(f"Server: {data}")
finally:
    client_socket.close()

```
server:
```
import socket

HOST = '127.0.0.1'  # localhost
PORT = 5000         # change if needed

# Create a TCP socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind the socket to address and port
server_socket.bind((HOST, PORT))

# Start listening for incoming connections
server_socket.listen(1)
print(f"Server listening on {HOST}:{PORT}...")

conn, addr = server_socket.accept()
print(f"Connected by {addr}")

try:
    while True:
        # Receive message from client
        data = conn.recv(1024).decode()
        if not data:
            break
        print(f"Client: {data}")
        # Send reply
        reply = input("Server: ")
        conn.sendall(reply.encode())
finally:
    conn.close()
    server_socket.close()

```
## OUTPUT
<img width="1571" height="1117" alt="image" src="https://github.com/user-attachments/assets/0da89d17-0758-4bd7-b7c8-6a51e8755079" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
