# WhatsApp Daily Message Sender

Send daily spiritual images + text messages to multiple WhatsApp groups safely, with support for multiple languages.

**Sends image with caption in a single message to each group**

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

### Step 1: Download or Clone the Project

Create a folder on your computer (e.g., `C:\whatsapp-sender` on Windows or `~/whatsapp-sender` on Mac/Linux)

The project should have these files:
- `index.js` - Main script
- `package.json` - Dependencies configuration
- `README.md` - This file

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

### Step 4: Set Up Language Folders

The script supports multiple languages. For each language, create a folder structure:

```
whatsapp-sender/
├── tamil/
│   ├── tamil.txt          # Your Tamil message
│   └── [any-name].jpg     # Your Tamil image (any .jpg file)
└── english/
    ├── english.txt        # Your English message
    └── [any-name].jpg     # Your English image (any .jpg file)
```

**Important:**
- The message file must be named exactly as configured: `tamil.txt` or `english.txt`
- The image can have any name, as long as it's a `.jpg` file

### Step 5: Get Your Group List

Run this command:
```
node index.js list
```

1. A QR code will appear in the terminal
2. Open WhatsApp on your phone
3. Go to **Settings > Linked Devices > Link a Device**
4. Scan the QR code
5. Wait for "WhatsApp client is ready!"
6. You'll see a list of all your groups with their IDs

The groups will be saved to `groups-list.json` for reference.

### Step 6: Configure Your Groups by Language

Create two JSON files for your group lists:

**`groups-tamil-list.json`** - Groups that should receive Tamil messages:
```json
[
    {
        "name": "Tamil Group 1",
        "id": "1234567890-1234567890@g.us"
    },
    {
        "name": "Tamil Group 2",
        "id": "1234567890-1234567890@g.us"
    }
]
```

**`groups-english-list.json`** - Groups that should receive English messages:
```json
[
    {
        "name": "English Group 1",
        "id": "1234567890-1234567890@g.us"
    },
    {
        "name": "English Group 2",
        "id": "1234567890-1234567890@g.us"
    }
]
```

Copy the exact group IDs from `groups-list.json` that was generated in Step 5.

---

## 📅 Daily Usage (Every Day)

### Step 1: Update Your Tamil Content
In the `tamil/` folder:
- Update or replace the `.jpg` image file with today's Tamil image
- Update `tamil.txt` with today's Tamil message

### Step 2: Update Your English Content
In the `english/` folder:
- Update or replace the `.jpg` image file with today's English image
- Update `english.txt` with today's English message

**Example message format (tamil.txt):**
```
பொது விதி - 9.4:

கேழ்வரகு, வரகு, தினை, சாமை, பருப்புவகை முதலிய விலக்குகளை நீக்குதல்.

- திருவருட்பிரகாச வள்ளலார்
(நித்திய கரும விதி - பொது விதி)
```

### Step 3: Send Messages
Open terminal/CMD in the folder and run:
```
node index.js send
```

**What happens:**
1. Validates all configurations (files exist, not empty)
2. For English groups:
   - Sends IMAGE + CAPTION to English Group 1
   - Waits 30-90 seconds (random)
   - Repeats for all English groups
3. For Tamil groups:
   - Sends IMAGE + CAPTION to Tamil Group 1
   - Waits 30-90 seconds (random)
   - Repeats for all Tamil groups
4. Total time depends on number of groups (~1-2 minutes per group)

---

## 📁 Project Structure

```
whatsapp-sender/
├── index.js                      # Main script
├── package.json                  # Dependencies
├── README.md                     # This file
├── .gitignore                    # Git ignore rules
├── groups-tamil-list.json        # Tamil groups configuration
├── groups-english-list.json      # English groups configuration
├── groups-list.json              # Generated list of all groups
├── tamil/
│   ├── tamil.txt                 # Daily Tamil message
│   └── [date]-tamil.jpg          # Daily Tamil image
├── english/
│   ├── english.txt               # Daily English message
│   └── [date]-english.jpg        # Daily English image
├── .wwebjs_auth/                 # Auto-generated (WhatsApp session)
└── .wwebjs_cache/                # Auto-generated (WhatsApp cache)
```

---

## 🎯 Features

- **Multi-language Support**: Send different messages to different group sets
- **Image with Caption**: Sends image and text as a single combined message
- **Safety Delays**: Random delays (30-90 seconds) between groups
- **Validation**: Checks all files before sending
- **Easy Configuration**: Simple JSON files for group management
- **Persistent Login**: Saves WhatsApp session (no need to scan QR every time)

---

## ⚠️ Safety Tips

1. **Don't send more than once per day** to the same groups
2. **Run manually** - don't set up auto-scheduling
3. **Keep delays enabled** - don't reduce the delay times
4. **Stop if you see warnings** from WhatsApp
5. **Test first** with one or two groups before sending to all

---

## ⚙️ Configuration

You can modify the delays and language order in [index.js](index.js) if needed:

```javascript
const CONFIG = {
    minDelay: 30000,  // 30 seconds minimum
    maxDelay: 90000,  // 90 seconds maximum

    // Language configurations (ordered - English first, then Tamil)
    languages: [
        {
            name: 'english',
            groupListFile: './groups-english-list.json',
            folder: './english',
            messageFile: 'english.txt'
        },
        {
            name: 'tamil',
            groupListFile: './groups-tamil-list.json',
            folder: './tamil',
            messageFile: 'tamil.txt'
        }
    ]
};
```

**Note:** Messages are sent in the order listed above (English first, then Tamil).

---

## 🔧 Troubleshooting

### "QR code keeps appearing"
- Delete the `.wwebjs_auth` folder and try again
- Make sure WhatsApp is open on your phone
- Ensure your phone has a stable internet connection

### "Group not found"
- Run `node index.js list` to get the latest group list
- Check that the group IDs in your JSON files are correct
- Make sure you copied the exact ID from `groups-list.json`

### "Image not found" or "Message file not found"
- Check that the folder exists: `tamil/` or `english/`
- Ensure the message file is named correctly: `tamil.txt` or `english.txt`
- Verify there's at least one `.jpg` file in the folder

### "Message file is empty"
- Open the text file and add your message
- Make sure you saved the file after editing

### "puppeteer error" (common on first install)
Run this command:
```
npm install puppeteer --save
```

If on Linux, you may need additional dependencies:
```
sudo apt-get install -y libgbm-dev
```

### Commands not working on Windows
Make sure you're using Command Prompt (CMD) or PowerShell, not Git Bash.

---

## 📝 npm Scripts

For convenience, you can also use npm scripts:

```bash
# List all groups
npm run list

# Send messages
npm run send
```

---

## 🙏 For Your Spiritual Service

This tool is designed for sending meaningful content like Vallalar's teachings.
Use it responsibly and spread positivity!

வள்ளலார் அருள் பெருக! 🙏
