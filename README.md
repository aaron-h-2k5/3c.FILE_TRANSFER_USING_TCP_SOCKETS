# Ex-3c CREATION FOR FILE TRANSFER USING TCP SOCKETS
## Register Number: 212223040001
## Name: H. AARON
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
### Client:
```
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
### Server:
```
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
    filename='mytext.txt'
    f = open(filename,'rb')
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
## OUTPUT
### Client:
<img width="936" alt="Screenshot 2024-04-18 at 7 05 16 PM" src="https://github.com/aaron-h-2k5/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144250957/9040d3bf-a336-41e4-8508-55777767efa3">

### Server:
<img width="936" alt="Screenshot 2024-04-18 at 7 05 06 PM" src="https://github.com/aaron-h-2k5/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144250957/c20f8bb0-6719-4bb1-9871-a2c471a26686">

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
