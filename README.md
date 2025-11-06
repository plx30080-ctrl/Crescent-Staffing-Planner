# Crescent Staffing Planner

A compact, cloud-enabled staffing management tool for production environments. Built for managers who need to quickly staff 120+ associates per shift with auto-save and remote access capabilities.

## Features

### Compact Design
- **Table-based layout** - Maximizes visible associates on screen
- **Inline editing** - Type names directly into positions
- **Small fonts & tight spacing** - Optimized for high-density data entry
- **Responsive design** - Works on tablets and computers

### Staffing Management
- **Direct name input** - Simply type associate names into position slots
- **New associate checkbox** - Mark first-day associates with one click
- **Waitlist integration** - Separate waitlist section within the same table
- **Date & shift tracking** - Every staffing sheet is saved with date and shift
- **Real-time stats** - See filled positions, new hires, and waitlist count at a glance

### Cloud Sync & Remote Access
- **Auto-save** - Changes automatically save 2 seconds after editing
- **Firebase integration** - Cloud storage for remote access
- **Local fallback** - Works offline with localStorage
- **Reporting tab** - View and download historical staffing data

### Additional Features
- **Core associates management** - Pre-configure regular team members
- **Export functionality** - Download staffing data as JSON
- **Multiple shifts** - Support for Day, Night, and Swing shifts
- **Production line setup** - Configure multiple lines with leads

## Quick Start

1. **Open the file** - Simply open `index.html` in any modern web browser
2. **Go to Setup tab** - Configure your production lines
3. **Start Staffing** - Begin entering associate names
4. **Auto-save** - Your changes save automatically

## Firebase Setup (For Cloud Sync)

To enable cloud storage and remote access, you need to configure Firebase:

### Step 1: Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project" or "Create a project"
3. Enter a project name (e.g., "crescent-staffing")
4. Click Continue through the setup wizard
5. Choose "Default Account for Firebase" for Google Analytics
6. Click "Create project"

### Step 2: Create a Web App

1. In your Firebase project, click the Web icon (</>)
2. Enter an app nickname (e.g., "Staffing Planner")
3. **DO NOT** check "Also set up Firebase Hosting"
4. Click "Register app"
5. Copy the Firebase configuration object (it will look like this):

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789012",
  appId: "1:123456789012:web:abcdef1234567890"
};
```

### Step 3: Enable Firestore Database

1. In Firebase Console, go to "Build" > "Firestore Database"
2. Click "Create database"
3. Choose "Start in **test mode**" (for initial setup)
4. Select a location (choose closest to your facility)
5. Click "Enable"

**IMPORTANT**: For production use, configure proper security rules:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /staffing/{document=**} {
      allow read, write: if true; // Change this for production!
    }
  }
}
```

### Step 4: Configure the Application

1. Open `index.html` in a text editor
2. Find the `FIREBASE_CONFIG` section (around line 494)
3. Replace the placeholder values with your Firebase config:

```javascript
const FIREBASE_CONFIG = {
    apiKey: "YOUR_API_KEY_HERE",
    authDomain: "your-project.firebaseapp.com",
    projectId: "your-project-id",
    storageBucket: "your-project.appspot.com",
    messagingSenderId: "123456789012",
    appId: "1:123456789012:web:abcdef1234567890"
};
```

4. Save the file
5. Refresh the page in your browser

### Step 5: Verify It's Working

1. Open the staffing planner
2. If Firebase is configured correctly, you **will NOT** see the yellow warning banner
3. When you make changes, you should see "Saved to cloud ✓" in the top right
4. Check Firebase Console > Firestore Database to see your saved data

## Usage Guide

### Setting Up a Shift

1. **Go to Setup tab**
2. Enter production line information:
   - Line Letter (A, B, C, etc.)
   - Line Lead name
   - Number of associates needed
3. Click "Add Another Line" for multiple lines
4. Click "Start Staffing"

### Staffing Associates

1. **Select Date & Shift** at the top of the staffing view
2. **Type names** directly into the position slots
3. **Check "New" box** for first-day associates
4. Changes auto-save after 2 seconds

### Managing Waitlist

1. Scroll to the **WAITLIST** section at the bottom
2. Click **"+ Add"** to add a new waitlist entry
3. Type the associate's name
4. Check "New" if applicable
5. Click **×** to remove from waitlist

### Viewing Reports

1. Go to **Reports tab**
2. Click any saved shift to view details
3. Click **"Load into Staffing"** to edit a previous shift
4. Reports show filled positions, new hires, and waitlist

### Managing Core Associates

1. Go to **Core Team tab**
2. Select an existing lead or enter a new one
3. Add core associates with optional notes
4. Core associates can be pre-loaded when setting up shifts (optional)

## Browser Compatibility

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Data Storage

- **Without Firebase**: Data stored in browser localStorage (local only)
- **With Firebase**: Data synced to cloud (accessible from any device)
- **Auto-save**: Triggers 2 seconds after last change
- **Manual export**: Available via Export button

## Security Notes

⚠️ **For Production Use**:
1. Configure Firebase security rules
2. Consider adding authentication
3. Use environment-specific Firebase projects
4. Regular backups recommended

## Support

For issues or questions:
- Check browser console for error messages
- Verify Firebase configuration
- Ensure internet connection for cloud sync
- Test with different browsers if issues persist

## Technical Details

- **Framework**: React 18 (via CDN)
- **Database**: Firebase Firestore
- **Fallback**: Browser localStorage
- **File size**: Single HTML file (~50KB)
- **Dependencies**: None (all loaded via CDN)

---

**Version**: 2.0
**Last Updated**: 2025
**License**: Proprietary - Crescent Staffing
