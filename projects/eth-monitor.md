<h1>
    Project proposal update
</h1>

<h2>
    Ethereum Monitor 
</h2>

<h3>
    Motivation and project description
</h3>

As the Ethereum network scales through various L2 solutions and becomes more computationally complex, monitoring the overall health of the network will be increasingly important to detect and respond to network issues and attacks rapidly.

Previously, in May there was a 7-block reorg which took a considerable amount of time to distinguish whether it was a malicious attack or a client implementation issue. After some time, it was later noted that this was due to certain validators not simply upgrading their software (caused by the proposer boost fork upgrade). In such occurrences, an Ethereum Network monitoring tool could be very useful to automatically detect and send alerts when there are issues in the network. This could catalyse the time required to address system failures and attacks. In addition, by utilising ML models it would also be possible to anticipate potential issues ahead of time and provide warning signals when there happens to be unusual activity occurring in the network. 

At the current moment, there isn’t a monitoring system in place that captures and aggregates information about the overall health of the Ethereum Network from various client implementations. Hence, building a monitoring system to track network data as well as on-chain events could be beneficial. The main purpose of the monitoring tool is to be used to track network failures and attacks (such as reorgs) whilst also enabling devs and researchers to interact with the data through a UI for further research and analysis purposes.


<h3>
    Specification
</h3>

The platform where the Ethereum infrastructure will be monitored is through the ELK (Elasticsearch Logstash Kibana) stack. The stack is optimised for building big data pipelines and streaming log data from servers. The Kibana platform also makes it well suited for the project as the data can be queried and visualised easily through publically accessible web interface. 

To get the overall picture of the Ethereum network, it will be necessary to set up multiple nodes running on different consensus clients and conduct queries at the local level and global levels. The first queries that will be tracked and monitored will be local queries and in the second phase, global queries will be incorporated into the monitoring system.

A <b>local query</b> is a query processed between the tool and the beacon node. An example query would be detecting late blocks and attestation in real-time and also archiving the event stream data from the Beacon-API (such as block fullness, attestation and sync committee participation).

A <b>global query</b> is processed at a given central location and monitors performance across multiple nodes. An example query would be monitoring block latency across multiple nodes. This is to monitor and begin to estimate the network latency which can give further insight into the many small reorgs that occur.

In addition, monitoring the underlying server as well as the network traffic may be necessary to get a holistic view of how the servers are functioning when there are potential attacks (DoS attacks) and when the network gets congested (e.g when there is a high number of tx sent to the mempool). To achieve this, lightweight modules will be installed on each client server to periodically collect OS and hardware metrics. 

Some of the lightweight modules to be included are:
- <b>Metricbeat</b>: Light module installed on the beacon node server which will collect data on the operating system (e.g RAM, Diskspace, CPU and more)
- <b>Packetbeat</b>: Light module installed on the beacon node server which will monitor network traffic (e.g DNS, SIP traffic, HTTP traffic, ICMP and more)
- <b>Filebeat </b>: Light module installed on beacon node server to read and parse system logs error messages (e.g used to read IIS log files and more)

<h4>
    The architecture design
</h4>

<img src='https://daoagents.s3.amazonaws.com/Quick_ct/arc.png' width="80%" height="80%" style='display: block;    
    margin: 0 auto;'>
<img width="120%" height="120%" src='https://daoagents.s3.amazonaws.com/Quick_ct/pipeline.png' style='display: block;    
    margin: 0 auto;'>
    
    

The data pipeline is as follows:
1.	Firstly, the outgoing data (local queries, global queries, server data and network data) will first get ingested by <b>Logstash</b>, where it will go through some data processing to enrich the data and filter out unnecessary information. 
2.	In the second phase, the data will be forwarded from Logstash to <b>Elasticsearch</b>, where it will get indexed making it available for programmatic querying through HTTP requests.
3.	The last stage would be to connect the <b>Kibana</b> platform to the indexed datasets in elasticsearch to create appropriate charts and tables for users to interact with. Users will also be able to make custom queries and interact with the dashboards through the Kibana UI. 
4.	Some of the data streamed from the servers will  be periodically archived in a centralised database for future research purposes as well as forensic analysis.
5.	The alerting module <b>Watcher</b> will be implemented on the Elasticseach node and configured to send emails when specific metric thresholds are met, or error messages are recorded on the system.

<h3>
    General roadmap
</h3>

Month 2: Data Pipeline building and setting up infrastructure <br>
Month 3: Streamlining data into the centralised server and connecting it to Kibana visualisation dashboard. <br>
Month 4: Building custom ML models and incorprating them to the alerting systems (watcher module) for given set metrics.<br>

<h3>
    Possible Challenges
</h3>

Some if the issues include:
-	The ELK stack does not allow for developing <b>custom ML models</b>. This means that in order to build custom intelligence into the platform, some of the processing and machine learning modelling would have to be done separately from the ELK stack and then later ingested through the pipeline and get indexed.
-	Managing all the nodes throughout the program efficiently whilst avoiding potential disconnection issues
-	Creating an efficient roadmap and predicting how long each step will take is fairly challenging since the project has not been started. The goal is to give regular biweekly updates along the process.

<h3>
    Goal of project
</h3>

The goal is to track and monitor as many features and metrics about the network as possible in the upcoming months. Given the timeframe, success would be to get the project off the ground and set up all the infrastructure and begin to stream network data, beacon node server data as well as some on-chain events through the data pipeline and visulise it through the interface (Kibana UI). 


<h3>
    Mentors
</h3>

The project has been highly shaped by Fredrik’s proposal, hence I plan to engage with Fredrik for further guidance.

I also plan to engage with Barnabé having published insightful work regarding reorg and on-chain CL client behaviour. 


<h3>
    Resources
</h3>

Three Attacks on Proof-of-Stake Ethereum
(https://eprint.iacr.org/2021/1413.pdf)

Blockchain attack discover via Anomaly detection
(https://intranet.icar.cnr.it/wp-content/uploads/2019/12/RT-ICAR-CS-19-07.pdf)

Barnabé Monnot- Visualising the 7-block reorg on the Ethereum beacon chain 
(https://barnabe.substack.com/p/pos-ethereum-reorg)

Barnabé Monnot- Data driven view of the beacon chain incident
(https://barnabe.substack.com/p/a-data-driven-view-of-the-beacon)


Intrusion detection systems on Ethereum (https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9815256)
