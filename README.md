# Django channels and web socket implementation

## Create virtual env

    $ python -m venv env

>you can use any name insted of **env**

## Activate the environment

    $ source env/bin/activate

## Install requirements.txt
    $ pip install -r requirements.txt

## Install Docker
    $ sudo snap install docker

## Start Redis server on port 6379
    $ sudo docker run -p 6379:6379 -d redis:5

## Confirming channel layer can communicate with Redis
    $ python manage.py shell
    >>> import channels.layers
    >>> channel_layer = channels.layers.get_channel_layer()
    >>> from asgiref.sync import async_to_sync
    >>> async_to_sync(channel_layer.send)('test_channel', {'type': 'hi'})
    >>> async_to_sync(channel_layer.receive)('test_channel')
    {'type': 'hi'}

## Run development server
    $ python manage.py runserver

Open a browser tab to the room page at http://127.0.0.1:8000/chat/room/. Open a second browser tab to the same room page.

In the second browser tab, type the message “Hi” and press enter. You should now see “Hi” echoed in the chat log in both the second browser tab and in the first browser tab.
