# Near — Local Wi-Fi QR Transfer

Send files directly in either direction between a laptop and a phone, tablet, or another laptop over the same Wi-Fi/local network. Choose **Send to device** to download laptop files on a phone, or **Receive from phone** to upload phone files into the laptop's Downloads folder. Scan the QR code with the receiving device's camera or QR scanner.

## Supported setup

- **Host:** macOS, Windows, or Linux laptop/desktop with Node.js 20 or newer.
- **Receiver:** a modern browser on Android, iPhone/iPad, or another laptop.
- **Network:** both devices must be on the same reachable Wi-Fi/LAN. Guest Wi-Fi, client isolation, VPN routing, or firewall rules may block local device-to-device traffic.
- The laptop hosting Near must remain awake and the app running until transfers finish. The actual file transfer stays on the local network; there is no cloud relay.

## Run the host

1. Install Node.js 20 or newer on the laptop that will host the files.
2. In this folder, run `npm install` once.
3. Run `npm start` and open `http://localhost:8787` on that laptop.
4. Choose files to send, or choose **Receive from phone** and scan that QR code to upload files to the laptop.

The address pill shows the host's LAN IP; click it to copy the address. If camera scanning is unavailable, use **Copy link** and open the link on the receiving device. On some networks, the receiving device may need to allow local-network access or the host app may need to be allowed through the computer's firewall.

## Transfer behavior

Each session expires after 30 minutes. **End transfer now** revokes the QR link and removes staged files for laptop-to-phone transfers. Phone-to-laptop uploads are saved with collision-safe names in `~/Downloads/Near Received`; ending that session prevents further uploads but keeps files already received. The total transfer limit is 2 GB. The interface defaults to dark glass mode, remembers the host's light/dark choice, and includes that choice in the QR link. Upload progress and short sound cues provide feedback; sounds can be muted with device/browser volume controls.

QR generation and the interface are local. The transfer uses HTTP on the trusted local network, so share the private QR link only with the intended recipient.
