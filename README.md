const { Client } = require('whatsapp-web.js');
const qrcode = require('qrcode-terminal');

// Initialize the WhatsApp client
const client = new Client();

// Connect to the WhatsApp web interface
client.on('qr', (qr) => {
  qrcode.generate(qr, { small: true });
});

client.on('ready', () => {
  console.log('Client is ready!');
});

// Listen for incoming messages
client.on('message', async (message) => {
  // Check if the message is a text message
  if (message.body) {
    // Send a response
    await message.reply('Hello! How can I help you?');
  }
});

// Start the client
client.initialize();
