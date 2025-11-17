# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:

To implement a program to illustrate the mechanism of sliding window protocol.

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client.
6. Stop the Program.
## PROGRAM:

### CLIENT:
```python
import socket
s = socket.socket()
s.bind(('localhost',8002))
s.listen(5)
c, addr = s.accept()
ListSize = int(input("Enter the number of frames to send : "))
List = list(range(ListSize))
WindowSize = int(input("Enter Window Size : "))
st, i = 0, 0
while True:
    while(i < ListSize):
        st += WindowSize
        c.send(str(List[i:st]).encode())
        Acknowledgment = c.recv(1024).decode()
        if Acknowledgment:
            print(Acknowledgment)
            i+=st
```

### SERVER:
```python
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
```
## OUPUT:

### CLIENT:

<img width="780" height="280" alt="client" src="https://github.com/user-attachments/assets/b20eaa55-ae28-4513-a93c-b2499708bacf" />

### SERVER:

<img width="783" height="238" alt="server" src="https://github.com/user-attachments/assets/6773eb7d-6ec3-46a8-bd2a-919d5be5c987" />

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed.
