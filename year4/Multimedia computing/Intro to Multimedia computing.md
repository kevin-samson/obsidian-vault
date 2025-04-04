# Goals
## Principles
- Classify multimedia applications
- Identify the network services the apps need
- Making the best of best effort services
- Mechanisms for providing Qos

## Protocols and Architectures
- Specific protocols for use on a best-effort network
- Architectures for Qos

# Multimedia Networking

| Feature                    | Streaming Stored Multimedia                                       | Streaming Live Multimedia                                       | Interactive Real-Time Multimedia                                                    |
| -------------------------- | ----------------------------------------------------------------- | --------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Definition**             | Media is pre-recorded and stored at the source.                   | Media is broadcasted live as it happens.                        | Real-time interactive applications like IP telephony and video conferencing.        |
| **Client Playback**        | Begins before all data has arrived (buffered).                    | Playback lags but still follows timing constraints.             | Requires minimal delay for real-time interaction.                                   |
| **Interactivity**          | VCR-like functionality (pause, rewind, fast forward, slider bar). | Some interactivity: pause, rewind possible but no fast forward. | Highly interactive; fast forward and rewind are not applicable.                     |
| **Delay Tolerance**        | Initial delay of ~10 sec is acceptable.                           | Playback buffer causes lag (tens of seconds).                   | End-to-end delay must be < 150 ms for good experience, < 400 ms still acceptable.   |
| **Protocol Used**          | RTSP (Real-Time Streaming Protocol).                              | Often uses similar protocols but optimized for live streaming.  | Requires real-time communication protocols like RTP (Real-time Transport Protocol). |
| **Examples**               | Netflix, YouTube (on-demand content).                             | Internet radio, live sports broadcasts.                         | Zoom, Skype, online multiplayer games.                                              |
| **Timing Constraints**     | Data must arrive in time for playout.                             | Still requires timing constraints for seamless playback.        | Strict timing constraints to maintain interactivity.                                |
| **Session Initialization** | Not a major concern, as media is pre-stored.                      | Live stream setup requires encoding and broadcasting setup.     | Requires mechanisms to advertise IP, port, and encoding (e.g., SIP for VoIP).       |

# Streaming Stored Multimedia
Application-level streaming techniques for making the best out of services
- Client side buffering - Showing loading symbol while buffering
- Use of UDP over TCP
- Use multiple encoding of multimedia

## Simplest Approach
```mermaid
graph TD;
    subgraph Client
        A[Web Browser] --> B[Media Player]
    end
    A <--> C[Web Server with Audio Files]

```

- Audio or Video are stored in files
- There are sent or transferred as HTTP objects
	- Sent as an entity to client and then passed to player
**Drawbacks**
- Audio or Video are not streamed
- No pipelining so it takes longer to play

## Streaming Approach
```mermaid
sequenceDiagram
    participant Web_Browser as Web Browser
    participant Media_Player as Media Player
    participant Web_Server as Web Server

    Web_Browser->>Web_Server: (1) HTTP request/response for meta file
    Web_Server-->>Web_Browser: Meta file
    Web_Browser->>Media_Player: (2) Send meta file
    Media_Player->>Web_Server: (3) Request audio/video file
    Web_Server-->>Media_Player: Send audio/video file over HTTP
```

- Browser gets metafile
- Browser launches player and passed the metafile to the media player
- Media player contacts the server 
- Server streams the audio and video the player

## Streaming from a streaming server

```mermaid
sequenceDiagram
    participant Web_Browser as Web Browser
    participant Media_Player as Media Player
    participant Web_Server as Web Server
    participant Streaming_Server as Streaming Server

    Web_Browser->>Web_Server: (1) HTTP request/response for presentation description file
    Web_Server-->>Web_Browser: Presentation description file
    Web_Browser->>Media_Player: (2) Send presentation description file
    Media_Player->>Streaming_Server: (3) Request audio/video file
    Streaming_Server-->>Media_Player: Send audio/video file
   
```

- This allows for non-HTTP protocols between server and media player
- Can also use UDP instead of TCP
## Streaming Multimedia: UDP vs. TCP

