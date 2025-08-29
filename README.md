# Trendspill
A worldwide blog network.
# Rebuild the blog starter files after reset, then re-zip.

import os, json, textwrap, zipfile, datetime

base = "/mnt/data/blog-starter"
assets = os.path.join(base, "assets")
posts_dir = os.path.join(base, "posts")
os.makedirs(assets, exist_ok=True)
os.makedirs(posts_dir, exist_ok=True)

now = datetime.date.today().strftime("%B %d, %Y")

# Minimal essential files for regeneration

# index.html
index_html = f"""<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Your Blog Name</title>
</head>
<body>
  <h1>Welcome to Your Blog</h1>
  <p>Launched {now}</p>
  <p><a href="about.html">About</a> | <a href="contact.html">Contact</a></p>
</body>
</html>
"""
with open(os.path.join(base, "index.html"), "w") as f:
    f.write(index_html)

# about.html
with open(os.path.join(base, "about.html"), "w") as f:
    f.write("<h1>About</h1><p>This is your about page.</p>")

# contact.html
with open(os.path.join(base, "contact.html"), "w") as f:
    f.write("<h1>Contact</h1><p>Contact form coming soon.</p>")

# post.html
with open(os.path.join(base, "post.html"), "w") as f:
    f.write("<h1>Post Page</h1><p>Post content will load here.</p>")

# sample posts.json
posts_index = [
    {
        "slug": "welcome-post",
        "title": "Welcome to Your Blog",
        "excerpt": "A quick hello post.",
        "date": "2025-08-01",
        "read": 2,
        "category": "Intro"
    }
]
with open(os.path.join(posts_dir, "posts.json"), "w") as f:
    json.dump(posts_index, f, indent=2)

# sample post file
welcome_post = {
  "title": "Welcome to Your Blog",
  "date": "2025-08-01",
  "read": 2,
  "category": "Intro",
  "html": "<p>This is your first post!</p>"
}
with open(os.path.join(posts_dir, "welcome-post.json"), "w") as f:
    json.dump(welcome_post, f, indent=2)

# Zip it again
zip_path = "/mnt/data/blog-starter.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for folder, _, files in os.walk(base):
        for file in files:
            full = os.path.join(folder, file)
            rel = os.path.relpath(full, base)
            z.write(full, arcname=f"blog-starter/{rel}")

zip_path
