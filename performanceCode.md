#Performance
###Rate of incomming/outcomming messages, total and per broker 

* Metrics Collector: Meter
	used to measure the rate of messages 
* Inject Location
	## Outcoming Messages: publishing 
	Package:
	* nsx/mp/proton/internal-framwork

	* nsx/management/messaging/publising/PublishManageer.java

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

	## Incoming Message : subscribing 
	* nsx/mp/proton/internal-framwork

	* nsx/management/messaging/subscribing/SubscriptionManager/

	```

	@Override
        public void handleMessage(Message<?> message) throws MessagingException {
        	// each broker was bound to a set of messageChannel 
        	// Delegate Desgin pattern 
            try {
                Message<?> newMessage = MessageBuilder.fromMessage(message).setHeader("broker", broker.getBrokerConfig()).build();
                MessageTracingUtils.printLog(Utils.formatAsLogSFPattern("Subscription manager: Forwarding message to inbound routing channel. Broker = {}, {}",
                    broker.getBrokerConfig().getHost(), messagingUtils.getMessageTag(message.getHeaders())));
                messageChannel.send(newMessage);
            } catch (Exception ex) {
                logger.error("Failed to send message to the subscribing channel.");
            }
        }
	```