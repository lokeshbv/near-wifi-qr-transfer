# Near

Send files between your computer and phone over the same Wi-Fi. Scan a QR code to download files to your phone, or upload files from your phone to your computer. Transfers stay on your local network; there is no cloud relay.

## Quick start

1. Install [Node.js 20 or newer](https://nodejs.org/) on the computer that will host the transfer.
2. Open Terminal (macOS/Linux) or PowerShell (Windows) in this project folder and run:

   ```sh
   npm install
   npm start
   ```

3. Open [http://localhost:8787](http://localhost:8787) on that computer.
4. Choose files to send, or choose **Receive from phone** to upload files to the computer.
5. Scan the QR code with your phone. Keep both devices on the same Wi-Fi until the transfer finishes.

The app shows your computer's Wi-Fi address and lets you copy the link if scanning is unavailable. If the phone cannot connect, check that both devices are on the same network and allow Near through the computer's firewall. Guest Wi-Fi, VPNs, or router client isolation can block device-to-device connections.

## Where received files go

Files uploaded from a phone are saved to `~/Downloads/Near Received` on the host computer. Existing files are kept; duplicate names get a number suffix. You can change the folder with the `NEAR_RECEIVE_DIR` environment variable.

## Privacy and limits

- The app listens on the local network so nearby devices can connect. Only share a QR link with the intended recipient.
- Each transfer link expires after 30 minutes. **End transfer now** revokes it.
- A transfer can contain up to 2 GB of files.
- Keep the host computer awake and the app running during a transfer.
- The local network transfer uses HTTP and has no cloud relay. Use a trusted Wi-Fi network.

## Development

```sh
npm run dev
```

The browser interface is served by the Node.js host; there is no separate frontend build step.
