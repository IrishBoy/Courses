**Let’s Talk About NTP (Network Time Protocol)**  
Ever wondered how computers stay in sync with time? That’s where NTP comes in. It’s one of the internet’s oldest tricks, created way back in 1981 by David Mills, a professor at the University of Delaware. It’s super reliable, scalable, and gets the job done when it comes to time synchronization.

### **How Does NTP Keep Time?**

Here’s the gist of it:

1. Your device (the client) sends a time request to a time server.
2. The server sends back the time, and the client adjusts its clock accordingly.
3. This happens a few times (like six exchanges over 10 minutes) to lock in the right time.

Once that’s done, your device checks in every 10 minutes or so to stay accurate. The magic happens over UDP (User Datagram Protocol) using port 123. NTP even allows multiple devices to sync up through broadcasts.

### **Stratum Levels – The Time Pyramid**

Think of time syncing as a hierarchy, starting with the most accurate source:

- **Stratum 0:** These are the “time gods” like atomic clocks or GPS systems.
- **Stratum 1:** Devices directly connected to Stratum 0 clocks.
- **Stratum 2:** Devices that get their time from Stratum 1.
- **Stratum 3:** You guessed it—these sync from Stratum 2.

The farther you go down the pyramid, the less accurate the time.
![[Network Time Protocol.png]]

### **NTPv4 – The Latest and Greatest**

The newest version, NTPv4, is super cool. It works with both IPv4 and IPv6, is backward-compatible with older versions, and is super accurate (down to a few microseconds). Plus, it has a nifty feature to find time servers automatically.

### **How Do Devices Get the Time?**

There are two main ways devices sync up:

- **Polling:** Devices ask specific servers for the correct time. This is super accurate and reliable.
- **Broadcasting:** Servers shout out the time to everyone listening. This method is quicker but not as precise.

### **What About SNTP?**

If full-blown NTP feels like overkill, there’s SNTP (Simple Network Time Protocol). It’s a lightweight version designed for less powerful devices that don’t need super precise time.