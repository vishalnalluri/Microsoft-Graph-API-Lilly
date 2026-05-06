# 2025 09 03   Technical Approaches for Real Time

## Page 1

Technical Approaches for Real-Time Data 
Scenarios, Technologies and Recommendations 
Author 
Francesco Gabbanini 
Contributors 
Devesh Agrawal, Marco Capirossi, Francesco Gabbanini, Vikas Pareek, Rahul Singhal 
Summary 
This document evaluates and recommends architectural patterns and technologies for exposing real-time data 
within the global MQ data asset managed by DIA, distinguishing between event-driven and request/response 
scenarios. 
This positions DIA to deliver scalable, secure, and efficient real-time data solutions, supporting both 
operational and analytical business needs. 
Event-Driven Architectures 
Real-time data delivery is achieved via publisher-subscriber (pub-sub) models. Platforms that will support this 
in DIA include Apache Kafka (scalable, high-throughput), HiveMQ (for MQTT IoT), and Azure Event Hubs. These 
enable decoupled, scalable, and low-latency messaging for both enterprise and edge use cases. 
Request/Response Patterns 
Two main approaches are envisioned to be used by DIA: Lakehouse Federation (LHF) and API-ﬁrst design. 
For Lakehouse Federation, Databricks is the selected platform, enabling uniﬁed access to distributed data 
sources via virtualized query engines and connectors. LHF abstracts physical storage, supports metadata-
driven access, and centralizes governance. While implementing LHF, key technical aspects to consider are: 
query performance, metadata quality, lack of distributed transactional support, and catalog proliferation. 
Security and resource management require IP whitelisting, query protection mechanisms, and strict table 
exposure governance. 
API-First Design is the approach for real time analytics and cross-source data composition. Services like Azure 
Functions can be used for implementations, while MuleSoft Anypoint Platform is used for API management, 
supporting design, security, monitoring, scaling and governance. 
General recommendations 
Under both approaches, recommendations to be considered when deploying real time data access platforms 
include: 1) engaging security and infrastructure teams for connectivity and resource protection; 2) limiting real-
time exposure to high-value, frequently changing tables; avoiding broad table exposure or massive streaming 
of events. 
Governance is also of paramount importance to deﬁne which data have to be exposed in real time and to 
assess whether speciﬁc application use cases truly need to consume real time data.

## Page 2

Introduction 
This document outlines various technical approaches that Data Integration and Analytics can implement to 
expose real-time data. 
There are two main scenarios for real-time data consumption: 
1. Event driven: “Notify me whenever a new data point is generated and give it to me.” 
2. Request/response: “Give me the most up-to-date data when I request it.” 
Scenario 1 requires publisher-subscriber solutions in place. 
Scenario 2 follows the request/response pattern and can be implemented using a variety of approaches. 
Note: in this document, “real-time” data refers to information that is made available to consumers as soon as 
it is generated in a given system (scenario 1), or to the capability for consumers to consume the most recent 
version of the data in a given source system, at the time when the request was triggered (scenario 2). 
According to the above statement, a system that refreshes data at given ﬁxed frequencies is NOT considered 
an example of a real-time system (even if the refresh frequency is very high). 
Scenario 1 - Event Driven 
In order to manage this scenario, publisher/subscriber architectures need to be put in place. 
In a publisher-subscriber (pub-sub) architecture, data producers ("publishers") send messages to a system 
without needing to know which consumers ("subscribers") will receive them. Subscribers express interest in 
speciﬁc topics or event types and receive relevant updates automatically as soon as new data is published. 
This decoupling enables scalable, real-time distribution of information and is foundational to many event-
driven solutions. 
Some widely used publisher-subscriber platforms include Apache Kafka, AWS Kinesis, and Google Pub/Sub. 
These platforms are designed to handle high-throughput, low-latency messaging, allowing organizations to 
transmit, process, and react to real-time data efficiently. They support scalable event-driven architectures and 
can integrate with various sources and consumers, making them suitable for a diverse range of real-time 
analytics and alerting use cases. 
Additionally, for IoT and lightweight messaging scenarios, platforms that implement the MQTT protocol—such 
as HiveMQ—are popular choices. MQTT-based platforms are optimized for reliable, efficient communication 
in environments with constrained bandwidth or intermittent connectivity, making them especially well-suited 
for sensor networks and edge devices. 
In modern architectures, these publisher-subscriber platforms are leveraged within cloud environments to 
streamline real-time data exposure and integration. Cloud providers such as AWS and Azure offer managed 
services—like AWS Kinesis, Amazon SNS, and Azure Event Hubs—that natively support pub-sub paradigms, 
enabling organizations to publish, subscribe, and stream data at scale without the overhead of managing 
underlying infrastructure. This approach provides seamless interoperability, high availability, and rapid scaling, 
empowering enterprises to build robust real-time data pipelines that are accessible from anywhere and can 
support a myriad of applications and analytics workloads.

## Page 3

