TAsk 00
user browser searches on ww.footbar.com on the cache.
if it is not found, it moves into DNS Server which looks up into A record and translate it to an IP Adress.
after that it goes to the web serve using TCP/IP over port 80 (HTTP) or 443 (HTTPS) with an request which the web server handles it with a response.
this response might retrieve queries from database via application server into HTML template as dynamic or it would be just a static html page handled by NGINX server directly.
the web browser recieves the respone and displays the content to the end user.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
the server is whether a computer or a software that has multiple services that handle clients requests.
the Domain Name is responsible for translating the names into IP adresses.
www is subdomain to footbar domain
the web server recieves a html request and handle it then send a response.
the application server is python code handles the dynamic html pages by retrieving from database and make operations on them if needed and send them back to webserver.
the database is storing the required data of a system and retrieved when needed to the application server.
the server is using TCP/IP over HTTP/HTTPS to comunnicate with the user computer.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
the challenges with this infrastructure are:
SPOF (Single Point of Faliure):
if server fails whole application is down.
Downtime during maintenance:
restarting the websites or deploying code causes temporary outage.
Scalability Limits:
one server can't handle large ammount of traffic or load.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Task 01:
The load balancer is added to direct requests into the destinated server via it's algorithms e.g. Round Robin.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Task 02:
There 3 fireWalls added and one more server.
The first firewall (The Perimeter Firewall) to block attacks before the traffic reaches the Load Balancer.
The second one (DB firewall) prevents app hosts from being used as a pivot to the DB by attackers.
the third (Host Firewall DB) extra protection layer for the most sensitive host.
Monotring Clients used to collect logs, metrics, traces and forward them to Sumo Logic (or similar) so you can observe health, performance, errors
1) Why terminating SSL at the load balancer level can be an issue?
it can cause risk if internal network is not fully trusted.
2) Why having only one MySQL server capable of accepting writes is an issue?
it will cause write and read failure, data loss if there is no data replication.
3) Why servers with all the same components (DB, web, app) might be a problem?
DB is I/O heavy; running it alongside web/app processes will compete for CPU/memory/disk, reducing performance.