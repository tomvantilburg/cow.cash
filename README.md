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

Run CASH with forever as a global service
----------------------------------------
1. If not previously done, install forever package

```
	npm install forever -g
```

2. Create a global init.d script (change paths as needed and uid for different clients/processes)

```
	sudo su
	vim /etc/init.d/cash-ontw
```
Check the sample init.d script and adjust code as needed

Make the script executable

```	
	chmod +x /etc/init.d/cash-ontw
```

Add script to rc.d, if you want to enable it on boot

```	
	update-rc.d cash-ontw defaults
```