MQ uses HiveMQ as the platform for MQTT messaging and also utilizes Apache Kafka for scalable pub-sub 
capabilities, while integration with Azure Event Hubs is available for additional ﬂexibility. This approach 
enables to meet both lightweight IoT requirements and broader enterprise messaging needs. 
Scenario 2 – Request/Response 
Lakehouse federation 
Lakehouse federation refers to an architectural approach in which data from multiple distributed storage 
systems can be accessed, queried, and managed as if they reside in a single uniﬁed environment. Rather than 
physically duplicating or consolidating all data into a central repository, federation enables seamless 
integration and interoperability across diverse platforms by virtually combining their metadata and query 
capabilities. 
By abstracting physical storage details and enabling cross-platform interoperability, lakehouse federation 
empowers organizations to unlock real-time insights from distributed datasets while minimizing data 
movement and operational complexity. 
Modern platforms, such as Databricks, implement lakehouse federation by integrating connectors and query 
engines that bridge disparate data sources—including cloud object stores, on-premises databases, and 
external warehouses—into a uniﬁed layer. These systems leverage metadata management and virtualized 
query planning to allow users to access, join, and analyze data from multiple repositories without moving or 
duplicating it. Security and governance controls are applied centrally, ensuring consistent policy enforcement 
across federated sources. 
Within MQ, Databricks has been selected as the primary platform for implementing lakehouse federation, 
providing uniﬁed data access across distributed storage systems. 
API-First Design 
APIs provide a standard way for applications to access real-time data. By using API-driven integration, systems 
can request current information, receive updates, or trigger actions as needed. This makes it easier for different 
platforms to connect and share data efficiently while keeping data ﬂow manageable and secure. 
To manage APIs efficiently, organizations can use API management solutions like MuleSoft Anypoint Platform. 
MuleSoft provides centralized control for designing, securing, monitoring, and scaling APIs, helping teams 
ensure reliable data access and integration across systems. For implementations, technologies that can be 
used include Azure Functions or AWS Lambda. 
Lilly recently adopted MuleSoft in MQ as a platform to manage APIs. 
Position Data Integration Strategies 
For event-driven scenarios, only the publisher-subscriber model is suitable, ensuring real-time updates via 
subscriptions. 
It is important to note that our company already has established platforms to support publisher-subscriber 
models for event-driven integrations. DIA will reuse those platforms, but the intent is not to create a layer that

## Page 4

streams all data exhaustively from every source system: instead, the offer for event driven data is foreseen to 
remain driven by business requests. 
The remainder of this document will concentrate on request-response integration approaches, evaluating 
when to leverage lakehouse federation or APIs to best address speciﬁc business needs. 
In request-response cases, both lakehouse federation and APIs are viable: the choice depends on the speciﬁc 
integration pattern required. 
This section tries to evaluate the pros and cons of each approach to determine the best ﬁt for various business 
needs and to determine how each different approach can be positioned in the overall DIA strategy for real time 
data. 
Lakehouse Federation 
DIA envisions that most of the needs for real time data can be covered through Lakehouse Federation (LHF). 
The idea is to use Databricks for the implementation of LHF, since this is the platform that DIA uses to expose 
the rest of the DIA data asset (GMDF-DP). This way, Databricks would become a uniﬁed platform to consume 
batch and real time data for all MQ. 
For each speciﬁc source system, there would be a set of tables to map using LHF, and connections to sources 
would happen through dedicated database accounts. Data would not be persisted anywhere: instead, the 
connections would allow to consume data directly from sources (because any data that gets persisted would 
rapidly become out of date, thus defeating the purpose of real-time). Also, LHF would not be for consuming 
massive amounts of data: typically, when an application needs to consume real time data, it is not interested 
in consuming extensive amounts of rows from a table, but just only in vary speciﬁc portions of data. 
The LHF approach is particularly effective because it enables rapid set up of access to real-time data from 
relational source systems. 
LHF on Databricks has two characteristics that DIA will have to carefully address: 
• 
It requires the creation of 1 different catalog for each source system; 
• 
It exposes all source system tables by default. 
In order to offer better experience to data consumers and to avoid exposing too many tables, DIA will need to 
put in place additional layers on the Databricks Unity Catalog to group together entities from different catalogs 
and prevent from exposing tables that are not needed in real time (this is in turn something that would avoid 
hitting source systems too much). 
The following points highlight key strengths of the Lakehouse Federation (LHF) approach in enabling real-time 
data access and integration: 
• 
Rapid integration: Connectors and query engines streamline connecting to new or external data 
sources. 
• 
Seamless access to distributed data sources without physically moving or duplicating data. 
• 
Operational efficiency: Reduces data movement and copying, minimizing storage costs and 
complexity. 
• 
Centralized governance: Security and policy enforcement can be centrally managed, ensuring 
compliance and consistency.

## Page 5