### UDP (User Datagram Protocol)
- Server sends data at a fixed rate, ignoring network congestion.
- Typically, **send rate = encoding rate** (constant).
- **Packet loss** reduces effective fill rate.
- **Short playout delay** (2-5 seconds) to handle jitter.
- **Error recovery** is limited due to time constraints.

### TCP (Transmission Control Protocol)
- Adjusts send rate dynamically based on **TCP congestion control**.
- **Fill rate fluctuates**, causing variability in delivery.
- Requires a **larger playout delay** to smooth out transmission.
- **Better firewall compatibility** (e.g., HTTP/TCP easily passes firewalls).

### 🚀 Key Takeaway:
- **UDP** is preferred for real-time, low-latency streaming but may suffer from packet loss.
- **TCP** ensures reliable delivery but introduces higher latency and buffering.

# User Control of Streaming Media: RTSP vs. HTTP

## HTTP  
- **Not designed for multimedia streaming**.  
- Lacks commands for **rewind, fast forward, pause, resume, etc.**  

## RTSP (Real-Time Streaming Protocol) - RFC 2326  
- A **client-server protocol** for controlling media playback.  
- Supports **rewind, fast forward, pause, resume, and repositioning**.  

### **What RTSP Doesn't Do**  
- **Does not** define how audio/video is encapsulated for streaming.  
- **Does not** restrict transport protocols (can use **UDP or TCP**).  
- **Does not** specify how media players handle buffering.  

## **RTSP and "Out-of-Band" Control**  
- Similar to **FTP**, which separates data and control channels:  
  - **Data (file transfer) → One TCP connection**.  
  - **Control (commands) → Separate TCP connection**.  
- RTSP works the same way:  
  - **RTSP control messages** use a different port (Port **554**) → **Out-of-band**.  
  - **Media stream** is sent separately (Port **332**) → **In-band**.  

## **Key Takeaway**  
- **RTSP** is built for streaming, allowing users to control playback.  
- **HTTP** lacks media control features.  
- **RTSP uses separate channels for control and media streaming**, improving efficiency.  

## RSTP Operation
```mermaid
sequenceDiagram
    participant Web_Browser as Web Browser
    participant Web_Server as Web Server
    

    Web_Browser->>Web_Server: HTTP GET
    Web_Server-->>Web_Browser: Presentation Description

    
```

```mermaid
sequenceDiagram
	participant Media_Player as Media Player
    participant Media_Server as Media Server

	Media_Player->>Media_Server: SETUP
    Media_Server-->>Media_Player: Acknowledge

    Media_Player->>Media_Server: PLAY
    Media_Server-->>Media_Player: Media Stream

    Media_Player->>Media_Server: PAUSE
    Media_Server-->>Media_Player: Acknowledge

    Media_Player->>Media_Server: TEARDOWN
    Media_Server-->>Media_Player: Acknowledge
```

# Content distribution networks
```mermaid
graph TD;
    A[Origin Server in North America] --> B[CDN Distribution Node];
    B --> C[CDN Server in S. America];
    B --> D[CDN Server in Europe];
    B --> E[CDN Server in Asia];
```
## **What is a CDN?**

- A **Content Delivery Network (CDN)** like **Akamai** helps websites (e.g., **CNN**) deliver content faster.

- It **stores copies** of website content on multiple **CDN servers** worldwide.

- When content is updated, the **CDN updates all its servers**.

  

## **How Does a CDN Route Requests?**

1. The **CDN creates a "map"** showing the closest CDN servers to different Internet providers (ISPs).

2. When a user requests content, their **ISP is identified**.

3. The request is **sent to the nearest CDN server** based on the map.

4. This speeds up delivery and reduces **loading time**.

  

## **How Does a CDN Distribute Content?**

- The **origin server** (e.g., `www.foo.com`) provides the main webpage and links to images and media.

- Instead of storing images on the origin server, it **replaces** links like:
http://www.foo.com/sports.ruth.gif
**With a CDN link:**
http://www.cdn.com/www.foo.com/sports/ruth.gif
- The **CDN company (`cdn.com`)** stores and serves these files efficiently.
- A **CDN's DNS server** redirects users to the best CDN location.

## **Why Use a CDN?**
- **Faster website loading**  
- **Reduces server load**  
- **Improves reliability**  
- **Better performance for global users**  