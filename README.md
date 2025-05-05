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
## CLIENT
```
import socket


client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect(("localhost", 12345))  # Connect to the server
print("Connected to the server. Type 'exit' to quit.")

while True:
    message = input("Client: ")
    client_socket.send(message.encode())

    if message.lower() == "exit":
        break

    response = client_socket.recv(1024).decode()
    print(f"Server: {response}")

client_socket.close()
```
## SERVER
```
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(("localhost", 12345))  # Bind to localhost and port 12345
server_socket.listen(1)  # Listen for one connection
print("Server is listening on port 12345...")

conn, addr = server_socket.accept()
print(f"Connection established with {addr}")

while True:
    data = conn.recv(1024).decode()
    if not data or data.lower() == "exit":
        print("Client disconnected.")
        break
    print(f"Client: {data}")
        
    response = input("Server: ")
    conn.send(response.encode())

conn.close()
server_socket.close()
```
## OUPUT

![Screenshot 2025-05-05 104237](https://github.com/user-attachments/assets/e2c63d6e-2229-4138-995f-4f6482f52e58)

![Screenshot 2025-05-05 104301](https://github.com/user-attachments/assets/33a3de11-93c1-45b9-a39b-ec3a881be89e)

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
