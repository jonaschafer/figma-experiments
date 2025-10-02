# Supabase Setup - Table Already Exists Fix

## ✅ Good News: Your `songs` table already exists!

The error "relation 'songs' already exists" means the table is already created. Now we just need to ensure the security policies are set up correctly.

## 🔧 Run This Query Instead

In your Supabase SQL Editor, run **only the security parts**:

```sql
-- Enable Row Level Security (if not already enabled)
ALTER TABLE songs ENABLE ROW LEVEL SECURITY;

-- Drop existing policy if it exists, then create new one
DROP POLICY IF EXISTS "Enable all operations for authenticated users" ON songs;

CREATE POLICY "Enable all operations for authenticated users" ON songs
FOR ALL USING (auth.role() = 'authenticated');
```

## 📋 Verify Your Table Structure

Run this query to check if your table has all the right columns:

```sql
SELECT column_name, data_type 
FROM information_schema.columns 
WHERE table_name = 'songs' 
ORDER BY ordinal_position;
```

**Expected columns:**
- id (bigint)
- created_at (timestamp with time zone)
- spotify_url (text)
- spotify_track_id (text)
- album_art (text)
- artist (text)
- title (text)
- genre (text)
- description (text)
- odesli_url (text)
- preview_url (text)

## 🚀 Next Steps

1. ✅ Run the security policy query above
2. ✅ Get your Supabase credentials:
   - Go to **Settings** → **API**
   - Copy **Project URL** and **anon public key**
   - Add them to your `.env.local` file
3. ✅ Set up Spotify API credentials
4. ✅ Run `npm install && npm run dev`

## 🔍 Test Your Setup

After running the app, try:
1. Sign up for a new account
2. Add a track with a Spotify URL
3. Check if it appears in your Supabase database

If you get any auth errors, the policies might need adjustment.
