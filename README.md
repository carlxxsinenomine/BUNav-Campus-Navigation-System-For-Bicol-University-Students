# BUNav - Bicol University Navigation System

<p align="center">
  <img src="public/BUNav_logo.svg" width="150" alt="BUNav Logo">
</p>

A full-stack, React-based 3D campus navigation application built with Mapbox GL, Node.js, and MongoDB. BUNav provides students, faculty, and visitors with interactive mapping, turn-by-turn directions, real-time location tracking, and an extensive directory of buildings and points of interest across Bicol University campuses.

---

## Key Features

- **Interactive 3D Map**: Fluid, high-performance map rendering powered by Mapbox GL.
- **Turn-by-turn Navigation**: Integrated Mapbox Directions API for calculating exact routes (Walking, Cycling, Driving) between any two points.
- **Building Directory & Information**: Search and navigate to specific buildings. Add descriptions and metadata to any building using the interactive UI.
- **Custom Points of Interest (POI)**: Drop custom colored pins anywhere on the map (e.g., parking, restrooms, canteens) and save them to the database. Toggle specific locations (like Gates or the CS Canteen) instantly via the POI List Panel.
- **Real-time GPS Tracking**: Follow your movement live on the map while navigating.
- **Global Search**: Quickly find gates, campuses, and individual buildings using the dynamic search bar.
- **Secure & Rate-Limited API**: Backend endpoints are secured with `express-rate-limit` to prevent DoS attacks and database spamming.
- **Persistent Storage**: Uses Express and MongoDB to save all custom buildings, POIs, and user-generated map data.

---

## Technology Stack

**Frontend:**
- **React 19** - UI Framework
- **Vite** - Build Tool & Dev Server
- **Mapbox GL JS** - 3D Map Rendering
- **@mapbox/mapbox-gl-draw** - Map drawing tools
- **@turf/turf** - Advanced geospatial analysis

**Backend & Database:**
- **Node.js + Express** - REST API Server
- **MongoDB + Mongoose** - Database and schema modeling
- **dotenv & cors & express-rate-limit** - Environment, security, and rate limiting middlewares

---

## Project Architecture

The codebase has been meticulously modularized for scalability and easy maintenance:

```text
BUNav/
├── server.js                    # Express backend server
├── check_db.cjs                 # Utility script to initialize/check MongoDB
├── public/                      
│   ├── BUNav_logo.svg           # Application logo
│   └── vite.svg                 
├── src/
│   ├── components/              # UI Components
│   │   ├── Three3DMap.jsx       # Main container coordinating map & hooks
│   │   ├── SearchBar.jsx        # Search functionality
│   │   ├── MapToolbar.jsx       # Vertical action toolbar
│   │   ├── NavigationPanel.jsx  # HUD for active routing instructions
│   │   ├── PoiListPanel.jsx     # Side panel for toggling POI visibility
│   │   ├── Snackbar.jsx         # Custom toast notifications
│   │   └── Modals/Popups        # AppInfoModal, DisclaimerModal, BuildingInfoModal, PoiModal, BuildingPopup
│   ├── hooks/                   # Custom business logic hooks
│   │   ├── useNavigation.js     # Routing and active trip tracking
│   │   ├── usePoi.js            # Dropping and managing Points of Interest
│   │   ├── useBuildingInfo.js   # Updating building metadata
│   │   ├── useBuildingSelection.js # Managing active selections
│   │   └── useSnackbar.js       # Toast state management
│   ├── utils/
│   │   └── geoUtils.js          # Turf.js distance and coordinate utilities
│   ├── main.jsx                 # React DOM mount point
│   └── index.css                # Global styles
├── .env                         # Environment variables (API keys, DB URI)
└── package.json                 # Dependencies
