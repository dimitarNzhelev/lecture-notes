
### Microcontrollers and Microprocessors (MCUs)
![[Pasted image 20241216191517.png]]
![[Pasted image 20241216191455.png]]


## PSU (Power Supply)

### DEFINING REQUIREMENTS
 - Input voltage
 - Output voltages
 - Continuous current consumption
 - Peak current consumption
 - Efficiency/Cooling
 - Derating/Grade
 - Insulation
 - Diagnostics
### POWER SOURCES
- Line power
- Battery power
- Energy harvester
- Combined

#### BATTERY POWERED – WHAT TO CONSIDER
- Capacity
- Chargeable/non-chargeable
- Cycle life (amount of charges and discharges)
- Form factor
- Temperature performance
- Chemistry type
- Regulations
## COMMUNICATION PROTOCOLS
#### Wired
![[Pasted image 20241216181900.png]]

### Wireless
![[Pasted image 20241216181942.png]]

#### 6LOWPAN
- IPv6 communication over low-power, low-bandwidth wireless networks
- **Compression:** Reduces the size of IPv6 headers to fit into small data packets typical of low-power networks (e.g., IEEE 802.15.4).
- **Fragmentation:** Splits larger IPv6 packets into smaller frames to meet the limited frame size of low-power networks

#### COAP
- **Definition:** CoAP (Constrained Application Protocol) is a lightweight web transfer protocol designed for constrained devices and low-power networks, primarily in IoT environments.
- **Purpose:** It enables efficient communication between devices with limited resources, often used in machine-to-machine (M2M) communication.
- **Protocol Basis:** Built on UDP (User Datagram Protocol) for simplicity and low overhead, unlike HTTP, which uses TCP.

- **Low Overhead:** Designed for minimal resource usage in terms of bandwidth, memory, and processing power.
- **RESTful API:** Similar to HTTP, it uses REST principles (GET, POST, PUT, DELETE) to interact with resources.
- **Compact Messages:** Uses a binary header and compact encoding to minimize message size.
- **Reliable Communication:** Supports optional reliability mechanisms like retransmissions and acknowledgments over UDP.
- **Asynchronous Communication:** Designed to handle intermittent connections and asynchronous message exchanges.

## COMMUNICATION MODELS

##### Device computing
- Real time
- Data from sensors directly connected to the IoT device
- Constrained resources/computing power
##### Edge computing
- Delay from communication protocols
- Data from multiple sensors
- Relatively big resources/computing power
##### Cloud computing
- Major delay due to the nature of the internet
- Data from millions of devices
- Resources available to run complex algorithms

#### Request & response model
- Based on client server architecture
- Stateless model
- Client sends a request to the server and the server responds to the request. When the
server receives the request it decides how to respond, fetches the data retrieves
resources, and prepares the response, and sends it to the client.

#### Publisher/Subscriber model
- topics
- publisher, broker, subscirber
- MQTT
	- single level wildcard - +
	- multi-level wildcard - #
	- QOS
		- QoS0 At most one delivery
		- QoS1 At least one delivery

		- QoS2 Exactly one delivery

#### Push-Pull model
The push-pull model constitutes data publishers, data consumers, and data queues.
- The push-pull model constitutes data publishers, data consumers, and data queues.
- Publishers and Consumers are not aware of each other.
- Publishers publish the message/data and push it into the queue. The consumers,
present on the other side, pull the data out of the queue. 
- Queues also act as a buffer which helps in situations where there is a mismatch
between the rate at which the producers push the data and consumers pull the data.
#### Exclusive pair
- bi-directional model, including full-duplex communication among client and
server. The connection is constant and remains open till the client sends a request to
close the connection.
- The Server has the record of all the connections which has been opened.
- This is a state-full connection model and the server is aware of all open
connections.


