# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program : 
client.py
```
import socket
# Create UDP socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
server_address = ("127.0.0.1", 15353)

# Get domain name from user
domain = input("Enter domain name: ")

# Send request to server
client_socket.sendto(domain.encode(), server_address)

# Receive response
ip_address, server = client_socket.recvfrom(1024)

print("IP Address:", ip_address.decode())

client_socket.close()
```
server.py
```
import socket

# DNS records (simulated database)
dns_table = {
    "google.com": "142.250.190.78",
    "yahoo.com": "98.137.11.163",
    "openai.com": "104.18.12.123",
    "example.com": "93.184.216.34"
}
# Create UDP socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

# Bind server to localhost and port
server_socket.bind(("127.0.0.1", 15353))

print("DNS Server running on port 5353...\n")

while True:
    # Receive domain request from client
    message, client_address = server_socket.recvfrom(1024)
    domain = message.decode()
    print("Request received for:", domain)
    # Check DNS table
    ip = dns_table.get(domain, "Domain not found")
    # Send response back to client
    server_socket.sendto(ip.encode(), client_address)
```
## OUTPUT :
<img width="1919" height="1021" alt="562041322-5de2df00-3ad3-4147-bf6d-3d1e246790a3" src="https://github.com/user-attachments/assets/b28b96c0-a904-4f7f-80b5-421cb485b02e" />


## Result 

Thus the socket for HTTP for web page upload and download created and Executed
