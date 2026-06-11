# Resume Folder

## Instructions

Add your resume PDF file to this folder with the following name:

```
Niharika_Suru_Resume.pdf
```

This file will be automatically linked to all "Download Resume" buttons on the portfolio website.

## File Naming Convention

If you want to use a different filename, update the following files:
- `index.html` - Search for `Niharika_Suru_Resume.pdf` and replace with your filename

## Supabase Setup (Optional)

To enable the contact form backend:

1. Create a free Supabase account at https://supabase.com
2. Create a new project
3. Go to the SQL Editor and run:

```sql
CREATE TABLE contact_submissions (
  id SERIAL PRIMARY KEY,
  first_name TEXT,
  last_name TEXT,
  email TEXT,
  company TEXT,
  message TEXT,
  submitted_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Enable Row Level Security
ALTER TABLE contact_submissions ENABLE ROW LEVEL SECURITY;

-- Create policy to allow inserts from anonymous users
CREATE POLICY "Allow anonymous inserts" ON contact_submissions
  FOR INSERT
  TO anon
  WITH CHECK (true);
```

4. Go to Project Settings > API
5. Copy your Project URL and anon/public key
6. Update `index.html`:
   - Replace `YOUR_SUPABASE_URL` with your Project URL
   - Replace `YOUR_SUPABASE_ANON_KEY` with your anon key
