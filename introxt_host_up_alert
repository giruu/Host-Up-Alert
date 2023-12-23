#!/bin/bash

# Clear the terminal for a clean output
clear

# Display the Introxt logo (assuming it's in a subdirectory named "Logo")
cd Logo && ./introxt_logo && cd ..

# Gather user input for credentials and message recipient
echo "Enter Mobile Number: "
read mobileNo
echo "Enter Password: "
read password
echo "Enter The Number Which Will Receive The Message: "
read num

# Function to extract a value from a string using a regular expression
function extract_value() {
  grep -oP "$1" | head -1
}

# Login to Way2SMS and extract authentication token
session_cookie=$(curl -i 'https://www.way2sms.com/re-login' \
  -H 'Accept: */*' \
  -H 'Referer: https://www.way2sms.com/' \
  -H 'Origin: https://www.way2sms.com' \
  -H 'X-Requested-With: XMLHttpRequest' \
  -H 'User-Agent: Mozilla/5.0' \
  -H 'Content-Type: application/x-www-form-urlencoded; charset=UTF-8' \
  --data "mobileNo=$mobileNo&password=$password&CatType=&redirectPage=&pid=" \
  --compressed -o /dev/null -w '%{cookie_header}')
token=$(extract_value 'JSESSIONID=([^;]*)' <<< "$session_cookie")

# Get hostname for message content
hostname=$(hostname)

# Send the SMS message
curl -i 'https://www.way2sms.com/smstoss' \
  -H "Cookie: $session_cookie" \
  -H 'Origin: https://www.way2sms.com' \
  -H 'Accept-Encoding: gzip, deflate, br' \
  -H 'Accept-Language: en-US,en;q=0.9' \
  -H 'User-Agent: Mozilla/5.0' \
  -H 'Content-Type: application/x-www-form-urlencoded; charset=UTF-8' \
  -H 'Accept: */*' \
  -H 'Referer: https://www.way2sms.com/send-sms' \
  -H 'X-Requested-With: XMLHttpRequest' \
  -H 'Connection: keep-alive' \
  --data "Token=$token&message=Introxt $hostname is up&toMobile=$num&ssaction=undefined&senderId=WAYSMS" \
  --compressed -o /dev/null

# Check for successful message delivery and provide feedback
if [ $? -eq 0 ]; then
  echo "Message Successfully sent"
else
  echo "Failed to send message"
fi
