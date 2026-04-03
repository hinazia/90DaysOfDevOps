**Task 1: DNS – How Names Become IPs**
1.Explain in 3–4 lines: what happens when you type google.com in a browser?
  Browser asks DNS resolver where is google.com. It sends the query to Root server.
  The root server says, asks .com server. In turn it says asks the Authoritative Server.
  Which has the mapped IP of google.com and hence Resolver returns IP to Browser. (Dia on pg 10 of notes)
  
2.What are these record types? Write one line each:
A, AAAA, CNAME, MX, NS
  A- The record which holds the IP addresses of the domain (usually IPv4)
  AAAA- contains the IPv6 address for the domain
  CNAME - Forwards one domain or subdomain to another, Does NOT provide an IP address
  MX - Directs mail to an EMail server
  NS - Stores the name of servers for DNS entry
3.Run: dig google.com — identify the A record and TTL from the output
  A - 127.0.0.53 , TTL - 62


  **Task 2: IP Addressing**
1.What is an IPv4 address? How is it structured? (e.g., 192.168.1.10)
  It is like an address of computers/devices to identify each other. IPv4 uses 4 numbers seperated by dots
  
2.Difference between public and private IPs — give one example of each
  Public IP - Routable on internet. Use on Internet. eg. web servers
  Private IP - Routable only inside the company and not on internet or defined network (LAN). eg databases
  
3.What are the private IP ranges?
  10.x.x.x, 172.16.x.x – 172.31.x.x, 192.168.x.x
  
Run: ip addr show — identify which of your IPs are private
    172.31.43.236/20

**Task 3: CIDR & Subnetting**

1.What does /24 mean in 192.168.1.0/24?
  24 means the number of IP addressses that will be created.
  
2.How many usable hosts in a /24? A /16? A /28?
  /24 256, /16 65,536, /28 16
  
3.Explain in your own words: why do we subnet?
  Subnets are created because it helps in the performance and security of the network but also a large of IP addresses becomes
  avaiable to be assign to the devices. Division of IP addresses becomes easy.
  
Quick exercise — fill in:
CIDR	Subnet Mask	        Total IPs	 Usable Hosts
/24	  255.255.255.0	         256         254    	      
/16	  255.255.0.0            65,536      65,534    
/28	  255.255.255.240        16          14

**Task 4: Ports – The Doors to Services**
What is a port? Why do we need them?
  Ports are the doors from where the services become available to the defined people or traffic. 
  Ports act like entry doors for data — the IP brings the data to the device, and the port directs it to the correct application.
  
**Document these common ports:**
Port	Service
22	   SSH
80	   HTTP
443	   HTTPS
53	   DNS
3306	 MySQL
6379	 TCP Redis
27017  TCP MongoDb

**Task 5: Putting It Together**
Answer in 2–3 lines each:

1.You run curl http://myapp.com:8080 — what networking concepts from today are involved?
  :8080 tells curl to connect to TCP port 8080 instead of the default HTTP port 80. 
  DNS resolution, my-app.com converting to IP address using DNS.
  TCP protocol
  
2.Your app can't reach a database at 10.0.1.50:3306 — what would you check first?
  Is my device IP allowed on the network or not. Since Databases can only be accsses through private IPs or over a private network,
  so I have to check whether my device IP has permisiion to access it or not

