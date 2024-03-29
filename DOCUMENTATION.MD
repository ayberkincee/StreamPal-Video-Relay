# WebSocket Streaming Server Documentation

## Overview

This project provides a WebSocket streaming server that facilitates real-time communication between broadcasters and streamers. Broadcasters can send video data in chunks, and the server efficiently handles the aggregation and delivery of these chunks to connected streamers.

## Features

* Real-time video streaming using WebSocket communication
* Support for broadcasters and streamers with unique identifiers
* Efficient handling of chunked video data for smooth streaming

## Getting Started

### Prerequisites

* Node.js installed on your machine

### Installation

1. Clone the repository:

```bash
git clone <repository-url>
```
2. Install dependencies:
```bash 
cd <project-folder> && npm install
```

npm start


The server will be running on port 3000.

## Usage

### Broadcasting

Broadcasters connect to the WebSocket server and send video data in chunks. The server handles the aggregation of these chunks and notifies streamers when the complete video is received.

### Streaming

Streamers connect to the WebSocket server and request data from specific broadcasters. They receive the video data in chunks, allowing for efficient streaming.

## API Reference

### Class: ChunkData

Represents a chunk of video data with metadata.

#### Constructor

```javascript
const chunk = new ChunkData(uint8Array);
```

## Methods
- toUint8Array(): Converts the ChunkData object to a Uint8Array.
# Function: sendForwardStreamMessage
Forwards video data from broadcasters to streamers.
```javascript
sendForwardStreamMessage(ws, messageData);
```

## License
This project is licensed under the GPL-3.0 License
## Acknowledgments
- Google Bard and Chat GPT along with Codeium for helping with lots of questions I had about scalabilty along with proper routes to take and such!
- https://github.com/fr4ctur3d
- https://github.com/Vampeyer
