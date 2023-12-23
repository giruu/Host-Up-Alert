**Mobile Messaging API**

This script automates the process of sending SMS messages using the Way2SMS API service. It gathers user input for credentials and the message recipient, logs in to Way2SMS to obtain an authentication token, manipulates the token so that server can accept it, constructs a message with the system's hostname, sends the message to the specified recipient, and provides feedback on the delivery status.

**Prerequisites**
* Bash (Bourne Again SHell)
* cURL (Client for URLs) command-line tool

**Usage**
Clone the repository:


```bash
git clone https://github.com/giruu/Mobile-Messaging-API.git
```
Navigate to the cloned directory:

```bash
cd Host-Up-Alert
```
Run the script:
```bash
./introxt_host_up_alert.sh
```
Follow the on-screen instructions to input your mobile number, password, and the recipient's number.

After sending the message, check the terminal for the delivery status.
