It is a system that allows clients to see the available seats for booking and book any of them as many times as required. It is a server client architecture, where server keeps all the record about the clients who have booked what seats till the time, and the current active clients booking(connected) etc. Server allows multiple clients to access the system and book the tickets using locks which allows data synchronization mechanism in the case of multiple clients trying to access the same data source. When client gets connected, displays a list of available seats and based on the seats selected by the client and server updates the available seats list and lets the client continue booking if required by client.

Modules
1. Server.py - it starts a server socket running on the host system and waits for clients to get connected. Once a client connects it starts a seperate thread to interact with the client. It sends a list of available seats to client and based on client's response it updates the list and sends it to all clients again for booking, notifying them about the change in the list of available seats. On closing system it prints the remaining seats and users and seats which are booked during the session

2. Client.py - it connects to specified host and port number and waits till receiving the initial list of available seats. Then it calls the ui module to display seats to user and take input. On receiving input(actually reads from file) from user it pads the data to make it 1024 bytes sends back data to server and waits for server's response. Which is stripped off to get only pure data and is displayed back to user.

3. ui.py - it is a simple ui created using tkinter library of python, which receives lists of available seats. Then writes the user input to a file and closes the window
