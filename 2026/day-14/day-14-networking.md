**OSI layers (L1–L7) vs TCP/IP stack (Link, Internet, Transport, Application)**
      OSI(Open system Interconnection) is the theoritical concept of how the network works and consists of seven layers but only in theory.
      Now the practical implementation of it was done and it is called TCP/IP and this is implemented in four layers.

**Where IP, TCP/UDP, HTTP/HTTPS, DNS sit in the stack----- TCP/OSI** 
      IP      -----> Layer 3/5 (Internet Layer)
      TCP/UDP -----> Layer 2/4 (Transport Layer)
      HTTP/HTTPS ---> Layer 1/7 (Application Layer)
      DNS ----------> Layer 4/1 (Network Access/Physical layer)

**Hands-on Checklist**
1.Identity: hostname -I (or ip addr show) — note your IP.
  ip-172-31-43-236(Private IP)
  
2.Reachability: ping <target> — mention latency and packet loss.
  73 packets transmitted, 72 received, 1.36986% packet loss, high latency 175ms
  
3.Path: traceroute <target> (or tracepath) — note any long hops/timeouts.     ##Latency = Time 
    Long hop: hop 5 -> hop 6 increased from ~30 ms to ~190 ms                 1–10 ms = very fast, 20–50 ms = good
      Timeouts: hops 8 and 9 did not respond                                  100+ ms = noticeable delay, 300+ ms = slow
 
4.Ports: ss -tulpn (or netstat -tulpn) — list one listening service and its port.
    0.0.0.0:80  , nginx
    0.0.0.0:22  , sshd
    
5.Name resolution: dig <domain> or nslookup <domain> — record the resolved IP.
  www.trainwithshubham.com. 300   IN      CNAME   graphyssl.com.
  graphyssl.com.          60      IN      A       152.42.156.175 (Revolved IP is the mapped DNS address)
  graphyssl.com.          60      IN      A       146.190.8.92
  
6.HTTP check: curl -I <http/https-url> — note the HTTP status code.
  curl -I  www.trainwithshubham.com
  HTTP/1.1 301 Moved Permanently
  
7.Connections snapshot: netstat -an | head — count ESTABLISHED vs LISTEN (rough).
  1 Established , 7 Listening

8. Which command gives you the fastest signal when something is broken?
   ping Host reachable or not, Latency, Packet loss
   dig helps check DNS issues
   curl -I helps check whether the web server responds
   traceroute helps locate where the path breaks
   
10. What layer (OSI/TCP-IP) would you inspect next if DNS fails? If HTTP 500 shows up?
    Network Access Layer , Application layer (HTTP error)
    
12. Two follow-up checks you’d run in a real incident.
    Will look up the layer where the error is arising from and executing the command accordingly
    


