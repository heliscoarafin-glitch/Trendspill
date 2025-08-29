
YOUR BLOG STARTER — Quick Guide
================================

1) Rename
---------
- Replace "Your Blog Name" across HTML files.
- Update the logo at assets/favicon.svg (keep the same filename for simplicity).

2) Add a Post
-------------
- Edit posts/posts.json and add a new item with fields:
  - slug: "your-new-post"
  - title: "Your Post Title"
  - excerpt: one sentence teaser
  - date: YYYY-MM-DD
  - read: minutes to read (number)
  - category: e.g., "News", "Tips", "Opinion"
- Create posts/your-new-post.json with:
  {"title": "Your Post Title", "date": "2025-08-29", "read": 3, "category": "News", "html": "<p>Your HTML content here</p>"}

3) Run Locally
--------------
- Use any static server (VS Code Live Server, Python's http.server) then open http://localhost:PORT
  Example: python3 -m http.server

4) Deploy (Free)
----------------
- Netlify: Drag-and-drop the folder in the Netlify dashboard.
- Vercel: `vercel` in the folder (auto-detects static site).
- GitHub Pages: Push to a repo and enable Pages on the main branch / root.

5) Hook a Form
--------------
- Replace the contact form's onsubmit handler with your service endpoint (Formspree, Getform, Basin, etc.).

6) Customize
------------
- Colors, spacing, and layout live in assets/styles.css.
- You can add analytics (Plausible, Umami) by dropping their script into <head>.

Happy publishing!
