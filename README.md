# 📹 Gothwad Meet

> **Modern, High-Performance, Zero-Backend Real-Time Video & Audio Conferencing App**  
> Google Meet jaisi seamless styling aur low-latency WebRTC peer-to-peer architecture ke saath, Cloudflare Pages aur modern web browsers ke liye fully optimized.

---

## 🌟 Key Highlights & Features (Khoobiyan)

- **⚡ Real-Time HD Video & Audio**: Peer-to-peer WebRTC mesh network through PeerJS for ultra-low latency calls.
- **🎨 Google Meet-Style Clean UI**:
  - Dark mode (`#212121`) & Light mode switchable theme.
  - Floating responsive control bar.
  - Active speaker detection with glowing visual waves and audio level analyzer.
- **🚪 Green Room (Preview Lobby)**:
  - Join karne se pehle camera, mic aur audio volume meter check karein.
  - Virtual background blur aur filter preview.
  - Front / back camera (mobile device) toggle.
- **🖥️ Screen Sharing**: One-click screen and application window sharing with audio support.
- **💬 Real-Time In-Meeting Chat**: Instant messaging with participant names, timestamps, and notification chimes.
- **👥 Participants & Host Controls**:
  - Participant list with active mic/cam status indicators.
  - Pin participant tile to spotlight.
  - Host controls: Mute participants, toggle chat permissions, screen sharing permissions.
- **📝 Collaborative Whiteboard**:
  - Live drawing canvas with multiple brush colors, brush sizes, eraser, and clear board.
- **🎭 Visual Effects**:
  - Background blur (standard & intense).
  - Virtual photo backgrounds.
- **💬 Live Closed Captions (Speech-to-Text)**:
  - Real-time speech recognition for live meeting subtitles.
- **🎉 Floating Emoji Reactions**:
  - Heart, thumbs up, clapping, laughing, celebration with canvas confetti particle animations.
- **📐 Flexible Layouts**:
  - **Tiled View**: Auto-arranges all participants dynamically.
  - **Spotlight View**: Maximizes active speaker or pinned participant.
  - **Sidebar View**: Large stage with participant strip on the right.
- **☁️ Zero-Backend Architecture**:
  - Fully static single-page application (SPA).
  - `public/_redirects` included for Cloudflare Pages SPA client-side routing.
  - No database or backend server required for basic meetings.

---

## 🛠️ Tech Stack

