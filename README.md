from zipfile import ZipFile
import os

# Membuat folder sementara
folder_name = "/mnt/data/website-bio"
os.makedirs(folder_name, exist_ok=True)

# HTML: index.html
index_html = """<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fadhil - Beranda</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Halo, Saya Fadhil</h1>
        <p>A girl who still chasing her dreams</p>
        <nav>
            <a href="index.html">Beranda</a>
            <a href="about.html">Tentang</a>
            <a href="portfolio.html">Portfolio</a>
            <a href="contact.html">Kontak</a>
        </nav>
    </header>
    <main>
        <section>
            <h2>Selamat Datang!</h2>
            <p>Website ini berisi informasi tentang saya, hobi, dan karya yang saya buat.</p>
        </section>
    </main>
    <footer>
        <p>© 2025 Fadhil. All rights reserved.</p>
    </footer>
</body>
</html>
"""

# HTML: about.html
about_html = """<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tentang Saya</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
<header>
    <h1>Tentang Saya</h1>
    <nav>
        <a href="index.html">Beranda</a>
        <a href="about.html">Tentang</a>
        <a href="portfolio.html">Portfolio</a>
        <a href="contact.html">Kontak</a>
    </nav>
</header>
<main>
    <section>
        <h2>Profil Singkat</h2>
        <p>Nama panggilan saya adalah Fadhil. Hobi saya bermain dan menganalisis keuangan. Saat ini saya bersekolah di SMAN 16 Jakarta. Moto hidup saya adalah: <i>"A girl who still chasing her dreams"</i>.</p>
    </section>
</main>
<footer>
    <p>© 2025 Fadhil. All rights reserved.</p>
</footer>
</body>
</html>
"""

# HTML: portfolio.html
portfolio_html = """<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
<header>
    <h1>Portfolio</h1>
    <nav>
        <a href="index.html">Beranda</a>
        <a href="about.html">Tentang</a>
        <a href="portfolio.html">Portfolio</a>
        <a href="contact.html">Kontak</a>
    </nav>
</header>
<main>
    <section>
        <h2>Karya & Pencapaian</h2>
        <ul>
            <li>Proyek Analisis Keuangan</li>
            <li>Presentasi Suara Demokrasi di Sekolah</li>
            <li>Penjualan Cireng Balado</li>
        </ul>
    </section>
</main>
<footer>
    <p>© 2025 Fadhil. All rights reserved.</p>
</footer>
</body>
</html>
"""

# HTML: contact.html
contact_html = """<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kontak</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
<header>
    <h1>Kontak</h1>
    <nav>
        <a href="index.html">Beranda</a>
        <a href="about.html">Tentang</a>
        <a href="portfolio.html">Portfolio</a>
        <a href="contact.html">Kontak</a>
    </nav>
</header>
<main>
    <section>
        <h2>Hubungi Saya</h2>
        <p>Email: <a href="mailto:fadhil@example.com">fadhil@example.com</a></p>
        <p>Instagram: @sapta_nada</p>
    </section>
</main>
<footer>
    <p>© 2025 Fadhil. All rights reserved.</p>
</footer>
</body>
</html>
"""

# CSS: style.css
style_css = """body {
    font-family: Arial, sans-serif;
    margin: 0;
    background-color: white;
    color: #333;
}

header {
    background-color: #005f99;
    color: white;
    padding: 20px;
    text-align: center;
}

header nav a {
    color: gold;
    margin: 0 10px;
    text-decoration: none;
}

header nav a:hover {
    text-decoration: underline;
}

main {
    padding: 20px;
}

footer {
    background-color: #005f99;
    color: white;
    text-align: center;
    padding: 10px;
    position: fixed;
    width: 100%;
    bottom: 0;
}
"""

# JS: script.js
script_js = """console.log("Website Fadhil aktif!");"""

# Menyimpan file ke folder
with open(os.path.join(folder_name, "index.html"), "w", encoding="utf-8") as f:
    f.write(index_html)

with open(os.path.join(folder_name, "about.html"), "w", encoding="utf-8") as f:
    f.write(about_html)

with open(os.path.join(folder_name, "portfolio.html"), "w", encoding="utf-8") as f:
    f.write(portfolio_html)

with open(os.path.join(folder_name, "contact.html"), "w", encoding="utf-8") as f:
    f.write(contact_html)

with open(os.path.join(folder_name, "style.css"), "w", encoding="utf-8") as f:
    f.write(style_css)

with open(os.path.join(folder_name, "script.js"), "w", encoding="utf-8") as f:
    f.write(script_js)

# Membuat file ZIP
zip_path = "/mnt/data/website-bio.zip"
with ZipFile(zip_path, "w") as zipf:
    for root, dirs, files in os.walk(folder_name):
        for file in files:
            zipf.write(os.path.join(root, file), os.path.relpath(os.path.join(root, file), folder_name))

zip_path
