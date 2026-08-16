# Replit run notes

## Start the server

```bash
npm install
npm start
```

The HTTP and WebSocket server listens on port `5000`. The WebSocket endpoints
are `/ws/gemini` and `/ws/esp32`.

## ESP32 connection stability

The ESP32 firmware uses `WebSocketsClient`'s built-in reconnect loop. Its
15-second JSON keepalive is handled by the server as a local pong and is not
forwarded to Gemini Live. After changing `firmware.ino`, flash the sketch to
the ESP32 and monitor the serial log for `[WS] Connected ✓` and
`[WS] Server hello/keepalive ack`.