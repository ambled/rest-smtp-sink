A busybox based container of the rest-smtp-sink application.

This works with both the official repo (https://github.com/llambda/rest-smtp-sink) and my own repo (https://github.com/ambled/rest-smtp-sink) which adds 'Delete'(single) and 'Purge'(before X) endpoints for the UI and REST.

This image exposes two ports which are overridden from the defaults (2525,2526)

25 - this is the smtp target for your development testing, messages received here will be stored in a sqlite database

80 - this port provides a web page with a rest API to retrieve messages

CMD ["node","cli","--listen","80","--smtp","25"]


docker run --name rest-smtp-sink -d -p 80 -p 25:25 weave/rest-smtp-sink