- **Framework**: [React 19](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/)
- **Bundler & Dev Server**: [Vite 8](https://vite.dev/)
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **Real-Time Communication**: [WebRTC](https://webrtc.org/) & [PeerJS](https://peerjs.com/)
- **Animations & Effects**: [Motion](https://motion.dev/) & [canvas-confetti](https://www.npmjs.com/package/canvas-confetti)
- **Icons**: [Lucide React](https://lucide.dev/)

---

## 🚀 Quick Start (Local Setup)

### 1. Repository Clone Karein
```bash
git clone https://github.com/GothwadTech/Mm.git
cd Mm
```

### 2. Dependencies Install Karein
```bash
npm install
```

> **Note**: `.npmrc` file already included hai jisme `legacy-peer-deps=true` set hai, jisse dependency conflicts nahi aate.

### 3. Development Server Start Karein
```bash
npm run dev
```
Dev server start ho jayega: `http://localhost:3000`

### 4. Production Build Test Karein
```bash
npm run build
npm run preview
```

---

## ☁️ Cloudflare Pages Par Deploy Karne Ka Tarika

Gothwad Meet ko **Cloudflare Pages** par deploy karna behad aasan hai:

### Step 1: Cloudflare Dashboard me Jayein
1. [Cloudflare Dashboard](https://dash.cloudflare.com/) open karein.
2. **Workers & Pages** -> **Create Application** -> **Pages** -> **Connect to Git** select karein.
3. Apna GitHub repository (`GothwadTech/Mm` ya `meet`) select karein.

### Step 2: Build Settings Configure Karein
Neeche diye gaye settings enter karein:

| Setting | Value |
|---|---|
| **Framework preset** | `Vite` |
| **Build command** | `npm run build` |
| **Build output directory** | `dist` |
| **Root directory** | `/` (leave empty) |

### Step 3: Environment Variables (Optional)
Agar aap koi custom variables use kar rahe hain:
- `NODE_VERSION`: `20` ya `22`

### Step 4: Save and Deploy
- **Save and Deploy** button par click karein.
- 1-2 minute me aapki meeting app live ho jayegi!
- `public/_redirects` file pehle se configured hai (`/* /index.html 200`), jisse direct meeting URLs (jaise `https://your-domain.pages.dev/?room=abc-defg-hij`) perfectly route honge without 404 error.

---

## 📁 Project Directory Structure

```text
├── public/
│   └── _redirects              # Cloudflare Pages SPA client-side routing
├── src/
│   ├── components/
│   │   ├── ActivitiesPanel.tsx # Whiteboard & meeting tools panel
│   │   ├── CallEnded.tsx       # Meeting exit & rejoin screen
│   │   ├── CaptionsOverlay.tsx # Live speech-to-text subtitles
│   │   ├── ChangeLayoutModal.tsx# Tiled / Spotlight / Sidebar layout selector
│   │   ├── ChatPanel.tsx       # In-meeting real-time chat
│   │   ├── CloudflareGuideModal.tsx # Built-in Cloudflare deployment guide
│   │   ├── ControlBar.tsx      # Bottom floating meeting controls
│   │   ├── GreenRoom.tsx       # Camera & Mic preview lobby
│   │   ├── HomeLobby.tsx       # Landing page (Start/Join meeting)
│   │   ├── HostControlsModal.tsx# Meeting moderation settings
│   │   ├── InfoPanel.tsx       # Room details & invite link copy
│   │   ├── MeetingRoom.tsx     # Main video conference stage
│   │   ├── Navbar.tsx          # App header & settings trigger
│   │   ├── PeoplePanel.tsx     # Participants list & pin controls
│   │   ├── ReactionsOverlay.tsx# Floating emoji reactions & confetti
│   │   ├── SettingsModal.tsx   # Audio/Video device selection modal
│   │   ├── VideoTile.tsx       # Responsive participant video tile
│   │   ├── VisualEffectsModal.tsx # Background blur & virtual backgrounds
│   │   └── WhiteboardModal.tsx # Interactive drawing canvas
│   ├── types/
│   │   └── meet.ts             # TypeScript interfaces
│   ├── utils/
│   │   ├── audioAnalyser.ts    # Web Audio API volume level detection
│   │   ├── sounds.ts           # Meeting join/leave/message sound effects
│   │   ├── speechRecognition.ts# Web Speech API wrapper for captions
│   │   └── webrtc.ts           # PeerJS signaling & stream connection helpers
│   ├── App.tsx                 # Root application screen manager
│   ├── index.css               # Global styles & Tailwind v4
│   └── main.tsx                # React entry point
├── .env.example                # Example environment variables
├── .npmrc                      # npm resolution flags (legacy-peer-deps)
├── metadata.json               # Applet capabilities & permissions
├── package.json                # Project dependencies & scripts
├── tsconfig.json               # TypeScript compiler config
└── vite.config.ts              # Vite configuration (port 3000, 0.0.0.0)
```

---

## 🔒 Permissions & Security

Application browser se neeche di gayi permissions request karti hai:
- **Camera (`camera`)**: Video streaming aur background effects ke liye.
- **Microphone (`microphone`)**: Audio streaming aur speech captions ke liye.
- **Screen Capture (`display-capture`)**: Screen sharing functionality ke liye.

---

## 🤝 Contribution & License

Contributions welcome hain! Koi bhi bug fix ya naya feature add karne ke liye Pull Request (PR) open karein.

Developed with ❤️ by **GothwadTech**.
