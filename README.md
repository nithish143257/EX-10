# EX-10 APPLICATION USING TCP SOCKETS - FILE TRANSFER PROGRAM
## DATE : 11-05-2023
## AIM :
#### To write a python program for creating File Transfer using TCP Sockets Links.
## ALGORITHM :
#### 1.Start the program.
#### 2.Get the frame size from the user.
#### 3.To create the frame based on the user request.
#### 4.To send frames to server from the client side.
#### 5.If your frames reach the server, it will send ACK signal to client otherwise it will sendNACK signal to client.
#### 6.Stop the program
## CLIENT PROGRAM :
```PY
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s', (data))
        if not data:
            break
        f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
## SERVER PROGRAM :
```PY
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    f = open('received_file','rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()

```
## SERVER OUTPUT :
![Screenshot 2023-05-28 182654](https://github.com/MOHAMEDROSHAN5/EX-10/assets/121704588/7c0886e1-18b1-46d2-b688-6a4622aa153b)
## CLIENT OUTPUT : 
![Screenshot 2023-05-28 182704](https://github.com/MOHAMEDROSHAN5/EX-10/assets/121704588/ac4cb51e-d67f-4fd6-90f1-02ba738013ee)
## RECEIVED FILE : 
![Screenshot 2023-05-28 183017](https://github.com/MOHAMEDROSHAN5/EX-10/assets/121704588/0b9f6941-40c0-4142-8cff-2f8e6f3b4ad0)
# RESULT:
#### Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
