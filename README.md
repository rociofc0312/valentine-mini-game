# Love Quest - Valentine Mini Game

A multi-level game to ask someone to be your Valentine!

## How to Test Locally

Simply open `index.html` in your browser:

```bash
open /Users/rociofc/Development/Personal/valentine-mini-game/index.html
```

## Customize the Game

Open `index.html` and find the section marked `===== CUSTOMIZE HERE =====` (around line 340).

### 1. Trivia Questions

Replace the placeholder questions and answers:

```javascript
const TRIVIA_QUESTIONS = [
  { q: "Where was our first date?", a: "the park", hint: "It was outdoors" },
  { q: "What's my favorite movie?", a: "inception", hint: "It's about dreams" },
  { q: "What did I order on our first dinner?", a: "pasta", hint: "Italian food" },
  { q: "What's our song?", a: "perfect", hint: "Ed Sheeran" },
  { q: "What's my pet's name?", a: "luna", hint: "Something celestial" },
];
```

**Important:** Answers are case-insensitive, so "The Park" matches "the park".

### 2. Lovedle Word

Change the 5-letter word for the final Wordle-style game:

```javascript
const LOVEDLE_WORD = "HEART"; // Must be exactly 5 letters
```

Ideas: A pet name, inside joke, meaningful place, etc.

### 3. Final Message

Customize the message revealed piece by piece:

```javascript
const MESSAGE_PIECES = [
  "You",                      // Revealed after Level 1
  "are the best thing",       // Revealed after Level 2
  "that ever happened",       // Revealed after Level 3
  "to me.",                   // Revealed after Level 4
  "I love you so much!"       // Revealed after Level 5
];
```

### 4. Prize Photos

Each level completion reveals a photo. To set up:

**Step 1:** Upload photos to Google Drive

**Step 2:** For each photo:
1. Right-click > Share > "Anyone with the link"
2. Copy the link (looks like: `https://drive.google.com/file/d/ABC123/view`)
3. Convert it to direct link format:
   - Original: `https://drive.google.com/file/d/ABC123/view`
   - Direct: `https://drive.google.com/uc?export=view&id=ABC123`

**Step 3:** Add to the code:

```javascript
const PRIZE_PHOTOS = [
  {
    url: "https://drive.google.com/uc?export=view&id=YOUR_FILE_ID_1",
    caption: "That photo you always asked for..."
  },
  {
    url: "https://drive.google.com/uc?export=view&id=YOUR_FILE_ID_2",
    caption: "Remember this day?"
  },
  // ... add all 5 photos
];
```

**Note:** The photos are technically accessible if someone finds the links in the source code, but they'd have to actively look for them. For most purposes, this provides reasonable privacy through obscurity.

## Deploy (Free Hosting)

### Option 1: Netlify (Easiest - Drag & Drop)

1. Go to [netlify.com](https://netlify.com) and sign up
2. Click "Add new site" > "Deploy manually"
3. Drag the entire `valentine-mini-game` folder into the browser
4. Done! You'll get a URL like `random-name.netlify.app`
5. (Optional) Click "Site settings" > "Change site name" to customize

### Option 2: GitHub Pages

1. Create a new repository on GitHub
2. Push this folder to the repo:
   ```bash
   cd /Users/rociofc/Development/Personal/valentine-mini-game
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/valentine-mini-game.git
   git push -u origin main
   ```
3. Go to repo Settings > Pages
4. Set Source to "main" branch, folder "/ (root)"
5. Your site will be at `YOUR_USERNAME.github.io/valentine-mini-game`

### Option 3: Vercel

1. Go to [vercel.com](https://vercel.com) and sign up
2. Click "Add New" > "Project"
3. Import your GitHub repo (or drag & drop the folder)
4. Done! You'll get a URL like `valentine-mini-game.vercel.app`

## Features

- **5 Progressive Levels:**
  1. Heart Catcher - Catch hearts, avoid broken ones
  2. Memory Match - Match pairs before time runs out
  3. Maze - Navigate through fog to find the envelope
  4. Trivia - Answer questions about your relationship
  5. Lovedle - Guess the secret word (Wordle-style)

- **Progress System:**
  - Auto-saves to browser storage
  - Love Code for cross-device progress
  - Level select screen

- **Extras:**
  - Teasing fail messages
  - Message revealed piece by piece
  - Confetti on final screen
  - Only "YES" and "OF COURSE" buttons at the end

## Love Code System

Players can save their progress with a code like `LOVE-3-ABCD`:
- First number = current level
- Letters = unique session identifier

They can enter this code on any device to continue where they left off.

---

Good luck! May they say YES!