The following points highlight key general aspects to consider when implementing LHF: 
• 
Query performance: Virtualized queries can be slower than those against co-located or materialized 
data, especially for large or complex workloads. 
• 
Dependency on metadata quality: Effective federation relies on well-curated metadata and consistent 
schema management across all sources. 
• 
Limited transactional support: Federated systems may not support distributed transactions or strict 
data consistency requirements. 
Before LHF is eventually adopted, it will be important to also address the following points: 
• 
Work on connectivity to L3 systems. Since LHF on Databricks requires compute instances that use 
ranges of IP’s, this approach requires our MESA team to whitelist ranges of IP’s against source systems. 
Security team also need to be involved in the discussions. 
• 
Envision built-in protection mechanisms to avoid data consumers triggering queries that are resource 
intensive and may block source systems. This is especially important since tables made available 
through LHF may be consumed by potentially many applications. Several approaches exist, both at 
source system level and at Databricks level. 
• 
Control on table exposure: by default, all tables are exposed, increasing the risk of sensitive or 
unnecessary data becoming visible to consumers (and also indirectly increasing the risk of hitting too 
much the source system). Clear process needs to be put in place to identify source system tables that 
should be available in real time and therefore are mapped using LHF. 
• 
Provide mechanisms to logically group related entities spanning multiple catalogs to streamline user 
experience and manage catalog proliferation. 
• 
Deﬁne governance to establish which tables should be made available in “real-time” using LHF. 
Ideally, real time should be limited to small sets of tables with data that is frequently changing. 
Example use cases 
• 
An application team needs to have up to date information from table XYZ in PMX, describing a given 
batch that is being produced. LHF is set up for table XYZ so the application can consume data from 
table XYZ in the Databricks catalog, using the batch number as a ﬁlter, to have the most recent copy of 
data. 
• 
An application team wants to implement a KPI calculation that requires combining data from GMDF 
reﬁne tables with up-to-date values from PMX table XYZ. LHF is setup for table XYZ so the application 
can have the most recent copy of data from PMX. 
APIs 
Once LHF is set up to expose raw data from source system tables, MuleSoft-based API layers can be put in 
place to provide the ability to combine real-time data across multiple source systems and/or to perform real 
time calculations on top of that data. 
API implementation can happen using MuleSoft itself (though it might be a complex option in some cases as it 
potentially requires writing Java code), or it can happen through a layer of Azure functions that are exposed 
using Azure API Management and mapped in MuleSoft through API proxies or connectors (that is, application 
uses MuleSoft APIs but then MuleSoft calls the APIM endpoint, which then routes to the Azure Function). This 
allows to leverage Python for implementations and to easily connect to data on Databricks, while leveraging

## Page 6

MuleSoft as a platform for orchestrating, integrating with other systems, managing and cataloguing APIs, 
policies and authentication. 
It is important to note that using APIs as a means to connect directly to relational systems would introduce 
unnecessary complexity, especially when the LHF approach is available. LHF provides a more straightforward 
and maintainable integration, avoiding the overhead of building and maintaining additional API layers merely 
to access relational data. Therefore, in scenarios where LHF can offer native access, it does not make sense to 
introduce APIs for this purpose. 
Since this API layer offers capabilities for elaborating source system data, idea is that this layer would likely be 
dependent on use cases and applications; however, careful design might offer opportunities for re-use across 
different contexts. 
The following list highlights key strengths of the API approach: 
• 
Fine-grained access: APIs allow for precise, controlled interactions with data and services, enabling 
secure, role-based access and robust auditing capabilities. 
• 
Standardization: RESTful APIs are widely adopted, allowing for standardized integration patterns 
across applications and systems. 
The following points represent aspects to consider when implementing the API layer: 
• 
Development and maintenance overhead: building, documenting, and maintaining APIs requires 
ongoing engineering resources and strong version control. 
• 
Scalability limits: APIs may introduce bottlenecks or require additional gateways/load balancers 
under heavy workloads. 
• 
Potential data silos: when not well-governed, or when badly designed, APIs can proliferate, leading to 
fragmented data and inconsistent access patterns across the organization. 
Examples 
• 
An application team needs to generate a representation of all alarms associated with a speciﬁc batch. 
The relevant data is sourced from tables in two separate systems (System A and System B), and must 
reﬂect the most current state of information at the time of generation. To achieve this, an API is 
developed that retrieves data from both systems using LHF. It then applies in-memory logic to merge 
and process the data, ultimately returning the combined results in the API response. 
Recommendation and next steps 
• 
In event-driven scenarios: 
o 
Use publisher-subscriber platforms that are already deployed within the company to provide 
real time access to data. 
• 
In request-response scenarios: 
o 
Use lakehouse federation to provide access to raw data in relational systems’ tables. 
o 
Use APIs to provide real time access to information that may combine different sources and 
offer real time insights and analytics based on source data. 
After reaching consensus among the principal stakeholders within MQ Tech@Lilly, the subsequent step is to 
initiate a project with clearly deﬁned priorities, timelines, and milestones.

## Page 7

Team will also need to carefully evaluate how to redesign existing applications that may need real time data to 
use the new approach.