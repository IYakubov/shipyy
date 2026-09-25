NAVAL DUEL — Networked Edition
================================

A 2-player top-down ship battle. One screen (PC, TV, laptop) shows the
battle. Two players connect from their phones and steer with a ship's
wheel + fire buttons.

REQUIREMENTS
------------
Node.js 16 or newer.

SETUP
-----
1. Open a terminal in this folder.
2. Install dependencies:
       npm install
3. Start the server:
       npm start
   You should see:
       NAVAL DUEL server running on http://localhost:3002

HOW TO PLAY
------------
1. On the PC/TV/laptop that will display the battle, open a browser to:
       http://localhost:3002
   (or http://<your-computer's-LAN-IP>:3002 if opening from another device)
   Click "CREATE GAME". A 6-digit room code appears with a QR code.

2. On each phone, connected to the SAME WiFi as the host computer, scan
   the QR code, or open:
       http://<host-computer-LAN-IP>:3002/controller.html
   and enter the 6-digit code.

3. The first phone to join becomes PLAYER A, the second becomes PLAYER B.
   Each phone shows a lobby screen — tap READY. Once both are ready, the
   ship's-wheel controller appears and the battle starts on the host screen.

CONTROLS (on phone, portrait)
------------------------------
- Ship's wheel (center): drag your finger around the dial to turn it,
  like turning a real boat's wheel. Turning it left/right steers the
  ship left/right. Holding the wheel (touching it at all) makes the
  ship sail forward at a steady, moderate speed — let go and it stops.
- MACHINE GUN button (bottom-left): hold to fire straight ahead from
  the bow, forward only.
- TORPEDOES button (bottom-right): tap to launch a 3-torpedo spread
  off the ship's left (port) side. Has a cooldown between salvos.

GAMEPLAY
--------
- Each ship has 6 HP. Machine-gun hits do 1 damage, torpedo hits do 2.
- First ship to sink the other wins the battle.
- After a win, the host shows a "Rematch" button — pressing it resets
  both ships without needing a new room code.

PROJECT STRUCTURE
------------------
server.js                    - Express + Socket.io server (rooms, lobby, input relay)
public/index.html            - Host display (the sea battle itself)
public/controller.html       - Phone controller (ship's wheel + weapon buttons)
public/assets/               - Wheel dial, wheel graphic, and weapon button art
package.json                 - Node dependencies

NOTES
-----
- Everything runs on your local network — no internet/cloud needed.
- If a phone disconnects mid-battle, it automatically tries to rejoin
  its same player slot when it reconnects.
- If the host page is closed or refreshed, the room is torn down and
  players are notified.
