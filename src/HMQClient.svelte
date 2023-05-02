<script>
	import LibLoader from "./LibLoader.svelte";

	// Chat app MQTT settings
	var toggle = 0;
	var USER = "KeshavSVen";
	var mqttServer = "ws://broker.hivemq.com:8000/mqtt";
	var mqttTopic = "codettes2022";
	var userName = USER; //document.getElementById("logon-as").value; // || "anonymous user"
	//var userName = "anonymous usr";
	const clientId = "cb22_" + Math.random().toString(16).substr(2, 8);
	var userList = [];

	const opts = {
		keepalive: 30,
		clientId: clientId,
		protocolId: "MQTT",
		protocolVersion: 4,
		clean: true,
		reconnectPeriod: 1000,
		connectTimeout: 30 * 1000,
		will: {
			topic: "WillMsg",
			payload: "Connection Closed abnormally..!",
			qos: 0,
			retain: false,
		},
		rejectUnauthorized: false,
	};

	function onLoaded() {
		// function that manages the UserList and other UI stuff related to PingPong
		function handlePong(pongObj) {
			if (toggle == 0) {
				const index = userList.findIndex((object) => {
					return object.userName === pongObj.userName;
					// Update Userlist with Pongs
				});

				//console.log("index:" + index);
				if (index >= 0) {
					console.log("User exists");
					userList[index] = pongObj;
				} else {
					console.log("New User " + pongObj.userName);
					userList.push(pongObj);
				}
				//console.log(userList);
				redrawUserList();
			}
		}

		function sendPing(usr = "*") {
			if (toggle == 0) {
				// ping sends out a message to all (*) or any specific user to respond if ur there
				var pingObj = { ping: usr }; // JS Object {ping : "usr"} -> JSON {/"ping/":/"usr/"}
				client.publish(mqttTopic, JSON.stringify(pingObj));
			}
		}

		function sendPong() {
			if (toggle == 0) {
				// sends clientID and UserName in a JSON object (and whatever u need more)
				var pongObj = {
					pong: { userName: userName, clientId: clientId },
				};
				client.publish(mqttTopic, JSON.stringify(pongObj));
				console.log(JSON.stringify(pongObj));
			}
		}

		function redrawUserList() {
			if (toggle == 0) {
				// Generate the userlist HTML
				var ulist = "";
				userList.forEach(function (item) {
					//var x = arrayItem.prop1 + 2;
					var CHATBUBBLE =
						'<div class="codettesBootcamp2022"><h4 class="bootcamp2022name">'; //</h4></div>
					if (item.userName == USER) {
						//ulist+= item.userName + " <a href='#" + mqttTopic + "/'><i class='fa fa-fw fa-phone'></i></a></li><br>"
						/*var apply = '<h4 class="styleY">' + item.userName + '</h4><br><button class="debug"onclick="openDebugDialog()"><img class="send-img" src="debug-icon.png"></button>';
            document.getElementById("you").innerHTML+=apply;*/
					} else {
						ulist +=
							CHATBUBBLE +
							item.userName +
							"<i class='fa fa-fw fa-phone'></i></a></li>" +
							"</h4></div>" +
							"<br>";
					} //ulist+= CHATBUBBLE + item.userName +  "<a href='#" + mqttTopic + "/" + item.clientId +"'><i class='fa fa-fw fa-phone'></i></a></li>"+ "</h4></div>" +"<br>"
				});
				//ulist+="</ul>";
				console.log(ulist);
				document.getElementById("userlist").innerHTML = ulist;
			}
		}

		console.log("connecting mqtt client");
		const client = mqtt.connect(mqttServer, opts);

		client.on("error", function (err) {
			console.log(err);
			client.end();
		});

		client.on("connect", function () {
			// Once a connection has been made, make a subscription and send a message.
			console.log("client connected:" + clientId);
			client.subscribe(mqttTopic, { qos: 0 });

			let message = USER + " just hopped on! say hi!";

			client.publish(mqttTopic, message, { qos: 0, retain: false });
			sendPong();
		});

		client.on("message", function (topic, message, packet) {
			if (toggle == 0) {
				let msg = message.toString(); // library delivers  buffer so convert to strig first
				console.log("onMessageArrived: " + msg);
				// if it has JSON payload do NOT add to chat
				/*try {
					let msgObj = JSON.parse(message.toString()); // t is JSON so handle it how u want
					// if message has Pin of Pong in it send it to the PingPongHandler
					if (Object.keys(msgObj)[0] == "ping") {
						sendPong();
					}
					if (Object.keys(msgObj)[0] == "pong") {
						handlePong(msgObj.pong);
					} // pong value is an object!!
					// other handlers for control messages below
				} catch {
					document.getElementById("chatlog").innerHTML +=
						"<br>" + msg;
				}*/
			}
		});

		client.on("close", function () {
			console.log(clientId + " disconnected");
		});
	}
</script>

<p>MQTT widget</p>

<LibLoader
	url="https://cdnjs.cloudflare.com/ajax/libs/mqtt/4.3.7/mqtt.min.js"
	on:loaded={onLoaded}
/>

<div id="container" />

<style>
	#container {
		height: 300px;
		width: 300px;
	}
</style>
