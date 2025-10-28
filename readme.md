 ┌──────── GUI (Wayland) ────────┐         ┌──────── RDP Core (FreeRDP) ─────────┐
 │  Rust/GTK4 (or Qt)            │   IPC   │  libfreerdp3 + winpr                │
 │  - toolbar (connect, CAD)     ├────────►│  freerdp_new/ freerdp_connect()     │
 │  - profiles JSON              │  mpsc   │  event loop: freerdp_check_event()  │
 │  - window w/ GL area          ◄────────┤  frame callbacks → your renderer     │
 └───────────────────────────────┘         └──────────────────────────────────────┘
                ▲                                     │
                │ input events (kb/mouse/gamepad)     │ RDP input channel
                └─────────────────────────────────────►