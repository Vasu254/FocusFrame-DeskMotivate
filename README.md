# FocusFrame-DeskMotivate

# 🎯 Goal Wallpaper App

A beautiful desktop application that helps you stay focused on your daily goals by automatically updating your desktop wallpaper with your goal list!

![Goal Wallpaper App](https://img.shields.io/badge/Electron-App-blue) ![MongoDB](https://img.shields.io/badge/MongoDB-Database-green) ![Express](https://img.shields.io/badge/Express-Backend-red)

## 🌟 Features

### ✨ **Core Functionality**
- **📝 Goal Management**: Add, edit, and delete your daily goals
- **🖼️ Automatic Wallpaper Updates**: Your goals are overlaid on your desktop wallpaper
- **💾 Persistent Storage**: Goals are saved to MongoDB database
- **📅 Date-based Organization**: Goals are organized by date

### 🎨 **Customization Options**
- **🎨 Text Color**: Choose any color for your goal text
- **📏 Text Size**: Small, Medium, Large, or Extra Large text
- **🌈 Background Themes**: 
  - Default image background
  - Blue gradient
  - Purple gradient  
  - Ocean gradient

### 🚀 **User Experience**
- **Modern UI**: Beautiful, responsive interface with gradient backgrounds
- **Real-time Updates**: Wallpaper updates instantly when goals are saved
- **Goal History**: Load and view previous goals
- **Smart Notifications**: Desktop notifications for successful updates

## 🏗️ Architecture

### **Frontend (Electron)**
```
📁 renderer/
├── index.html          # Main UI with modern CSS styling
└── (preload.js)        # Secure communication bridge
```

### **Backend (Express + MongoDB)**
```
📁 backend/
├── server.js           # Express server with REST API
├── db.js              # MongoDB connection setup
└── models/
    └── Goal.js        # Mongoose schema for goals
```

### **Core Utilities**
```
📁 utils/
└── wallpaper-generator.js    # Sharp-based image processing
```

## 🛠️ How It Works

### **Workflow Overview**
1. **User Input**: Enter goals in the Electron app's beautiful interface
2. **Data Storage**: Goals are sent to Express backend and saved to MongoDB
3. **Image Processing**: Sharp library overlays goal text onto background image
4. **Wallpaper Update**: New wallpaper is automatically set as desktop background
5. **Persistence**: Settings and goals are saved for future sessions

### **Technical Flow**
```
┌─────────────────┐    HTTP POST    ┌─────────────────┐
│   Electron UI   │ ──────────────> │  Express Server │
│  (Frontend)     │                 │   (Backend)     │
└─────────────────┘                 └─────────────────┘
         │                                   │
         │ IPC Communication                 │ MongoDB
         ▼                                   ▼
┌─────────────────┐                 ┌─────────────────┐
│ Wallpaper Gen   │                 │    Database     │
│   (Sharp.js)    │                 │   (Goals +      │
└─────────────────┘                 │   Settings)     │
         │                          └─────────────────┘
         ▼
┌─────────────────┐
│ Desktop         │
│ Wallpaper       │
│ (OS Level)      │
└─────────────────┘
```

## 📋 Prerequisites

### **Required Software**
- **Node.js** (v14 or higher) - [Download here](https://nodejs.org/)
- **MongoDB** (Community Server) - [Download here](https://www.mongodb.com/try/download/community)
- **Windows OS** (Currently optimized for Windows)

### **Verify Installation**
```bash
# Check Node.js
node --version

# Check npm
npm --version

# Check MongoDB (after installation)
mongod --version
```

## 🚀 Installation & Setup

### **Step 1: Clone/Download Project**
```bash
# If using git
git clone <repository-url>
cd goal-wallpaper-app

# Or download and extract ZIP file
```

### **Step 2: Install Dependencies**
```bash
# Install Node.js packages
npm install
```

### **Step 3: Setup MongoDB**

#### **Option A: Windows Service (Recommended)**
```bash
# Start MongoDB service
net start MongoDB
```

#### **Option B: Manual Start**
```bash
# Create data directory (if doesn't exist)
mkdir C:\data\db

# Start MongoDB manually
mongod --dbpath "C:\data\db"
```

### **Step 4: Create Default Wallpaper**
```bash
# Generate default background image
node create-default-wallpaper.js
```

## 🎮 Running the Application

### **Method 1: Two Terminal Setup (Recommended)**

#### **Terminal 1: Start Backend Server**
```bash
cd backend
node server.js
```
**Expected Output:**
```
Server running on port 3000
Connected to MongoDB
```

#### **Terminal 2: Start Electron App**
```bash
# From project root directory
npm start
```

### **Method 2: Using npm Scripts**
```bash
# Start backend (in one terminal)
npm run backend

# Start frontend (in another terminal)  
npm start
```

## 🎯 Using the Application

### **Setting Goals**
1. **Open the app** - Beautiful gradient interface will appear
2. **Enter your goals** in the textarea (one goal per line)
3. **Customize appearance**:
   - Choose text color with color picker
   - Select text size (Small/Medium/Large/Extra Large)
   - Pick background theme (Default/Blue/Purple/Ocean)
4. **Click "Set Goals"** - Wallpaper updates automatically!

### **Managing Goals**
- **📂 Load Today's Goals**: Click "Load Today's Goals" to retrieve saved goals
- **✏️ Edit Goals**: Click "Edit" next to any goal in the list
- **🗑️ Delete Goals**: Click "Delete" to remove specific goals
- **🧹 Clear All**: Use "Clear All" to start fresh

### **Example Goals**
```
• Exercise for 30 minutes
• Read 20 pages of a book  
• Learn something new about programming
• Drink 8 glasses of water
• Call a friend or family member
• Complete 3 work tasks
• Practice meditation for 10 minutes
```

## 🛠️ Configuration

### **Default Settings**
- **Port**: 3000 (Backend server)
- **Database**: Local MongoDB (mongodb://localhost:27017/goalwallpaper)
- **Wallpaper Resolution**: 1920x1080
- **Text Color**: White (#ffffff)
- **Text Size**: 32px (Medium)

### **Customization Options**
```javascript
// In wallpaper-generator.js, you can modify:
- Background colors
- Text positioning  
- Font families
- Image resolution
- Text effects
```

## 📁 Project Structure

```
goal-wallpaper-app/
├── 📄 README.md                    # This file
├── 📄 package.json                 # Dependencies and scripts
├── 📄 main.js                      # Electron main process
├── 📄 preload.js                   # Electron preload script
├── 📄 create-default-wallpaper.js  # Wallpaper creation utility
├── 🖼️ default_wallpaper.jpg        # Default background image
├── 🖼️ current_wallpaper.jpg        # Generated wallpaper (auto-created)
│
├── 📁 backend/                     # Express.js backend
│   ├── 📄 server.js               # REST API server
│   ├── 📄 db.js                   # MongoDB connection
│   └── 📁 models/
│       └── 📄 Goal.js             # Goal data model
│
├── 📁 renderer/                    # Electron frontend  
│   └── 📄 index.html              # Main UI with CSS/JS
│
└── 📁 utils/
    └── 📄 wallpaper-generator.js   # Image processing logic
```

## 🔧 API Endpoints

### **Backend REST API**
- **GET** `/goals` - Retrieve all goals
- **POST** `/goals` - Save new goals with settings
- **GET** `/goals/:date` - Get goals for specific date
- **DELETE** `/goals/:date` - Delete goals for specific date

### **Electron IPC Channels**
- `update-wallpaper` - Process wallpaper update with goals and settings
- `show-notification` - Display desktop notification

## 🐛 Troubleshooting

### **Common Issues & Solutions**

#### **MongoDB Won't Start**
```bash
# Solution 1: Create data directory
mkdir C:\data\db

# Solution 2: Check if service exists
sc query MongoDB

# Solution 3: Start manually
mongod --dbpath "C:\data\db"
```

#### **Electron App Won't Launch**
```bash
# Solution 1: Install Electron globally
npm install -g electron

# Solution 2: Clear cache and reinstall
rm -rf node_modules
npm install
```

#### **Wallpaper Not Updating**
- Check if `default_wallpaper.jpg` exists in project root
- Verify backend server is running on port 3000
- Check console (F12) for JavaScript errors
- Ensure proper write permissions in project directory

#### **Backend Connection Failed**
- Verify MongoDB is running: `sc query MongoDB`
- Check port 3000 is not in use by another application
- Test API directly: `http://localhost:3000/goals`

### **Debug Mode**
```bash
# Run with debug output
DEBUG=* npm start

# Check backend logs
cd backend && node server.js

# View Electron console
# Press F12 in the Electron app window
```

## 🎨 Customization Guide

### **Adding New Background Themes**
1. Edit `utils/wallpaper-generator.js`
2. Add new color in the `colors` object
3. Add option in `renderer/index.html` select dropdown

### **Changing Text Styles**
```javascript
// In wallpaper-generator.js, modify the SVG style:
.title { 
  fill: ${textColor}; 
  font-size: ${textSize}px; 
  font-family: 'Your Custom Font', Arial, sans-serif; 
  font-weight: bold;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.5); // Add shadow
}
```

### **Custom Wallpaper Dimensions**
```javascript
// Modify in wallpaper-generator.js:
create: {
  width: 2560,  // Your screen width
  height: 1440, // Your screen height
  channels: 3,
  background: colors[backgroundType]
}
```

## 📖 Technology Stack

- **🖥️ Electron** - Cross-platform desktop app framework
- **⚡ Express.js** - Fast, minimalist web framework  
- **🍃 MongoDB** - NoSQL document database
- **🏗️ Mongoose** - MongoDB object modeling
- **🖼️ Sharp** - High-performance image processing
- **🎨 CSS3** - Modern styling with gradients and animations
- **📱 HTML5** - Semantic markup structure

## 🚀 Future Enhancements

### **Planned Features**
- [ ] **📱 Mobile companion app**
- [ ] **☁️ Cloud sync across devices**  
- [ ] **📊 Goal completion tracking**
- [ ] **🎨 Custom image uploads**
- [ ] **⏰ Scheduled wallpaper updates**
- [ ] **📈 Progress analytics**
- [ ] **🎯 Goal categories and priorities**
- [ ] **🔄 Auto-start with Windows**

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📞 Support

If you encounter any issues:
1. Check the troubleshooting section above
2. Look for error messages in the console (F12)
3. Verify all prerequisites are installed
4. Check that MongoDB service is running

---

**🎯 Stay focused, achieve your goals, and let your desktop wallpaper remind you of what matters most!**

