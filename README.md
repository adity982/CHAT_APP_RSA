# CHAT_APP_RSA
1. app.py - Client-Side Chat Application

Description:

The app.py file represents the client side of the chat application. This is the script that users will execute to connect to the chat server and communicate with other users in real-time. It makes use of TCP sockets for establishing a connection to the server and RSA encryption for secure messaging.

Upon running app.py, the user will:

    Enter their username.
    Exchange RSA public keys with the server.
    Send and receive messages in a secure, encrypted format.

Functionality:

    Connection: The client connects to the server using the server's IP address and port.
    Encryption: The client's public key is shared with the server, and messages are encrypted using the recipient’s public key before being sent.
    Decryption: Incoming messages are decrypted using the client’s private key.
    Real-Time Messaging: The client listens for incoming messages while allowing users to type and send new ones.

How to Use:

    Run app.py and provide the server IP and port to connect.
    Enter your username and begin chatting securely.

Sample Commands:

bash

python3 app.py

2. socket_server.py - Server-Side Chat Application

Description:

The socket_server.py file is responsible for managing the server-side operations of the chat application. It listens for incoming client connections, handles multiple clients simultaneously using threads, and relays messages between clients.

The server performs the following actions:

    Accepts connections from multiple clients.
    Receives RSA public keys from clients to facilitate encrypted communication.
    Broadcasts messages between connected clients, ensuring that only the intended recipient can decrypt them.

Functionality:

    Multi-Client Support: The server uses threading to handle multiple clients at once, allowing real-time communication between all connected users.
    Key Management: It stores each client’s public key and username, enabling secure messaging between users.
    Broadcasting: Messages are sent securely, ensuring the proper delivery to the intended recipient.
    Connection Handling: The server ensures that if a client disconnects, other users are notified, and the connection is cleanly closed.

How to Use:

    Run socket_server.py to start the server on the specified IP and port.
    Clients can then connect using their respective app.py files.

Sample Commands:

bash

python3 socket_server.py

Application Flow:

    Start the Server: The chat server is started by running socket_server.py. It will listen for incoming connections on the specified IP and port.

    Connect the Clients: Users run app.py to connect to the server. Each client will:
        Send their username and public key to the server.
        Receive public keys from other clients for encryption purposes.

    Messaging: Once connected, clients can send encrypted messages to each other. The server facilitates the secure transfer of these messages.

    Decryption: Each client decrypts incoming messages using their private key, ensuring only the intended recipient can read the message.

Security:

This chat application uses RSA encryption to secure communications. Messages are encrypted using the recipient’s public key, and only the recipient's private key can decrypt them. This ensures that messages remain private even if intercepted.
Example of Running the Application:

    Start the server:

    bash

python3 socket_server.py

Start the client (from another terminal or machine):

bash

    python3 app.py

    Example of Encrypted Communication:
        User A sends a message to User B.
        The message is encrypted using User B’s public key and relayed through the server.
        User B decrypts the message with their private key, and User A cannot decrypt it.

This structure allows for a secure, multi-client chat experience with end-to-end encryption using RSA, which ensures that only intended recipients can access the message contents.

