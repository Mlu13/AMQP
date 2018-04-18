Maggies-MacBook-Pro:~ maggie$ pip install pika
Requirement already satisfied: pika in /Library/Python/2.7/site-packages (0.11.2)
Maggies-MacBook-Pro:~ maggie$ python
Python 2.7.10 (default, Jul 15 2017, 17:16:57) 
[GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.31)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import pika
>>> url = "amqp://tafzfptx:lRrZ2PMfADB1Rq7zUHIs7J4dzkpTXQ1x@otter.rmq.cloudamqp.com/tafzfptx"
>>> params = pika.URLParameters(url)
>>> connection = pika.BlockingConnection(params)
>>> channel = connection.channel()
>>> channel.queue_declare(queue="hello")
<METHOD(['channel_number=1', 'frame_type=1', "method=<Queue.DeclareOk(['consumer_count=0', 'message_count=0', 'queue=hello'])>"])>
>>> def callback(ch, method, properties, body):
...     print "
  File "<stdin>", line 2
    print "
          ^
SyntaxError: EOL while scanning string literal
>>>     print "[x] Received %r" %(body)
  File "<stdin>", line 1
    print "[x] Received %r" %(body)
    ^
IndentationError: unexpected indent
>>> def callback(ch, method, properties, body):
...     print "[x] Received %r" %(body)
... 
>>> channel.basic_consume(callback, queue="hello", no_ack=True)
'ctag1.fac464fb7349409c8d5d05e2794a5a8c'
>>> channel.start_consuming()
[x] Received 'hello viewers!'
[x] Received 'hello viewers second time!'

*************************************************************************************
Last login: Tue Apr 17 21:41:44 on ttys000
Maggies-MacBook-Pro:~ maggie$ python
Python 2.7.10 (default, Jul 15 2017, 17:16:57) 
[GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.31)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import pika
>>> url = "amqp://tafzfptx:lRrZ2PMfADB1Rq7zUHIs7J4dzkpTXQ1x@otter.rmq.cloudamqp.com/tafzfptx"
>>> params = pika.URLParameters(url)
>>> connection = pika.BlockingConnection(params)
>>> channel = connection.channel()
>>> channel.basic_publish(exchange="", routing_key="hello", body="hello viewers!")
True
>>> >>> channel.basic_publish(exchange="", routing_key="hello", body="hello viewers!")
  File "<stdin>", line 1
    >>> channel.basic_publish(exchange="", routing_key="hello", body="hello viewers!")
     ^
SyntaxError: invalid syntax
>>> channel.basic_publish(exchange="", routing_key="hello", body="hello viewers second time!")
True
>>> 
