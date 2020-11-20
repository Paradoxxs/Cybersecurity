Message broker is a middle man between the sender and receiver, handling message validation, transformation, and routing. This allow decouple of end-points. 
A message broker may be used to manage a workload queue or message queue for multiple receivers, providing reliable storage, guaranteed message delivery and perhaps transaction management. The following represent other examples of actions that might be handled by the broker
	-	Route messages to one or more destinations
	-	Transform messages to an alternative representation
	-	Perform message aggregation, decomposing messages into multiple messages and sending them to their destination, then recomposing the responses into one message to return to the user
	-	Interact with an external repository to augment a message or store it
	-	Invoke web services to retrieve data
	-	Respond to events or errors
	-	Provide content and topic-based message routing using the publish–subscribe pattern
	
	
Example of message broker:
	- [[RabbitMQ]]
	- Kafka
	- Radis
	- ZereMq