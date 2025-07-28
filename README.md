# LLM_function_calling

## Ooen AI key
You will need to create a new open API key from [here](https://platform.openai.com/api-keys) 
## Create virtualenv end install libraries
create a python virtual envirnment using the following commands
```
virtualenv venv
python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt
``` 

## API 

We have two end points:

### Cancel order 
Business logic: Only cancel if order_date < 10 days ago, here is a simple `curl` command to test calling the function.

```
curl -X 'POST' \
 'http://127.0.0.1:8888/cancel_order' \
 -H 'accept: application/json' \
 -H 'Content-Type: application/json' \
 -d '{
  "order_id": "1"
}'
```

### Order tracking 
Track the order, here is a simple `curl` to test it.
```
curl -X POST "http://127.0.0.1:8888/track_order" \
     -H "Content-Type: application/json" \
     -d '{"order_id": 1}'

```

### Chat with LLM
This is the main function to chat with the chatbot. I will show two examples chatting with the chatbot.

* Chatting with the chatbot asking to `cancel` an order. 
```
curl -X POST "http://127.0.0.1:8888/chat" \
     -H "Content-Type: application/json" \
     -d '{"message": "Can you cancel order 1 for me?"}'

```

* Chatting with the chatbot asking to `track` an order.
```
curl -X POST "http://127.0.0.1:8888/chat" \
     -H "Content-Type: application/json" \
     -d '{"message": "Can you track order 1 for me?"}'

```
