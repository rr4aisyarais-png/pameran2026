
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Digital Art Exhibition</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, sans-serif;
  background: #f5f4f0;
  color: #222;
}

header {
  padding: 25px 8%;
  border-bottom: 1px solid #ddd;
}

header h2 {
  font-size: 18px;
  letter-spacing: 3px;
}

.container {
  max-width: 850px;
  margin: 50px auto;
  padding: 20px;
}

.artwork {
  background: white;
  padding: 25px;
  border-radius: 8px;
}

.artwork img {
  width: 100%;
  max-height: 550px;
  object-fit: contain;
  background: #eee;
}

.info {
  margin-top: 25px;
}

.info h1 {
  font-family: Georgia, serif;
  font-size: 32px;
  margin-bottom: 12px;
}

.artist {
  color: #777;
  margin-bottom: 25px;
}

.description {
  line-height: 1.8;
  font-size: 15px;
  white-space: pre-line;
}

.meta {
  margin-top: 25px;
  padding-top: 15px;
  border-top: 1px solid #ddd;
  color: #777;
  font-size: 13px;
}

.not-found {
  text-align: center;
  padding: 100px 20px;
}

footer {
  text-align: center;
  padding: 30px;
  font-size: 12px;
  color: #888;
}

</style>
</head>

<body>

<header>
  <h2>DIGITAL EXHIBITION</h2>
</header>

<main class="container" id="content"></main>

<footer>
  DIGITAL ART EXHIBITION © 2026
</footer>

<script>

// DATABASE KARYA
const artworks = {

  "karya001": {
    title: "Apa Kabar?",
    artist: "Raisya Salsabilla Dewanti",
    major: "Fotografi",
    year: "2026",
    image: "images/apa-kabar.jpg",
    description: `Telepon kabel menjadi salah satu
    media komunikasi yang pernah menghubungkan
    manusia dalam jarak yang terbatas.

    Sebelum teknologi berkembang seperti sekarang,
    percakapan harus dilakukan melalui perangkat
    yang terikat oleh kabel, jarak, dan biaya.

    Karya ini mengajak kita mengingat kembali
    bagaimana sederhana dan berharganya sebuah
    komunikasi pada masa itu.`
  },

  "karya002": {
    title: "Di Antara Waktu",
    artist: "Nama Peserta Kedua",
    major: "Fotografi",
    year: "2026",
    image: "images/karya-dua.jpg",
    description: `Tuliskan deskripsi karya kedua di sini.`
  },

  "karya003": {
    title: "Judul Karya Ketiga",
    artist: "Nama Peserta Ketiga",
    major: "Seni Rupa",
    year: "2026",
    image: "images/karya-tiga.jpg",
    description: `Tuliskan deskripsi karya ketiga di sini.`
  }

};

// MEMBACA ID DARI URL
const params = new URLSearchParams(window.location.search);
const id = params.get("id");

const content = document.getElementById("content");
const work = artworks[id];

if (work) {

  document.title = work.title + " | Digital Exhibition";

  content.innerHTML = `
    <article class="artwork">

      <img src="${work.image}"
           alt="${work.title}"
           onerror="this.style.display='none'">

      <div class="info">

        <h1>${work.title}</h1>

        <p class="artist">
          ${work.artist} · ${work.major}
        </p>

        <div class="description">
          ${work.description}
        </div>

        <div class="meta">
          Tahun: ${work.year}
          <br>
          ID Karya: ${id}
        </div>

      </div>
    </article>
  `;

} else {

  content.innerHTML = `
    <div class="not-found">
      <h2>Karya tidak ditemukan</h2>
      <p>Periksa kembali QR Code yang kamu pindai.</p>
    </div>
  `;

}

</script>

</body>
</html>
