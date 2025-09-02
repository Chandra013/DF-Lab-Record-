# Experiment-3: Password Capturing Using Wireshark

**Course / Lab:** Digital Forensics Lab  
**Experiment No.:** 3  
**Title:** Password Capturing Using Wireshark  


---

## Aim
To capture and analyze network packets using Wireshark.

---

## Requirements
- Wireshark  
- Windows  
- Active internet connection or local network traffic  

---

## Description
Wireshark is a popular open-source network protocol analyzer.  
It allows forensic investigators and security analysts to:  
- Capture live network traffic  
- Inspect packet contents (headers & payloads)  
- Filter and search packets (e.g., HTTP, DNS, TCP, ICMP, ARP)  
- Detect suspicious or malicious activity  
- Reconstruct sessions (e.g., HTTP requests, TCP streams)  

---

## Procedure — Steps to Capture and Analyze Passwords

**Step-1:** Open Wireshark. You will see different network interfaces. Select the network that is connected (e.g., Wi-Fi).  


![(images/exp3-step1.png)](https://github.com/Chandra013/DF-Lab-Record-/blob/6db05094e136e61eb7f17c3dcca55d37819e8fbd/Images/WhatsApp%20Image%202025-09-02%20at%2010.34.15%20AM.jpeg)


**Step-2:** On the top right corner, click the blue shark fin button. Wireshark begins capturing live traffic and packets appear in real-time.  

![(images/exp3-step2.png)](https://github.com/Chandra013/DF-Lab-Record-/blob/6db05094e136e61eb7f17c3dcca55d37819e8fbd/Images/WhatsApp%20Image%202025-09-02%20at%2010.34.16%20AM.jpeg)

**Step-3:** After starting packet capture, go to a website and log in with credentials.  

![(images/exp3-step3.png)](https://github.com/Chandra013/DF-Lab-Record-/blob/6db05094e136e61eb7f17c3dcca55d37819e8fbd/Images/WhatsApp%20Image%202025-09-02%20at%202.17.53%20PM.jpeg)

**Step-4:** Return to Wireshark and apply filters like **HTTP** to find HTTP packets on the network.  

![(images/exp3-step4.png)](https://github.com/Chandra013/DF-Lab-Record-/blob/6db05094e136e61eb7f17c3dcca55d37819e8fbd/Images/WhatsApp%20Image%202025-09-02%20at%2010.34.17%20AM.jpeg)

**Step-5:** Some HTTP packets will be captured. We specifically look for **form data** that the user submitted to the website.  
- We have main two methods used for submitting form data from web pages like login forms
to the server. They are ‘GET’ & ‘POST’
  

**Step-6:** To check credentials in requests sent via the **GET method**, apply this filter:  
- http.request.method == "GET"
  
![(images/exp3-step6.png)](https://github.com/Chandra013/DF-Lab-Record-/blob/6db05094e136e61eb7f17c3dcca55d37819e8fbd/Images/WhatsApp%20Image%202025-09-02%20at%2010.34.20%20AM.jpeg)

**Step-7:** If credentials are not found with GET, apply the **POST method filter**:  
- http.request.method == "POST"

![(images/exp3-step7.png)](https://github.com/Chandra013/DF-Lab-Record-/blob/6db05094e136e61eb7f17c3dcca55d37819e8fbd/Images/WhatsApp%20Image%202025-09-02%20at%2010.34.26%20AM.jpeg)

As you analyze the HTML form in POST requests, you can view user credentials (e.g., username and password).  
Example:  
- Form item: "uname" = "chandra"
- Form item: "pass" = "1234"
