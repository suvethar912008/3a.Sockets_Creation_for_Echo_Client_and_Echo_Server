# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM
##Server
```
import socket

def echo_server():
    host = '127.0.0.1'
    port = 12345

    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
    server_socket.bind((host, port))
    server_socket.listen(1)

    print(f"Server listening on {host}:{port}")
    conn, addr = server_socket.accept()
    print(f"Connected by {addr}")

    while True:
        data = conn.recv(1024)
        if not data:
            break
        print("Server received:", data.decode())
        conn.sendall(data)

    conn.close()
    server_socket.close()

if __name__ == "__main__":
    echo_server()
## client
```
import socket

def echo_client():
    host = '127.0.0.1'
    port = 12345

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))

    while True:
        message = input("Enter message (type 'exit' to quit): ")
        if message.lower() == 'exit':
            break
        client_socket.sendall(message.encode())
        data = client_socket.recv(1024)
        print("Echo from server:", data.decode())

    client_socket.close()

if __name__ == "__main__":
    echo_client()

## OUPUT
Server:

<img width="362" height="208" alt="image" src="https://github.com/user-attachments/assets/f2013e8d-9770-4dbf-97c8-49b7198c1544" />

client:

<img width="412" height="271" alt="image" src="https://github.com/user-attachments/assets/bd4d84c9-e82b-40d2-9904-dafbeb69cd93" />

## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
