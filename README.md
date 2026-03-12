# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
# server
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
# client
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT

Server

<img width="632" height="246" alt="Screenshot 2026-03-12 135700" src="https://github.com/user-attachments/assets/fb0c7b86-00d2-4824-b22f-ae38c707f49e" />

Client

<img width="764" height="273" alt="Screenshot 2026-03-12 135651" src="https://github.com/user-attachments/assets/f1abc794-4749-43ea-b266-8befe9225ce8" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
