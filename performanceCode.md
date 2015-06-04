#Performance
###Rate of incomming/outcomming messages, total and per broker 
*Metrics: Meter
	used to measure the rate of messages 
*Inject Location
	Package:nsx/mp/proton/internal-framwork
	nsx/management/messaging/PublishManageer.java
	```
	private SendResult send(List<Broker> brokers, Message amqpMessage, String exchangeName, String routingKey,
            boolean isTopicHeartbeat, boolean suppressIndividualBrokerSendFailure) {
            ...
            for (Broker broker : brokers) {

            	...
            	// one manager publish message to each broker 
            	broker.getAmqpTemplate().send(exchangeName, routingKey, amqpMessage); 
        	}
        }
	```