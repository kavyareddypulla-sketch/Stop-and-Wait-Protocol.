# Stop-and-Wait-Protocol.
## AIM
To write a python program to perform stop and wait protocol

## ALGORITHM
Start the program.
Get the frame size from the user
To create the frame based on the user request.
To send frames to server from the client side.
If your frames reach the server it will send ACK signal to client
Stop the Program

## PROGRAM
## client
```import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(('localhost', 8000))

while True:
    message = client.recv(1024).decode()
    print("Received from Client:", message)

    client.send("Acknowledgement Received".encode())

    if message.lower() == "exit":
        client.close()
        break
```
## server
```
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(('localhost', 8000))
server.listen(1)

print("Waiting for connection...")
conn, address = server.accept()
print("Connected:", address)

while True:
    data = input("Enter a data: ")
    conn.send(data.encode())

    if data.lower() == "exit":
        conn.close()
        server.close()
        break

    response = conn.recv(1024).decode()
    print("Client:", response)
```
##OUTPUT

CILENT
<img width="800" height="126" alt="image" src="https://github.com/user-attachments/assets/66f1bfbb-0294-4c4d-b963-e0d1b8f77272" />

SERVER
<img width="806" height="183" alt="image" src="https://github.com/user-attachments/assets/11add714-7a28-4a90-9d60-f35cc49b334a" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
