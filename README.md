# Call Centre Staff Dashboard and Calling Demo

## Overview

A React front-end for a call centre operations dashboard with a real browser-to-browser WebRTC calling demo and a browser voice-assistant demo.

## Dashboard Features

- Summary metrics for team size, current availability, calls handled, and average CSAT.
- Search by staff name, role, team, or extension; filter by availability and sort by name or calls handled.
- Change a staff member's availability directly from their card or profile.
- Open staff profiles to view their team, extension, shift, call volume, and CSAT score.
- Responsive layout and 12 sample staff profiles. All dashboard data is in-memory mock data and resets on refresh.
- Human-to-human calling over WebRTC between two tabs in the same browser, with live camera and microphone.
- AI-to-human voice-assistant demo with browser speech output and scripted billing/support-hours responses.

## Tech Stack

- React (Create React App)
- Browser WebRTC, BroadcastChannel, and Web Speech APIs (no added packages)
- CSS styling (no UI component dependencies required)

## Setup Instructions

1. Clone the repository.
2. Run `npm install`.
3. Run `npm start`.
4. Open `http://localhost:3000` in your browser.

## AI Tools Used

- Microsoft Copilot (for step-by-step guidance and UI improvements)

## Calling demo

1. Run `npm install` and `npm start`, then open `http://localhost:3000`.
2. For human-to-human calling, leave **Human call** selected, enter the same room name in two tabs of the same browser, and select **Join live call** in both. Allow camera and microphone access and use headphones.
3. For the voice-assistant demo, select **AI voice call**, select **Start AI call**, then use **Speak** if browser speech recognition is available or type and send a reply.

The human call uses real camera/microphone streams and peer-to-peer WebRTC. BroadcastChannel is only used to exchange connection setup messages between tabs; no signaling server, TURN/STUN service, or external media server is configured. It is a same-browser demo and does not connect separate devices or browsers. Browser permission prompts and secure-context requirements apply (localhost or HTTPS). A second tab may not be able to acquire the camera on every device/browser.

The voice assistant uses browser speech synthesis and fixed, local intent responses; it is not connected to an LLM or call-centre backend. Browser speech recognition may send audio to the browser vendor for transcription. No recording or persistent transcript storage is implemented.

See [CALLING_IMPLEMENTATION.txt](./CALLING_IMPLEMENTATION.txt) for the end-to-end process, implementation details, and limitations.

## Notes

- This project uses sample data (`src/staffData.js`) only; no backend is connected.
- Main components: `src/App.js`, `src/components/StaffList.js`, and `src/components/StaffCard.js`.
- Calling demo: `src/components/CallPanel.js`.
