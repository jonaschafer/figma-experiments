# Add Service Role Key to Fix Album Art Issue

## The Problem
Your album art and track data aren't showing because of Row Level Security (RLS) policies in Supabase.

## The Solution
Add your Supabase service role key to your `.env.local` file:

1. Go to your Supabase dashboard: https://supabase.com/dashboard
2. Select your project
3. Go to Settings > API
4. Copy the "service_role" key (NOT the anon key)
5. Add this line to your `.env.local` file:

```
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key_here
```

6. Restart your dev server:
```bash
cd prototypes/wall-of-sound
npm run dev
```

## Why This Fixes It
The service role key bypasses RLS policies, allowing the API routes to read/write data on behalf of authenticated users.

## Security Note
Keep the service role key secret - it has admin access to your database!
