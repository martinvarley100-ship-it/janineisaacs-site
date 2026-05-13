# janineisaacs.com — CMS Setup Instructions

## Current draft URL
https://janineisaacsdraft.netlify.app

## Admin login (once set up)
https://janineisaacsdraft.netlify.app/admin

---

## One-time setup — do this once, takes about 15 minutes

### Step 1 — Put the site on GitHub
1. Go to github.com and sign in (or create a free account)
2. Click the + button → New repository
3. Name it: janineisaacs-site
4. Leave it Public, click Create repository
5. Upload all the site files to that repository (drag and drop works)

### Step 2 — Connect Netlify to your GitHub repo
1. In your Netlify dashboard, open the janineisaacsdraft site
2. Go to: Site configuration → Build & deploy → Link repository
3. Choose GitHub, find janineisaacs-site
4. Set build command: (leave blank)
5. Set publish directory: /  (just a forward slash)
6. Click Deploy

### Step 3 — Enable Netlify Identity
1. In Netlify dashboard → Identity tab
2. Click "Enable Identity"
3. Under Registration preferences: select "Invite only"
4. Scroll down to "Invite users" and invite: janine@janineisaacs.com
5. Janine will receive an email to set a password — she must do this before logging in

### Step 4 — Enable Git Gateway
1. Still in the Identity tab
2. Scroll to Services → Git Gateway
3. Click "Enable Git Gateway"

### Step 5 — Log in to the editor
1. Go to: https://janineisaacsdraft.netlify.app/admin
2. Log in with your email and the password you set
3. You will see the content editor

---

## When DNS moves to janineisaacs.com

Update one line in admin/config.yml — change:
  site_url: https://janineisaacsdraft.netlify.app
to:
  site_url: https://janineisaacs.com

Or delete the site_url lines entirely and Netlify will detect it automatically.
The admin will then be at: https://janineisaacs.com/admin

---

## Using the editor

### Add a testimonial
1. Go to /admin → click Testimonials in the left menu
2. Click the + button to add a new entry
3. Fill in: Client name, Short pull-quote, Full text
4. Click Publish — it saves to GitHub and goes live within a minute

### Write a Reflection (blog post)
1. Go to /admin → click Reflections in the left menu
2. Click New Reflection
3. Fill in title, date, short excerpt, full body text
4. Click Publish

### Edit page copy
1. Go to /admin → Page copy
2. Choose which page to edit
3. Make changes and click Publish

---

## Adding a blog post manually (if CMS is not yet set up)

Create a file in data/posts/ named YYYY-MM-DD-short-title.json with this content:

{
  "title": "Your post title here",
  "date": "2026-05-01",
  "excerpt": "One or two sentences shown in the listing.",
  "body": "First paragraph.\n\nSecond paragraph.\n\nThird paragraph."
}

Then re-upload the site folder to Netlify.
