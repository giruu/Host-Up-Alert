**SMS Automation Script**

This script automates the process of sending SMS messages using the Way2SMS service. It gathers user input for credentials and the message recipient, logs in to Way2SMS to obtain an authentication token, constructs a message with the system's hostname, sends the message to the specified recipient, and provides feedback on the delivery status.

**Prerequisites**
* Bash (Bourne Again SHell)
* cURL (Client for URLs) command-line tool

**Usage**
Clone the repository:


```bash
git clone https://github.com/your-username/sms-automation.git
```
Navigate to the cloned directory:

```bash
cd sms-automation
```
Run the script:
```bash
./sms-automation.sh
```
Follow the on-screen instructions to input your mobile number, password, and the recipient's number.

After sending the message, check the terminal for the delivery status.
