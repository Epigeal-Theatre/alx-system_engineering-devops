this is my readme for the project 0x09-web_infrastructure_design

AUTHOR DANIEL ONYINKWA

Task 0: Basic Web Stack

What is a server? A server is a piece of hardware (computer), software (program), or device responsible for transmitting, storing, and receiving data, responding to clients through HTTP requests.

What is the purpose of a domain name? A domain name serves as the address for a specific website, aiding in locating website addresses via the internet protocol. Domain names are easier to recall compared to strings of numbers comprising IP addresses.

What type of DNS record is www in www.foobar.com? It is an A record. An A record links a domain to the physical IP address of the computer hosting that domain. Internet traffic utilizes the A record to locate the computer hosting your domain's DNS settings.

What role does the web server play? A web server is a computer responsible for storing, processing, and delivering website files to web browsers.

What is the function of the application server? An application server is designed to install, operate, and host applications.

What is the purpose of the database? The database stores all the information that users need to store.

How does the server communicate with the user's computer requesting the website? Web browsers and servers communicate using TCP/IP, with the Hypertext Transfer Protocol serving as the standard application protocol on top of TCP/IP, supporting web browser requests and server responses.

Single Point of Failure (SPOF): A single point of failure (SPOF) poses a potential risk in the event of a flaw. If a component of a system fails, it can halt the entire system's operation. Downtime is necessary for maintenance tasks like deploying new code, requiring the web server to be restarted. Since there is only one server, the system must be shut down for maintenance. Scaling becomes challenging if there is excessive incoming traffic, with no option to scale the service with additional backup servers. This can lead to potential breakdowns of the webpage and client requests exceeding server capacity.

Task 1: Distributed Web Infrastructure

Why are additional elements being added?

The new configuration comprises two master servers and one slave server. As the master servers will operate based on an Active-Active setup requiring identical configurations, every additional element needs to be added, akin to the simple web infrastructure in the previous scenario. Load management is facilitated through a load balancer using a Round Robin algorithm to distribute queries evenly. An additional server is necessary to serve as a replica or slave server, helping alleviate the load on the master servers when handling read queries.

What distribution algorithm is employed by your load balancer and how does it function?

My load balancer employs a Round Robin algorithm for distribution. This means that queries are sequentially distributed to each server, and after reaching the last server, the algorithm cycles back to the first. On average, this results in a roughly equal distribution of server load, approximately 50% each for the two-server configuration.

Is your load balancer configured for Active-Active or Active-Passive setup, and what is the difference?

My load balancer is configured for an Active-Active setup. In an Active-Active cluster, at least two nodes actively run the same services concurrently, aiming to balance the load by distributing tasks across different servers to prevent overloads. Conversely, an Active-Passive setup involves at least two nodes, but not all are actively serving at the same time. While one node is active, others (failover servers) remain passive until they are needed to serve as backup in case of the primary server's failure.

How does a database Primary-Replica (Master-Slave) cluster function?

A database Primary-Replica (Master-Replica) cluster replicates data from a master database server to one or more replica servers, ensuring that all users access the same data. This process creates a distributed database, enabling users to access data quickly without interference. Replication can be synchronous, where data is replicated to all replicas before client notification, or asynchronous, where data is replicated at the client's pace after confirmation.

What distinguishes the Primary node from the Replica node in terms of application?

The Primary node stores the "real" data and handles writing operations, while the Replica node only handles reading operations. This architecture aims to enhance site reliability by preventing overload on the Primary node with both reading and writing requests, particularly under heavy traffic.

Secured and Monitored Web Infrastructure

Why add each additional element?

Three Firewalls: The first firewall checks incoming requests and may deny subsequent ones based on rules. The second firewall operates on the server to prevent hacking attempts based on requests. The third firewall serves as a circuit-level firewall, inspecting information transactions.

SSL Certificate: An SSL certificate is added to secure HTTPS protocols, encrypting communication to prevent unauthorized access to plaintext, thereby enhancing the security of communication between browsers and web servers.

Why serve traffic over HTTPS?

Serving traffic over HTTPS utilizes the secure port 443, encrypting outgoing information to deter unauthorized access or surveillance, thereby enhancing site security.

What is the purpose of monitoring?

Monitoring ensures quality control, maintaining high standards, consistency, and performance improvements by identifying anomalies in data quality against predefined rules and metrics, triggering alerts for further investigation and correction.

How does the monitoring tool collect data?

IT monitoring comprises three components: Foundation (the lowest layer of the software stack, including physical and virtual devices), Software (analyzing device activity in terms of CPU usage, memory, etc.), and Interpretation (translating collected data into metrics presented through graphs or data charts).

How to monitor web server QPS?

Monitor Queries Per Second (QPS) to gauge server traffic rate, enabling decision-making regarding scalability to handle usage demands and resource requirements to prevent server overload.

What are Website KPIs?

Website Key Performance Indicators (KPIs) highlight customer behavior, SEO performance, and e-commerce website health.

Issues in Secured and Monitored Web Infrastructure

Why is terminating SSL at the load balancer level problematic?

Terminating SSL at the load balancer leaves data unencrypted between the load balancer and the App Server, potentially exposing applications to Man-in-the-Middle Attacks.

Why is having only one MySQL server capable of accepting writes problematic?

Relying on a single MySQL server for write operations poses risks due to the absence of automatic failover in case of the master node's failure.

Why might having servers with identical components pose a problem?

If servers with identical components fail simultaneously, website downtime may occur due to the entire stack combination being affected.
