# 🔧 TROUBLESHOOTING GUIDE - Fixing "npm run dev" Error

## The Error You're Seeing

```
npm error Missing script: "dev"
```

## Why This Happens

This error means npm can't find the "dev" script in your package.json file. This usually happens when:
1. package.json is missing or corrupted
2. You're in the wrong folder
3. Files weren't extracted properly

## ✅ SOLUTION - Step by Step

### Step 1: Make Sure You're in the Right Folder

Open PowerShell/Terminal and check:
```bash
# See where you are
pwd

# You should see something like:
# C:\Users\ADMIN\Downloads\vision-final
```

If you're NOT in the vision-final folder:
```bash
cd vision-final
```

### Step 2: Check if package.json Exists

```bash
# Windows PowerShell
dir package.json

# Mac/Linux
ls package.json
```

If it says "file not found", the extraction failed.

### Step 3: Delete node_modules (if it exists)

```bash
# Windows PowerShell
Remove-Item -Recurse -Force node_modules

# Mac/Linux  
rm -rf node_modules
```

### Step 4: Install Dependencies Again

```bash
npm install
```

Wait for it to finish. You should see a progress bar.

### Step 5: Run the Dev Server

```bash
npm run dev
```

## 🎯 If Still Not Working - Fresh Start

### Option A: Re-extract the ZIP

1. Delete the vision-final folder completely
2. Re-extract the ZIP file
3. Open terminal in the NEW folder
4. Run: `npm install`
5. Run: `npm run dev`

### Option B: Check Your package.json

Open `package.json` in a text editor. It should look like this:

```json
{
  "name": "vision-international",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.20.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.43",
    "@types/react-dom": "^18.2.17",
    "@vitejs/plugin-react": "^4.2.1",
    "vite": "^5.0.8"
  }
}
```

If it looks different or has errors, copy the above code and paste it into package.json.

## Common Issues

### Issue: "command not found: npm"
**Fix:** Install Node.js from https://nodejs.org

### Issue: "Cannot find module vite"
**Fix:** 
```bash
npm install
```

### Issue: "Port 5173 already in use"
**Fix:** Close other terminals or use:
```bash
npm run dev -- --port 3000
```

### Issue: Still getting errors
**Fix:** Try these commands in order:
```bash
# 1. Remove old files
rm -rf node_modules package-lock.json

# 2. Clear npm cache
npm cache clean --force

# 3. Install again
npm install

# 4. Run dev server
npm run dev
```

## ✅ What Success Looks Like

When it works, you'll see:

```
VITE v5.0.8  ready in 500 ms

➜  Local:   http://localhost:5173/
➜  Network: use --host to expose
➜  press h + enter to show help
```

Then open: http://localhost:5173

## 🆘 Still Stuck?

### Check These:

1. ✅ Are you in the right folder? (`pwd` to check)
2. ✅ Did `npm install` complete without errors?
3. ✅ Is Node.js installed? (`node --version` to check)
4. ✅ Is package.json present? (`ls package.json`)

### Get the Folder Structure Right:

```
vision-final/
├── package.json          ← Must be here!
├── vite.config.js        ← Must be here!
├── index.html            ← Must be here!
└── src/
    ├── main.jsx
    ├── App.jsx
    ├── components/
    ├── pages/
    └── styles/
```

If any of these are missing, re-extract the ZIP.

## Quick Command Reference

```bash
# Navigate to folder
cd vision-final

# Install packages
npm install

# Run development server
npm run dev

# Stop the server
Ctrl + C

# Check Node.js version
node --version

# Check npm version
npm --version
```

---

**Remember:** The most common issue is being in the wrong folder! Always check with `pwd` first.

If everything else fails, download the ZIP again and start fresh. Sometimes files get corrupted during download/extraction.
