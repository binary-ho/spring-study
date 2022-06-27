# Message Broker

simple broker는 클라이언트에서 전달 받은 subscription을 메모리에 저장하고 연결된 client에게 메시지를 보내는 역할을 한다. <br> <br>
stomp broker relay는 Spring MessageHandler로 메시지를 message broker에게 전달하는 역할을 한다. 
그렇게 하기 위해 tcp 연결이 성립되고 나면 모든 메시지는 broker에게 전달하고 다시 broker에게 전달받은 메시지를  WebSocket session을 통해서 클라이언트에게 보낸다. <br> 
**이 작업을 relay라고 하고 broker <-> messageHandler <-> clinet 양방향으로 진행된다.**

https://wedul.site/693
