# Wall of Sound - Setup Guide

## 1. 📍 .env.local File Location

Create the `.env.local` file in the **root of the wall-of-sound project** (same level as package.json):

```
prototypes/wall-of-sound/.env.local
```

**Contents:**
```bash
# Supabase
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key

# Spotify API
SPOTIFY_CLIENT_ID=your_spotify_client_id
SPOTIFY_CLIENT_SECRET=your_spotify_client_secret
```

## 2. 🗄️ How to Run SQL Schema in Supabase

### Step 1: Create Supabase Project
1. Go to [supabase.com](https://supabase.com)
2. Sign up/login and create a new project
3. Wait for the database to initialize

### Step 2: Run SQL Schema
1. In your Supabase dashboard, go to **SQL Editor** (left sidebar)
2. Click **"New Query"**
3. Copy and paste this SQL:

```sql
-- Create the songs table
create table songs (
  id bigint primary key generated always as identity,
  created_at timestamp with time zone default now(),
  spotify_url text,
  spotify_track_id text,
  album_art text,
  artist text,
  title text,
  genre text,
  description text,
  odesli_url text,
  preview_url text
);

-- Enable Row Level Security
alter table songs enable row level security;

-- Create policy to allow all operations for authenticated users
create policy "Enable all operations for authenticated users" on songs
for all using (auth.role() = 'authenticated');
```

4. Click **"Run"** button
5. You should see "Success. No rows returned" message

### Step 3: Get Your Credentials
1. Go to **Settings** → **API** in your Supabase dashboard
2. Copy your **Project URL** and **anon public** key
3. Paste them into your `.env.local` file

## 3. 🎵 Spotify API Setup

### Step 1: Create Spotify App
1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Log in with your Spotify account
3. Click **"Create app"**
4. Fill in:
   - **App name**: "Wall of Sound"
   - **App description**: "Music collection app"
   - **Website**: `http://localhost:3000` (for development)
   - **Redirect URI**: `http://localhost:3000` (for development)
   - Check **Web API**

### Step 2: Get Credentials
1. Click on your new app
2. Click **"Settings"**
3. Copy **Client ID** and **Client Secret**
4. Paste them into your `.env.local` file

## 4. 🚀 Running the Project

```bash
# Navigate to the project
cd prototypes/wall-of-sound

# Install dependencies
npm install

# Run development server
npm run dev
```

Then open http://localhost:3000

## 5. 📁 Final Project Structure

```
prototypes/wall-of-sound/
├── .env.local              # ← CREATE THIS FILE HERE
├── package.json
├── next.config.js
├── app/
├── components/
├── lib/
└── public/
```

## 6. 🎨 Optional: Add Figma Header

1. In Figma, select the "wall of sound" header design
2. Export as SVG or PNG
3. Save as `prototypes/wall-of-sound/public/wall-of-sound-header.svg`
4. Uncomment the `<img>` tag in `components/MusicWall.js`

## 🔧 Troubleshooting

**"Module not found" errors**: Run `npm install`

**Supabase connection errors**: Check your URL and key in `.env.local`

**Spotify API errors**: Verify your Client ID and Secret

**Database errors**: Make sure you ran the SQL schema in Supabase

---

🎵 **You're ready to build your wall of sound!**
