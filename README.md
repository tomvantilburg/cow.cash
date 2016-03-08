# cow.cash
Socketserver for COW

COW needs a minimal server to serve websockets, the current implementation is a Node.js instance called cash.js. It has some auto-restarting magic around it to make it more robust (though it hasn't crashed for a long time)

### CASH ###

Cash is the server component of COW. It is meant to run behind a secure proxy which handles the SSL bit and passes a non-secure websocket through (hence the normal http server in cash). Currently we use haproxy to do this,since there are not many websocket aware proxies that also can handle SSL.

Running direct
---------------
Run cash with:
	```
		node cash.js
	```

Run CASH with forever-service as a global service
----------------------------------------
1. If not previously done, install forever package

	```
		npm install forever-service -g
	```

2. Create service for a given client

	```
		sudo forever-service install cash-<myclient> --script /<pathto>/<cash-myclient>.js
	```

3. Delete service for a given client

	```
		sudo forever-service delete cash-<myclient>
	```