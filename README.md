# m32_chat_server

Simple chat server for [Morserino-32](https://github.com/oe1wkl/Morserino-32)

This server script listens for UDP messages and rebroadcasts them to all other clients.

To "connect" or "make yourself known" to the server, ~~send "hi" message from your Morserino~~ just start sending morse code.  Server will respond with ":hi" with number of clients connected (1 means you're alone). After that, server will resend all messages from you to all other known clients (you excluded).

If client is inactive (not transmitting) for too long, it will be dropped from the list. This is indicated by ":bye" message sent from the server. To reconnect, ~~send "hi" again~~ just start sending again.

You can also force disconnection by sending ":bye".

Additional features:
 * empty keepalive UDP packets sent each 10 seconds to avoid NAT timeouts
 * number of clients is restricted (to avoid abuse)
 * small delay is introduced (to avoid abuse)
 * Console logging output designed to be appended to an HTML file, eg: `./m32_chat_server | tee -a ~/public_html/morse_log.html` or similar...  (I suggest running the server in `tmux` or `screen` to keep it running after you've logged off.)
 
**Caution: UDP keepalive messages, while invisible, prevent your Morserino-32 from auto-shutdown!**
