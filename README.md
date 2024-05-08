# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
### NAME: S ADITYA
### REG NO: 212223040007
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM:
### SERVER:
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
### CLIENT:
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
## OUTPUT:
### SERVER:
![image](https://github.com/arbasil05/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144218037/a259761e-9f14-4535-b863-0b9eaa19f9db)
### CLIENT: 
![image](https://github.com/arbasil05/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144218037/738dda1d-9af9-4ca0-b41a-ef136b568c9f)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
