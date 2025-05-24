# README content
readme_md = """# No War Landing Page

This is a public GitHub Pages-ready landing page template designed to:
- Embed your project (e.g., Padlet or homepage)
- Block visitors from aggressor countries (Russia, Belarus, China, North Korea)
- Show a message in multiple languages
- Auto-redirect them after 8 seconds
- Open the Universal Declaration of Human Rights

## Deploy instructions

1. Fork or use this template on GitHub.
2. Upload the files (`index.html` and this README).
3. Go to **Settings > Pages**, select branch `main`, folder `/root`.
4. Done – your page is now live.

## Credits

Built with HTML, JavaScript and `ipapi.co` for geolocation.

License: MIT
"""

# Save files
with open(os.path.join(base_path, "index.html"), "w", encoding="utf-8") as f:
    f.write(index_html)

with open(os.path.join(base_path, "README.md"), "w", encoding="utf-8") as f:
    f.write(readme_md)

# Create zip
zip_path = f"/mnt/data/{repo_name}.zip"
with ZipFile(zip_path, 'w') as zipf:
    for root, dirs, files in os.walk(base_path):
        for file in files:
            full_path = os.path.join(root, file)
            arcname = os.path.relpath(full_path, base_path)
            zipf.write(full_path, arcname)

zip_path
