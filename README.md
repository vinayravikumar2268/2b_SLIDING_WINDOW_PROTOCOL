# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
~~~
client.py
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames:"))
l=list(range(size))
s=int(input("Enter window size:"))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
~~~
server.py
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknoledgement recieved from the server".encode())

~~~
## OUTPUT
client.py
<img width="1370" height="229" alt="image" src="https://github.com/user-attachments/assets/998867fa-5092-40bb-9cde-22553f635f3d" />
sever.py
<img width="1372" height="191" alt="image" src="https://github.com/user-attachments/assets/e7ceebf6-10b6-4edc-add7-8761fbe431ee" />




## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
