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
client:
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
print('Successfully got the file')
s.close()
print('connection closed')
```
server:
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

## OUPUT

### client

![319137118-d4bc70e9-1ec9-4530-914f-fb903ac76eb8](https://github.com/Prasanavausdevan/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870579/cc63add3-1c25-4bc2-9d9c-9257209a7c03)

### server

![319136893-7e85a4de-e427-47e3-b4d2-e91ba5aa3d7a](https://github.com/Prasanavausdevan/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870579/6851caee-2b57-4de2-beb3-3f8ae65daa19)



## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
