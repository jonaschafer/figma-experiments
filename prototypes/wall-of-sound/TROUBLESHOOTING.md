# Wall of Sound - Troubleshooting Guide

## 🎵 **Issue: Empty Album Art & Missing Track Info**

**Problem**: When you add a Spotify track, the album shows up empty with no artist, title, or cover art.

**Cause**: Missing Spotify API credentials in `.env.local`

### **Fix: Add Spotify API Credentials**

1. **Go to Spotify Developer Dashboard**: https://developer.spotify.com/dashboard
2. **Create a new app**:
   - App name: "Wall of Sound"
   - App description: "Music collection app"
   - Website: `http://localhost:3000`
   - Redirect URI: `http://localhost:3000`
   - Check **Web API**

3. **Get your credentials**:
   - Click on your app → **Settings**
   - Copy **Client ID** and **Client Secret**

4. **Add to `.env.local`**:
```bash
# Supabase (you already have these)
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_key

# Add these Spotify credentials
SPOTIFY_CLIENT_ID=your_client_id_here
SPOTIFY_CLIENT_SECRET=your_client_secret_here
```

5. **Restart the server**:
```bash
# Stop current server (Ctrl+C)
npm run dev
```

## 🖼️ **Issue: Missing Header Image**

**Problem**: The "wall of sound" header shows as text instead of the stylized design.

**Fix**: Export the header from Figma and add it to your project:

1. **In Figma**: Select the "wall of sound" header design
2. **Export as SVG or PNG**
3. **Save as**: `prototypes/wall-of-sound/public/wall-of-sound-header.svg`
4. **Update the code**: The image tag is already in the code but commented out

**Or keep the text version**: The current text header "«« wall of sound »»" looks good too!

## 🧪 **Test Your Fix**

After adding Spotify credentials:

1. **Add a new track** with a Spotify URL like:
   ```
   https://open.spotify.com/track/4iV5W9uYEdYUVa79Axb7Rh
   ```

2. **You should see**:
   - ✅ Album cover art
   - ✅ Artist name
   - ✅ Song title
   - ✅ Genre and description you added

## 🔍 **Still Having Issues?**

Check the browser console (F12 → Console) for error messages. Common issues:

- **"Failed to fetch Spotify data"**: Wrong Client ID/Secret
- **"Network error"**: Server isn't running
- **"Unauthorized"**: Supabase credentials issue

## 🎯 **Quick Test URLs**

Try these Spotify URLs to test:
- https://open.spotify.com/track/4iV5W9uYEdYUVa79Axb7Rh (Mr. Brightside)
- https://open.spotify.com/track/0VjIjW4GlULA4LGwqf0YVk (Blinding Lights)

---

**Once you add the Spotify credentials, your wall of sound will come alive with beautiful album art and track info!** 🎵
