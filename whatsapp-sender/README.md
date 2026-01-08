# WhatsApp Daily Message Sender

Send your daily spiritual images + text messages to multiple WhatsApp groups safely.

**Sends BOTH image and text message separately (like you currently do manually)**

---

## 📋 Prerequisites

You need to install **Node.js** on your computer first.

### Windows:
1. Go to https://nodejs.org/
2. Download the **LTS** version (recommended)
3. Run the installer, click Next through all steps
4. Restart your computer

### To verify installation:
Open Command Prompt (CMD) or Terminal and type:
```
node --version
```
You should see something like `v18.17.0` or higher.

---

## 🚀 Step-by-Step Setup

### Step 1: Download the Project

Create a folder on your computer (e.g., `C:\whatsapp-sender` on Windows or `~/whatsapp-sender` on Mac/Linux)

Place these files in the folder:
- `index.js`
- `package.json`
- `daily-message.txt`

### Step 2: Open Terminal/Command Prompt

**Windows:**
- Press `Win + R`, type `cmd`, press Enter
- Navigate to your folder: `cd C:\whatsapp-sender`

**Mac/Linux:**
- Open Terminal
- Navigate to your folder: `cd ~/whatsapp-sender`

### Step 3: Install Dependencies

Run this command:
```
npm install
```

Wait for it to complete (may take 1-2 minutes).

### Step 4: Get Your Group List

Run this command:
```
node index.js list
```

1. A QR code will appear in the terminal
2. Open WhatsApp on your phone
3. Go to **Settings > Linked Devices > Link a Device**
4. Scan the QR code
5. Wait for "WhatsApp client is ready!"
6. You'll see a list of all your groups

### Step 5: Configure Your Groups

Open `index.js` in any text editor (Notepad, VS Code, etc.)

Find this section and add your group names:
```javascript
const TARGET_GROUPS = [
    'Group Name 1',
    'Group Name 2',
    'Group Name 3',
    // Add all 13 group names here
];
```

**Example:**
```javascript
const TARGET_GROUPS = [
    'வள்ளலார் குறுஞ்செய்திகள்',
    'Spiritual Family',
    'Tamil Devotional',
    'Daily Quotes Group',
    // ... add all your groups
];
```

**Note:** You don't need exact names - partial match works!
- If your group is "🙏 வள்ளலார் குறுஞ்செய்திகள் 🙏"
- You can just write "வள்ளலார் குறுஞ்செய்திகள்"

---

## 📅 Daily Usage (Every Day)

### Step 1: Update Your Image
- Replace `daily-image.png` with your new image
- Keep the same filename OR rename your new image to `daily-image.png`

### Step 2: Update Your Message
Open `daily-message.txt` in Notepad and replace the content with today's message:

```
பொது விதி - 9.4:

கேழ்வரகு, வரகு, தினை, சாமை, பருப்புவகை முதலிய விலக்குகளை நீக்குதல்.

- திருவருட்பிரகாச வள்ளலார்
(நித்திய கரும விதி - பொது விதி)
```

### Step 3: Send
Open terminal/CMD in the folder and run:
```
node index.js send
```

**What happens:**
1. Sends IMAGE to Group 1
2. Sends TEXT MESSAGE to Group 1
3. Waits 30-90 seconds (random)
4. Repeats for all 13 groups
5. Total time: ~10-15 minutes

---

## 📁 Files You Need Daily

| File | Purpose |
|------|---------|
| `daily-image.png` | Your image for today |
| `daily-message.txt` | Your text message for today |

Just update these 2 files every day before running `node index.js send`

---

## ⚠️ Safety Tips

1. **Don't send more than once per day** to the same groups
2. **Run manually** - don't set up auto-scheduling
3. **Keep delays enabled** - don't reduce the delay times
4. **Stop if you see warnings** from WhatsApp

---

## 🔧 Troubleshooting

### "QR code keeps appearing"
- Delete the `.wwebjs_auth` folder and try again
- Make sure WhatsApp is open on your phone

### "Group not found"
- Run `node index.js list` to see exact group names
- Check spelling in TARGET_GROUPS

### "Image not found"
- Make sure the image is in the same folder
- Check the filename matches CONFIG.imagePath

### "puppeteer error" (common on first install)
Run these commands:
```
npm install puppeteer --save
```

If on Linux, you may need:
```
sudo apt-get install -y libgbm-dev
```

---

## 📁 Files Explained

```
whatsapp-sender/
├── index.js          # Main script
├── package.json      # Dependencies
├── daily-image.png   # Your image (add this)
├── groups-list.json  # Auto-generated group list
└── .wwebjs_auth/     # Auto-generated login data (don't delete)
```

---

## 🙏 For Your Spiritual Service

This tool is designed for sending meaningful content like Vallalar's teachings.
Use it responsibly and spread positivity!

வள்ளலார் அருள் பெருக! 🙏
