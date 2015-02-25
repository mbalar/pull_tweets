Some Code Examples
------------------

First, authenticate with your application credentials::

	from TwitterAPI import TwitterAPI
	api = TwitterAPI(consumer_key, consumer_secret, access_token_key, access_token_secret)

Get some tweets::

	r = api.request('search/tweets', {'q':'pizza'})
	for item in r:
		print item

Stream tweets from New York City::

	r = api.request('statuses/filter', {'locations':'-74,40,-73,41'})
	for item in r:
		print item
		
Notice that ``request()`` accepts both REST and Streaming API methods, and it takes two arguments: the Twitter method, and a dictionary of method parameters.  In the above examples we use ``get_iterator()`` to get each tweet object.  The iterator knows how to iterate both REST and Streaming API results.  Alternatively, you have access to the response object returned by ``request()``.  From the response object ``r`` you can get the raw response with ``r.text`` or the HTTP status code with ``r.status_code``.  See the `requests <http://docs.python-requests.org/en/latest/user/quickstart/>`_ library documentation for more details.