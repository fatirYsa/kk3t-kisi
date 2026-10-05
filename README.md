Konten dibuat oleh pengguna dan belum diverifikasi.


220
Pelajari tentang artifacts
<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Latihan Soal UTS — Pengelolaan Website</title>
<style>
:root{
  --bg:#f6f4ee;
  --panel:#ffffff;
  --ink:#1c2521;
  --muted:#5c6a63;
  --line:#dfe3d8;
  --accent:#2f6f4f;
  --accent-ink:#ffffff;
  --wrong:#b3453a;
  --wrong-bg:#fbeae7;
  --correct:#2f6f4f;
  --correct-bg:#e7f2ea;
  --chip:#eef1e8;
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px);
  padding-bottom:env(safe-area-inset-bottom,0px);
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --bg:#14201a;
    --panel:#1b2921;
    --ink:#eef3ec;
    --muted:#a9b8ac;
    --line:#324237;
    --accent:#5cae83;
    --accent-ink:#0d1712;
    --wrong:#e2837a;
    --wrong-bg:#3a201d;
    --correct:#5cae83;
    --correct-bg:#1e3327;
    --chip:#233129;
  }
}
:root[data-theme="dark"]{
  --bg:#14201a;
  --panel:#1b2921;
  --ink:#eef3ec;
  --muted:#a9b8ac;
  --line:#324237;
  --accent:#5cae83;
  --accent-ink:#0d1712;
  --wrong:#e2837a;
  --wrong-bg:#3a201d;
  --correct:#5cae83;
  --correct-bg:#1e3327;
  --chip:#233129;
}
html{scroll-padding-top:env(safe-area-inset-top,0px);}
*{box-sizing:border-box;}
body{
  margin:0;
  background:var(--bg);
  color:var(--ink);
  font-family:"Source Serif 4","Georgia",serif;
  min-height:100%;
}
.wrap{
  max-width:720px;
  margin:0 auto;
  padding:20px 16px 64px;
}
header.top{
  position:sticky;
  top:env(safe-area-inset-top,0px);
  background:var(--bg);
  padding:10px 0 12px;
  z-index:5;
  border-bottom:1px solid var(--line);
}
h1{
  font-size:1.15rem;
  margin:0 0 2px;
  font-weight:700;
  letter-spacing:.01em;
}
.sub{color:var(--muted);font-size:.85rem;margin:0 0 10px;font-family:system-ui,sans-serif;}
.progress-row{display:flex;align-items:center;gap:10px;font-family:system-ui,sans-serif;font-size:.82rem;color:var(--muted);}
.bar{flex:1;height:6px;border-radius:3px;background:var(--line);overflow:hidden;}
.bar > div{height:100%;background:var(--accent);width:0%;transition:width .25s ease;}
.scorepill{
  font-family:system-ui,sans-serif;
  font-size:.78rem;
  background:var(--chip);
  color:var(--ink);
  padding:3px 10px;
  border-radius:999px;
  white-space:nowrap;
}

.card{
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:14px;
  padding:22px 20px 20px;
  margin-top:18px;
}
.qnum{font-family:system-ui,sans-serif;font-size:.78rem;color:var(--accent);font-weight:600;margin-bottom:6px;}
.qtext{font-size:1.08rem;line-height:1.5;margin:0 0 16px;}
.options{display:flex;flex-direction:column;gap:9px;}
.opt{
  display:flex;
  align-items:flex-start;
  gap:10px;
  text-align:left;
  border:1px solid var(--line);
  background:transparent;
  color:var(--ink);
  border-radius:10px;
  padding:11px 13px;
  font-family:system-ui,sans-serif;
  font-size:.95rem;
  line-height:1.4;
  cursor:pointer;
  transition:border-color .15s ease, background .15s ease;
}
.opt:hover:not(:disabled){border-color:var(--accent);}
.opt:disabled{cursor:default;}
.opt .letter{
  flex:0 0 auto;
  width:24px;height:24px;
  border-radius:50%;
  border:1px solid var(--line);
  display:flex;align-items:center;justify-content:center;
  font-size:.78rem;font-weight:700;
}
.opt.correct{border-color:var(--correct);background:var(--correct-bg);}
.opt.correct .letter{background:var(--correct);color:var(--accent-ink);border-color:var(--correct);}
.opt.wrong{border-color:var(--wrong);background:var(--wrong-bg);}
.opt.wrong .letter{background:var(--wrong);color:#fff;border-color:var(--wrong);}

.feedback{
  margin-top:16px;
  padding:13px 14px;
  border-radius:10px;
  font-family:system-ui,sans-serif;
  font-size:.88rem;
  line-height:1.5;
  display:none;
}
.feedback.show{display:block;}
.feedback.ok{background:var(--correct-bg);color:var(--correct);}
.feedback.no{background:var(--wrong-bg);color:var(--wrong);}
.feedback b{display:block;margin-bottom:4px;font-size:.82rem;text-transform:none;}
.feedback .expl{color:var(--ink);opacity:.88;}

.navrow{
  display:flex;
  justify-content:space-between;
  align-items:center;
  gap:10px;
  margin-top:20px;
  font-family:system-ui,sans-serif;
}
.navbtn{
  border:1px solid var(--line);
  background:var(--panel);
  color:var(--ink);
  padding:9px 16px;
  border-radius:9px;
  font-size:.88rem;
  cursor:pointer;
}
.navbtn:disabled{opacity:.4;cursor:default;}
.navbtn.primary{background:var(--accent);color:var(--accent-ink);border-color:var(--accent);font-weight:600;}

.jumpwrap{margin-top:22px;}
.jumpgrid{
  display:grid;
  grid-template-columns:repeat(10,1fr);
  gap:5px;
  margin-top:8px;
}
.jbtn{
  aspect-ratio:1;
  border-radius:6px;
  border:1px solid var(--line);
  background:var(--panel);
  color:var(--muted);
  font-family:system-ui,sans-serif;
  font-size:.68rem;
  cursor:pointer;
  display:flex;align-items:center;justify-content:center;
}
.jbtn.current{border-color:var(--accent);border-width:2px;}
.jbtn.ok{background:var(--correct-bg);color:var(--correct);border-color:var(--correct);}
.jbtn.no{background:var(--wrong-bg);color:var(--wrong);border-color:var(--wrong);}

.summary{
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:14px;
  padding:22px 20px;
  margin-top:18px;
  font-family:system-ui,sans-serif;
}
.summary h2{margin:0 0 6px;font-family:"Source Serif 4",serif;font-size:1.3rem;}
.bigscore{font-size:2.4rem;font-weight:800;color:var(--accent);margin:6px 0;}
.summary p{color:var(--muted);font-size:.88rem;margin:0 0 14px;}
.review-item{border-top:1px solid var(--line);padding:12px 0;}
.review-item .rq{font-size:.85rem;font-weight:600;margin-bottom:4px;}
.review-item .ra{font-size:.82rem;color:var(--muted);}
.resetbtn{
  margin-top:16px;
  border:none;
  background:var(--accent);
  color:var(--accent-ink);
  padding:11px 18px;
  border-radius:9px;
  font-size:.9rem;
  font-weight:600;
  cursor:pointer;
  width:100%;
}
footer.hint{
  text-align:center;
  color:var(--muted);
  font-family:system-ui,sans-serif;
  font-size:.75rem;
  margin-top:26px;
}
</style>
</head>
<body>
<div class="wrap">
  <header class="top">
    <h1>Latihan Soal Bayangan UTS — Pengelolaan Website</h1>
    <p class="sub">SMK Kelas 11 TKJ · 140 soal pilihan ganda</p>
    <div class="progress-row">
      <div class="bar"><div id="barFill"></div></div>
      <span class="scorepill" id="scorePill">0 / 0 terjawab</span>
    </div>
  </header>

  <div id="quizArea"></div>
  <div id="summaryArea"></div>

  <div class="jumpwrap" id="jumpWrap">
    <div class="progress-row" style="justify-content:space-between;">
      <span>Lompat ke soal</span>
    </div>
    <div class="jumpgrid" id="jumpGrid"></div>
  </div>

  <footer class="hint">Jawabanmu tersimpan otomatis di perangkat ini.</footer>
</div>

<script>
const QUIZ = [
{n:1,q:"WordPress Hosting adalah layanan web hosting yang dikonfigurasi dan dioptimalkan khusus untuk menjalankan situs web berbasis CMS WordPress. Manakah dari berikut ini yang BUKAN merupakan keunggulan optimasi WordPress Hosting dibandingkan dengan Shared Hosting biasa?",o:{A:"Memiliki caching khusus di tingkat server seperti LiteSpeed Cache dan Redis",B:"Menyediakan fitur instalasi satu-klik dan pembaruan otomatis untuk core WordPress",C:"Menggunakan sistem pengindeksan khusus yang membuat loading time lebih cepat",D:"Mampu menjalankan berbagai jenis CMS lain seperti Magento dan Joomla dengan performa sama",E:"Dilengkapi dengan plugin optimasi prainstal dan integrasi CDN otomatis"},a:"D",e:"WordPress Hosting dioptimalkan KHUSUS untuk WordPress, bukan untuk menjalankan CMS lain seperti Magento/Joomla — itu justru batasannya, bukan keunggulannya."},
{n:2,q:"Berdasarkan perbandingan harga hosting di Indonesia, jika seorang entrepreneur pemula ingin membangun company profile dengan budget terbatas, jenis hosting manakah yang paling cocok?",o:{A:"WordPress Hosting dengan kisaran harga Rp25.000–Rp100.000 per bulan",B:"Shared Hosting dengan kisaran harga Rp15.000–Rp75.000 per bulan",C:"Cloud Hosting dengan kisaran harga Rp80.000–Rp400.000+ per bulan",D:"Dedicated Server dengan kisaran harga Rp1–3 juta per bulan",E:"VPS Enterprise dengan kisaran harga Rp2.000.000–Rp5.000.000+ per bulan"},a:"B",e:"Untuk budget paling terbatas, Shared Hosting adalah opsi termurah (Rp15.000–Rp75.000/bulan), cukup untuk company profile sederhana."},
{n:3,q:"Dalam model bisnis Reseller Hosting, seorang reseller membeli paket seharga Rp500.000/bulan kemudian membaginya menjadi 10 akun hosting dan menjualnya dengan harga Rp100.000 per akun. Jika semua akun terjual, berapakah keuntungan kotor yang diperoleh reseller sebelum dikurangi biaya tambahan lainnya?",o:{A:"Rp500.000",B:"Rp600.000",C:"Rp800.000",D:"Rp1.000.000",E:"Rp1.500.000"},a:"A",e:"Pendapatan = 10 × Rp100.000 = Rp1.000.000. Biaya = Rp500.000. Keuntungan kotor = Rp1.000.000 − Rp500.000 = Rp500.000."},
{n:4,q:"Cloud Hosting menggunakan cluster server yang saling terhubung dalam sebuah jaringan. Manakah pernyataan berikut yang PALING TEPAT menjelaskan keunggulan Cloud Hosting dalam hal skalabilitas?",o:{A:"Dapat menambah atau mengurangi sumber daya sesuai kebutuhan tanpa downtime",B:"Hanya bisa menambah sumber daya saat website mengalami gangguan",C:"Memerlukan pembelian server fisik baru setiap kali terjadi peningkatan traffic",D:"Skalabilitas hanya bisa dilakukan pada jam-jam tertentu saja",E:"Tidak memerlukan monitoring karena skalabilitas berjalan sepenuhnya otomatis tanpa kontrol"},a:"A",e:"Skalabilitas elastis adalah ciri khas Cloud Hosting: resource dapat ditambah/dikurangi kapan saja sesuai kebutuhan tanpa mematikan layanan (downtime)."},
{n:5,q:"Dedicated Server Hosting menawarkan server fisik penuh untuk satu pelanggan. Pernyataan manakah yang BENAR mengenai kekurangan Dedicated Server?",o:{A:"Biaya sangat murah sehingga cocok untuk website kecil",B:"Jika server bermasalah, layanan bisa berhenti total dan keamanan harus dikelola sendiri",C:"Sumber daya harus dibagi dengan pengguna lain di server yang sama",D:"Tidak perlu pembaruan sistem karena penyedia hosting menangani semuanya",E:"Tidak ada risiko gangguan karena server bekerja secara terisolasi dari pengguna lain"},a:"B",e:"Karena hanya ada satu server fisik tanpa redundansi otomatis, jika server itu bermasalah layanan berhenti total; keamanan & maintenance juga jadi tanggung jawab penuh pelanggan."},
{n:6,q:"VPS (Virtual Private Server) membagi satu server fisik menjadi beberapa server virtual yang terisolasi. Teknologi apakah yang digunakan untuk melakukan pembagian server fisik tersebut?",o:{A:"Load Balancer",B:"Hypervisor",C:"Proxy Server",D:"Router Virtual",E:"DNS Server"},a:"B",e:"Hypervisor adalah perangkat lunak virtualisasi yang membagi satu server fisik menjadi beberapa server virtual (VPS) yang terisolasi satu sama lain."},
{n:7,q:"Seorang web developer yang ingin memulai bisnis menjual hosting kepada beberapa klien kecilnya akan memilih jenis hosting yang manakah dan mengapa?",o:{A:"Shared Hosting, karena biaya termurah dan mudah dikelola meski hanya untuk satu website",B:"Reseller Hosting, karena dapat membeli satu paket lalu menjualnya kembali kepada beberapa klien dengan margin keuntungan",C:"WordPress Hosting, karena dioptimalkan untuk semua jenis CMS dan bisnis hosting",D:"Dedicated Server, karena memberikan kontrol penuh meski biayanya lebih tinggi",E:"Cloud Hosting, karena dapat skalabilitas unlimited untuk semua klien sekaligus"},a:"B",e:"Model bisnis Reseller Hosting memang dirancang untuk membeli satu paket besar lalu menjualnya kembali ke banyak klien kecil dengan margin keuntungan."},
{n:8,q:"Dalam dokumen WordPress Hosting, disebutkan bahwa shared hosting biasa dirancang umum untuk berbagai platform. Apa keunggulan utama WordPress Hosting dibandingkan shared hosting biasa dalam hal caching?",o:{A:"Menggunakan caching hanya di tingkat aplikasi melalui plugin WordPress",B:"Menggunakan server-level caching seperti LiteSpeed Cache, Varnish, atau Redis yang memproses permintaan tanpa membebani sistem aplikasi",C:"Tidak menggunakan sistem caching sama sekali karena WordPress sudah dioptimalkan",D:"Caching dilakukan melalui browser pengguna saja tanpa melibatkan server",E:"Menggunakan CDN tanpa memerlukan sistem caching server"},a:"B",e:"Keunggulannya adalah caching di level SERVER (LiteSpeed/Varnish/Redis), bukan hanya lewat plugin aplikasi, sehingga permintaan diproses lebih cepat tanpa membebani WordPress."},
{n:9,q:"Berdasarkan kelebihan dan kekurangan masing-masing, apa yang menjadi kekurangan utama jika developer memilih Shared Hosting untuk website WordPress traffic sedang?",o:{A:"Tidak mendapat dukungan teknis khusus WordPress dari provider",B:"Aktivitas website lain di server yang sama dapat memengaruhi kinerja website klien jika memakai resource berlebih",C:"Biaya terlalu mahal sehingga tidak cocok untuk website kecil",D:"Memerlukan pembaruan manual untuk versi WordPress dan plugin",E:"Tidak dapat menjalankan website berbasis WordPress"},a:"B",e:"Karena resource server dibagi bersama, aktivitas berlebih dari website lain di server yang sama bisa memengaruhi kinerja website kita — ini risiko khas Shared Hosting."},
{n:10,q:"Fitur apa yang biasanya disediakan oleh WordPress Hosting dan TIDAK disediakan oleh shared hosting biasa?",o:{A:"Panel kontrol cPanel untuk mengelola email dan file",B:"Instalasi dan pembaruan otomatis (auto-update) untuk core WordPress, tema, dan plugin serta staging environment untuk menguji perubahan",C:"Unlimited bandwidth untuk semua website di server",D:"Akses SSH dan FTP untuk upload file website",E:"Database MySQL dengan ukuran tak terbatas"},a:"B",e:"Auto-update khusus WordPress dan staging environment adalah fitur khas WordPress Hosting yang umumnya tidak ada di Shared Hosting biasa."},
{n:11,q:"Seorang freelancer membeli paket Reseller Hosting seharga Rp400.000/bulan dan menjual kepada 8 klien dengan harga Rp80.000/klien per bulan. Jika semua klien terjual, berapa keuntungan kotor yang diperoleh setelah dikurangi biaya reseller?",o:{A:"Rp240.000",B:"Rp280.000",C:"Rp320.000",D:"Rp360.000",E:"Rp400.000"},a:"A",e:"Pendapatan = 8 × Rp80.000 = Rp640.000. Biaya = Rp400.000. Keuntungan = Rp640.000 − Rp400.000 = Rp240.000."},
{n:12,q:"Apa keuntungan utama dari skalabilitas dalam Cloud Hosting untuk sebuah website yang traffic-nya tidak stabil?",o:{A:"Mengurangi kebutuhan akan sumber daya secara permanen dan menjadi lebih murah",B:"Memungkinkan website untuk otomatis menambah atau mengurangi sumber daya sesuai kebutuhan traffic real-time, sehingga menghemat biaya saat traffic rendah dan stabil saat traffic tinggi",C:"Menghilangkan kebutuhan akan CDN dan caching di website",D:"Memastikan website tidak akan pernah mengalami gangguan sama sekali tanpa biaya tambahan",E:"Memungkinkan website berjalan tanpa koneksi internet"},a:"B",e:"Skalabilitas otomatis mengikuti traffic real-time: hemat biaya saat sepi, tetap stabil saat ramai — inilah nilai utama Cloud Hosting untuk traffic tidak stabil."},
{n:13,q:"Menurut dokumen WordPress Hosting, fitur caching khusus di tingkat server (seperti LiteSpeed Cache, Varnish, atau Redis) memberikan keuntungan utama berupa:",o:{A:"Mengurangi biaya sewa hosting secara signifikan",B:"Mempercepat waktu respons (TTFB) tanpa membebani sistem dari sisi aplikasi/plugin",C:"Memungkinkan instalasi plugin unlimited tanpa batasan",D:"Meningkatkan jumlah domain yang dapat dikelola dalam satu akun",E:"Memberikan sertifikat SSL gratis seumur hidup"},a:"B",e:"Caching server-level mempercepat Time to First Byte (TTFB) karena permintaan diproses di level server, tidak membebani aplikasi/plugin WordPress."},
{n:14,q:"Jika satu akun di server shared hosting terkena malware atau serangan hacker, risiko terbesarnya adalah:",o:{A:"Akun lain di server serupa bisa terkena imbas karena berbagi infrastruktur server",B:"Provider hosting akan memblokir semua website di server tersebut selamanya",C:"Biaya sewa akan meningkat dua kali lipat secara otomatis",D:"Data pelanggan akan dijual ke pihak ketiga tanpa persetujuan",E:"Website akan dipindahkan ke server cloud dan dikenakan biaya tambahan"},a:"A",e:"Karena infrastruktur server dibagi bersama, gangguan keamanan pada satu akun berisiko menular ke akun lain di server yang sama — ini kelemahan khas Shared Hosting."},
{n:15,q:"Dari pilihan berikut, siapa yang PALING TIDAK TEPAT untuk menggunakan layanan Reseller Hosting?",o:{A:"Web developer yang membuat website untuk beberapa klien",B:"Web design agency yang ingin menyediakan hosting sekaligus jasa pembuatan website",C:"Seorang blogger pribadi yang hanya memiliki satu website dengan traffic rendah",D:"Freelancer yang memiliki beberapa klien membutuhkan hosting",E:"Pengusaha pemula yang ingin memulai bisnis hosting sendiri"},a:"C",e:"Reseller Hosting dirancang untuk mengelola BANYAK akun/klien. Blogger dengan satu website traffic rendah lebih cocok pakai Shared Hosting biasa, bukan Reseller."},
{n:16,q:"Ketika terjadi lonjakan traffic pengunjung website secara tiba-tiba, keunggulan utama Cloud Hosting dibanding dedicated server adalah:",o:{A:"Biaya bulanan akan tetap sama meskipun traffic meningkat drastis",B:"Sistem dapat secara otomatis menambahkan atau mengalokasikan sumber daya sesuai kebutuhan real-time",C:"Kecepatan internet pengguna akan meningkat hingga 10 kali lipat",D:"Website tidak memerlukan update keamanan atau patch sistem apapun",E:"Administrator tidak perlu memonitor server sama sekali"},a:"B",e:"Cloud Hosting menambah resource otomatis saat traffic melonjak, sedangkan Dedicated Server kapasitasnya tetap dan berisiko downtime bila kewalahan."},
{n:17,q:"Seorang programmer ingin membuat server game online multiplayer dengan latency sangat rendah dan kapasitas prosesor kuat yang stabil 24/7. Pilihan PALING OPTIMAL adalah:",o:{A:"Shared Hosting karena harganya paling murah",B:"WordPress Hosting khusus karena sudah dilengkapi plugin optimasi bawaan",C:"Reseller Hosting karena memungkinkan membuat banyak akun sekaligus",D:"Dedicated Server Hosting karena memberikan sumber daya server penuh tanpa berbagi dengan pengguna lain",E:"Cloud Hosting karena dapat dengan mudah skalabilitas resource saat traffic puncak"},a:"D",e:"Untuk game server yang butuh performa stabil 24/7 dan latency serendah mungkin, Dedicated Server (resource penuh, tidak berbagi) adalah pilihan paling optimal."},
{n:18,q:"Isolasi antar VPS ini penting karena:",o:{A:"Agar setiap VPS dapat menggunakan sistem operasi berbeda-beda secara independen",B:"Agar aktivitas atau gangguan pada satu VPS tidak langsung memengaruhi VPS lainnya, namun tetap lebih hemat biaya dibanding dedicated server",C:"Agar provider hosting dapat membatasi kecepatan internet setiap VPS secara adil",D:"Agar VPS dapat terhubung langsung dengan internet tanpa melalui router apapun",E:"Agar setiap VPS memiliki sertifikat SSL yang berbeda dan unik"},a:"B",e:"Isolasi VPS mencegah gangguan pada satu VPS menular ke VPS lain, sekaligus tetap lebih hemat biaya dibanding menyewa Dedicated Server penuh."},
{n:19,q:"Teknologi caching tingkat server seperti LiteSpeed Cache, Varnish, atau Redis difungsikan untuk...",o:{A:"Mengurangi jumlah plugin yang dapat diinstal pada WordPress",B:"Memproses permintaan langsung tanpa membebani sistem dari aplikasi/plugin, sehingga waktu respons (TTFB) lebih cepat",C:"Membatasi jumlah pengguna yang dapat mengakses website secara bersamaan",D:"Mengenkripsi semua data pengguna agar lebih aman dari serangan malware",E:"Menghapus secara otomatis semua plugin pihak ketiga yang tidak diperbarui"},a:"B",e:"Fungsinya sama seperti soal no.13: mempercepat TTFB dengan memproses permintaan di level server tanpa membebani aplikasi/plugin."},
{n:20,q:"Kelebihan WordPress Hosting yang tidak dimiliki Shared Hosting Biasa adalah...",o:{A:"Harga yang lebih murah karena sumber daya dibagi dengan banyak pengguna",B:"Kemudahan instalasi dengan cPanel dan FTP access yang standar",C:"Pembaruan otomatis (auto-update) untuk core WordPress, tema, dan plugin, serta dukungan teknis khusus yang terlatih menangani masalah WordPress",D:"Kapasitas penyimpanan unlimited dan bandwidth tanpa batas",E:"Kemampuan menjalankan berbagai platform CMS sekaligus seperti Joomla, Magento, dan Laravel"},a:"C",e:"Auto-update khusus WordPress dan dukungan teknis terlatih WordPress adalah nilai tambah yang tidak dimiliki Shared Hosting biasa."}
,
{n:21,q:"Sebuah perusahaan keuangan (fintech) yang memproses data sensitif nasabah mempertimbangkan jenis hosting. Menurut dokumen, jenis hosting mana yang paling sesuai dan mengapa?",o:{A:"Shared Hosting, karena termurah dan sudah memiliki keamanan standar",B:"WordPress Hosting, karena memiliki fitur auto-update dan dukungan teknis khusus",C:"Dedicated Server Hosting, karena memberikan kontrol penuh terhadap keamanan, tidak berbagi server dengan pengguna lain, dan memenuhi standar keamanan ketat",D:"Cloud Hosting, karena skalabilitas unlimited dan dapat menyimpan data di berbagai lokasi",E:"Reseller Hosting, karena dapat membagi resource dengan banyak klien secara aman"},a:"C",e:"Fintech butuh kontrol keamanan penuh dan kepatuhan regulasi ketat — hanya server yang tidak dibagi (Dedicated Server) yang memenuhi kebutuhan ini."},
{n:22,q:"Pernyataan mana yang BENAR terkait karakteristik VPS (CPU virtual, RAM, penyimpanan, OS, IP sendiri, bekerja terisolasi)?",o:{A:"Gangguan atau crash pada satu VPS akan langsung mempengaruhi VPS lain di server fisik yang sama",B:"VPS lebih mahal daripada Dedicated Server karena setiap VPS memiliki sistem operasi terpisah",C:"Teknologi hypervisor memungkinkan isolasi antar VPS sehingga aktivitas satu VPS tidak langsung mempengaruhi VPS lainnya",D:"Setiap VPS harus menggunakan sistem operasi dan konfigurasi yang sama dengan VPS lain",E:"VPS tidak memiliki alamat IP sendiri karena masih berbagi server fisik dengan pengguna lain"},a:"C",e:"Hypervisor-lah yang menciptakan isolasi antar VPS, sehingga masing-masing VPS bekerja independen meski berbagi satu server fisik."},
{n:23,q:"Mengapa teknologi caching server-level (LiteSpeed Cache, Varnish, Redis) lebih efektif dibanding hanya plugin caching di sisi aplikasi?",o:{A:"Karena caching server-level memproses permintaan jauh lebih cepat tanpa harus membebani sistem aplikasi, sehingga Time to First Byte (TTFB) menjadi lebih singkat",B:"Plugin caching tidak dapat bekerja pada WordPress, jadi server-level caching adalah satu-satunya solusi yang viable",C:"Caching di tingkat server menggunakan algoritma AI yang dapat memprediksi permintaan pengguna dengan akurasi 100%",D:"Server-level caching dapat mengurangi biaya bandwidth hingga 90% karena tidak memerlukan koneksi internet",E:"Teknologi Varnish dan Redis hanya tersedia untuk WordPress dan tidak dapat digunakan pada platform CMS lainnya"},a:"A",e:"Caching di level server memproses permintaan sebelum sampai ke aplikasi, sehingga TTFB lebih cepat dan beban aplikasi berkurang — inilah efektivitasnya."},
{n:24,q:"Pertimbangan apa yang paling rasional untuk memilih Reseller Hosting dibanding Dedicated Server untuk melayani 15 klien traffic rendah-sedang?",o:{A:"Reseller Hosting memungkinkan agency mengelola multiple website klien dari satu paket dengan biaya modal lebih rendah, sambil tetap bisa branding sendiri dan menghasilkan margin keuntungan",B:"Dedicated Server menawarkan performa yang jauh lebih tinggi sehingga lebih cocok untuk website dengan traffic rendah hingga sedang",C:"Reseller Hosting memiliki keamanan lebih baik karena setiap klien mendapatkan server fisik terpisah",D:"Dedicated Server tidak dapat digunakan untuk melayani multiple klien sekaligus",E:"Reseller Hosting otomatis memberikan lisensi cPanel profesional kepada semua klien tanpa biaya tambahan"},a:"A",e:"Untuk 15 klien traffic rendah-sedang, Reseller Hosting lebih rasional: modal lebih rendah, tetap bisa branding sendiri, dan menghasilkan margin — dibanding investasi besar di Dedicated Server."},
{n:25,q:"Apa keuntungan utama penggunaan hypervisor dibanding tetap menggunakan satu server fisik untuk semua klien tanpa virtualisasi?",o:{A:"Hypervisor memungkinkan isolasi penuh antar VPS sehingga kegagalan atau masalah pada satu VPS tidak langsung mempengaruhi VPS lain, sekaligus mengoptimalkan resource utilization server fisik",B:"Hypervisor menghilangkan kebutuhan koneksi internet sehingga VPS dapat bekerja offline",C:"Menggunakan hypervisor membuat server fisik tidak perlu lagi memiliki CPU dan RAM sendiri",D:"Hypervisor secara otomatis mengenkripsi semua data di VPS dengan standar militer",E:"Tanpa hypervisor, server fisik hanya dapat melayani satu klien, tetapi dengan hypervisor dapat melayani unlimited klien"},a:"A",e:"Hypervisor memberi dua manfaat sekaligus: isolasi antar VPS (masalah satu VPS tak menular) dan optimalisasi pemanfaatan resource server fisik."},
{n:26,q:"Fitur cloud hosting manakah yang membuat Netflix dapat scale-up resource secara real-time tanpa downtime (menggunakan AWS)?",o:{A:"Skalabilitas elastis yang memungkinkan cloud hosting secara otomatis menambah atau mengurangi sumber daya (CPU, RAM, bandwidth) sesuai kebutuhan traffic saat itu, tanpa perlu restart server",B:"Netflix menggunakan teknologi p2p sehingga penonton lain dapat membantu melayani traffic dengan device mereka",C:"Cloud Hosting AWS memiliki backup server unlimited yang dapat instantly diaktifkan tanpa perlu alokasi ulang",D:"AWS secara fisik memiliki infinite server di seluruh dunia sehingga tidak pernah kehabisan kapasitas",E:"Netflix memitigasi lonjakan traffic dengan membatasi jumlah penonton secara otomatis ketika kapasitas sudah 80% terpakai"},a:"A",e:"Skalabilitas elastis (auto-scaling) AWS-lah yang memungkinkan Netflix menambah/mengurangi resource real-time tanpa restart atau downtime."},
{n:27,q:"Mengapa Dedicated Server lebih sesuai untuk industri finansial dibanding Cloud Hosting atau VPS?",o:{A:"Dedicated Server memberikan kontrol penuh atas konfigurasi hardware dan software sehingga memudahkan compliance dengan regulasi seperti data sovereignty, enkripsi end-to-end, dan audit trail—sesuatu yang sulit dilakukan di shared infrastructure",B:"Cloud Hosting tidak memiliki fitur keamanan apapun, hanya Dedicated Server yang dilengkapi firewall",C:"VPS tidak dapat menjalankan aplikasi banking karena sistem operasi virtualnya tidak stabil",D:"Dedicated Server adalah satu-satunya jenis hosting yang tersedia di Indonesia sesuai regulasi Bank Indonesia",E:"Fintech lebih memilih Dedicated Server karena harganya lebih murah dibanding Cloud Hosting dan VPS"},a:"A",e:"Kontrol penuh atas hardware/software memudahkan pemenuhan regulasi ketat (data sovereignty, audit trail) yang sulit dicapai di infrastruktur berbagi."},
{n:28,q:"Mengapa WordPress Hosting TIDAK direkomendasikan untuk perusahaan yang ingin menjalankan aplikasi custom non-WordPress atau multi-platform?",o:{A:"WordPress Hosting dikonfigurasi dan dioptimalkan khusus untuk arsitektur WordPress saja, sehingga kurang fleksibel atau bahkan melarang plugin tertentu—tidak cocok untuk custom framework atau CMS lain seperti Magento, Laravel, atau Drupal",B:"WordPress Hosting memiliki biaya lisensi yang sangat mahal untuk non-WordPress",C:"WordPress Hosting tidak memiliki koneksi internet sehingga tidak dapat mengintegrasikan API eksternal",D:"Server WordPress Hosting hanya kompatibel dengan PHP-WordPress dan tidak bisa menjalankan Python, Node.js",E:"Semua provider WordPress Hosting secara tegas melarang instalasi aplikasi non-WordPress berdasarkan perjanjian lisensi internasional"},a:"A",e:"Optimasi khusus WordPress membuat server ini kurang fleksibel untuk arsitektur/CMS lain — bukan soal lisensi atau bahasa pemrograman, tapi soal konfigurasi server."},
{n:29,q:"Berdasarkan analogi 'tinggal di rumah kos' pada Shared Hosting, elemen manakah yang menggambarkan risiko keamanan terbesar?",o:{A:"Kamar pribadi dipakai bersama dengan penghuni lain",B:"Jika satu penghuni terkena penyakit, penghuni lain bisa tertular karena berbagi fasilitas",C:"Biaya listrik, air, dan gas dibagi rata dengan semua penghuni kos",D:"Pengguna tidak bisa mengubah atau memodifikasi fasilitas umum seperti dapur",E:"Pengelolaan rumah kos sepenuhnya ditangani oleh pemilik tanpa melibatkan penghuni"},a:"B",e:"Analogi 'tertular karena berbagi fasilitas' menggambarkan risiko keamanan Shared Hosting: masalah di satu akun bisa menular ke akun lain di server yang sama."},
{n:30,q:"Reseller membeli paket dengan 15 akun cPanel, menjual Rp75.000/akun, berhasil menjual 12 akun, biaya paket Rp800.000/bulan. Berapa keuntungan kotor per bulan?",o:{A:"Rp100.000",B:"Rp300.000",C:"Rp500.000",D:"Rp900.000",E:"Rp1.200.000"},a:"A",e:"Pendapatan = 12 × Rp75.000 = Rp900.000. Biaya = Rp800.000. Keuntungan = Rp900.000 − Rp800.000 = Rp100.000."},
{n:31,q:"Untuk keperluan apakah Spotify memanfaatkan Google Cloud Platform?",o:{A:"Untuk menyimpan file video musik dengan enkripsi tingkat enterprise",B:"Untuk memproses miliaran data selera musik pengguna dan menyajikan rekomendasi lagu personal tanpa mengganggu pemutaran audio",C:"Untuk menjalankan server game online multiplayer dengan latency rendah",D:"Untuk mengelola transaksi pembayaran langganan dari jutaan pengguna secara real-time",E:"Untuk menghosting website portal berita dengan trafik pengunjung yang sangat tinggi"},a:"B",e:"Spotify memakai skala komputasi cloud untuk memproses data preferensi pengguna dalam jumlah besar dan menghasilkan rekomendasi personal secara real-time."},
{n:32,q:"Bisnis fintech baru memproses data sensitif nasabah (transaksi, kartu kredit, rekening bank). Jenis hosting manakah yang paling sesuai?",o:{A:"Shared Hosting karena biayanya paling murah dan cocok untuk startup",B:"WordPress Hosting karena dilengkapi fitur keamanan dan backup otomatis",C:"Reseller Hosting karena memungkinkan fintech untuk menjual layanan hosting ke klien lain",D:"Dedicated Server Hosting karena menyediakan server fisik penuh, keamanan terisolasi, dan standar keamanan ketat dapat dipenuhi sepenuhnya",E:"VPS karena harganya lebih terjangkau dari dedicated server namun masih memiliki performa bagus"},a:"D",e:"Sama seperti soal 21 & 27: data finansial sensitif memerlukan isolasi dan kontrol keamanan penuh yang hanya diberikan Dedicated Server."},
{n:33,q:"Berdasarkan analogi 'rumah pribadi vs kos-kosan', pernyataan mana yang TEPAT menggambarkan perbedaan Dedicated Server dan Shared Hosting?",o:{A:"Di rumah pribadi, pemilik bebas mengatur dan mengubah semuanya tanpa berbagi dengan orang lain; demikian pula Dedicated Server memberikan akses penuh sumber daya tanpa berbagi dengan pengguna lain",B:"Di rumah pribadi, pemilik harus membayar biaya bulanan untuk setiap fasilitas; demikian pula Dedicated Server memiliki biaya yang jauh lebih murah",C:"Di rumah pribadi, pemilik tidak perlu khawatir tentang keamanan; demikian pula Dedicated Server tidak memerlukan update sistem keamanan",D:"Di kos-kosan, penghuni berbagi fasilitas namun biayanya lebih mahal; demikian pula Shared Hosting memberikan performa lebih tinggi dengan harga lebih tinggi",E:"Di rumah pribadi, pemilik dapat mengundang tamu tanpa batas; demikian pula Dedicated Server dapat menjalankan aplikasi tanpa batasan jumlah pengguna"},a:"A",e:"Analogi yang tepat: rumah pribadi = kontrol dan akses penuh tanpa berbagi, persis seperti Dedicated Server yang tidak berbagi resource dengan pengguna lain."},
{n:34,q:"Apa dampak langsung dari isolasi antar VPS terhadap stabilitas dan keamanan sistem?",o:{A:"Aktivitas atau gangguan pada satu VPS tidak langsung memengaruhi VPS lainnya karena masing-masing bekerja secara terpisah",B:"Isolasi membuat biaya VPS menjadi lebih murah karena tidak perlu investasi server fisik besar",C:"Isolasi memastikan semua VPS mendapatkan kecepatan internet yang sama tanpa perbedaan",D:"Isolasi memungkinkan pengguna VPS untuk mengakses dan memodifikasi sistem operasi pengguna lain",E:"Isolasi berarti VPS tidak perlu dilakukan backup data karena data sudah terlindungi otomatis"},a:"A",e:"Isolasi berarti setiap VPS berjalan terpisah, jadi gangguan pada satu VPS tidak langsung berdampak pada VPS lainnya — ini menjaga stabilitas dan keamanan."},
{n:35,q:"Studio Shodwe membeli paket Reseller Hosting Rp200.000/bulan, membaginya menjadi 5 akun dijual Rp60.000/akun. Jika semua akun terjual, berapa keuntungan kotor per bulan?",o:{A:"Rp100.000",B:"Rp300.000",C:"Rp100.000",D:"Rp200.000",E:"Rp500.000"},a:"A",e:"Pendapatan = 5 × Rp60.000 = Rp300.000. Biaya = Rp200.000. Keuntungan = Rp300.000 − Rp200.000 = Rp100.000."},
{n:36,q:"Berdasarkan dokumen Shared Hosting dan WordPress Hosting, perbedaan utama dalam hal optimasi server adalah...",o:{A:"Shared Hosting lebih mahal daripada WordPress Hosting",B:"Shared Hosting dirancang umum untuk berbagai platform, sedangkan WordPress Hosting dikustomisasi khusus dari sisi server-side untuk arsitektur WordPress",C:"WordPress Hosting hanya cocok untuk website e-commerce, sedangkan Shared Hosting untuk semua jenis website",D:"Shared Hosting memiliki caching otomatis, sedangkan WordPress Hosting tidak",E:"WordPress Hosting tidak memerlukan domain, sementara Shared Hosting memerlukan domain tersendiri"},a:"B",e:"Inti perbedaannya: Shared Hosting bersifat umum/generik untuk semua platform, sedangkan WordPress Hosting dikustomisasi khusus dari sisi server untuk WordPress."},
{n:37,q:"Berikut ini yang bukan merupakan konten yang dapat disimpan dalam hosting adalah...",o:{A:"Gambar dan video",B:"Tulisan dan teks",C:"Plugin dan script yang rumit",D:"Protokol HTTP dan DNS server",E:"File multimedia dan dokumen"},a:"D",e:"HTTP dan DNS adalah PROTOKOL/SISTEM, bukan konten/file yang disimpan di hosting. Hosting menyimpan file (gambar, teks, script, dokumen), bukan protokol."},
{n:38,q:"Jenis hosting dimana sebuah server dapat digunakan secara bersama-sama oleh banyak pengguna secara bersamaan disebut...",o:{A:"VPS Hosting",B:"Cloud Hosting",C:"Shared Hosting",D:"Dedicated Hosting",E:"WordPress Hosting"},a:"C",e:"Definisi dasar Shared Hosting: satu server fisik dipakai bersama oleh banyak pengguna secara bersamaan."},
{n:39,q:"Layanan hosting di mana sebuah server yang dipakai oleh 1 account saja dinamakan...",o:{A:"Shared Hosting",B:"VPS Hosting",C:"Cloud Hosting",D:"Dedicated Hosting",E:"WordPress Hosting"},a:"D",e:"Dedicated Hosting/Server berarti satu server fisik penuh disewa oleh satu pelanggan/account saja, tanpa berbagi dengan pihak lain."},
{n:40,q:"Fungsi utama dari nama domain adalah...",o:{A:"Menyimpan file dan data website",B:"Mempermudah pengunjung dalam mengakses dan mengingat alamat website",C:"Menerjemahkan protokol HTTP menjadi HTTPS",D:"Memberikan styling dan desain visual pada website",E:"Menjalankan script JavaScript pada browser"},a:"B",e:"Domain adalah nama/alamat website yang mudah diingat manusia, menggantikan alamat IP numerik yang sulit dihafal."}
,
{n:41,q:"Dari nama domain smkhkti2.sch.id, bagian mana yang merupakan Second Level Domain (SLD)?",o:{A:".id",B:".sch",C:"smkhkti2",D:"sch.id",E:"smkhkti2.sch"},a:"C",e:"SLD adalah bagian nama unik sebelum TLD/domain tingkat kedua — di sini 'smkhkti2', sementara 'sch.id' adalah TLD gabungan (ccTLD+kategori)."},
{n:42,q:"Subdomain dari Google.com untuk mengakses website email Gmail adalah...",o:{A:"gmail.google.com",B:"mail.google.com",C:"email.google.com",D:"google.gmail.com",E:"account.google.com"},a:"B",e:"Subdomain resmi Gmail adalah mail.google.com — subdomain diletakkan di depan domain utama."},
{n:43,q:"Jenis TLD yang digunakan untuk website pendidikan Indonesia adalah...",o:{A:".com",B:".org",C:".ac.id",D:".gov.id",E:".net"},a:"C",e:".ac.id adalah ccTLD khusus untuk institusi akademik/pendidikan di Indonesia (ac = academic)."},
{n:44,q:"Jika HTML diibaratkan sebagai rangka tubuh manusia, maka CSS diibaratkan sebagai...",o:{A:"Otot dan saraf yang memberikan interaksi",B:"Pakaian dan kulit yang menambahkan estetika",C:"Tulang yang membentuk struktur dasar",D:"Otak yang mengontrol logika pergerakan",E:"Jantung yang mengatur aliran darah"},a:"B",e:"Dalam analogi Web Trinity: HTML=rangka/struktur, CSS=pakaian & kulit (estetika/tampilan), JavaScript=otot & saraf (interaksi/perilaku)."},
{n:45,q:"Dalam analogi pemesanan makanan di restoran untuk siklus client-server, posisi pelayan restoran adalah...",o:{A:"Server yang memproses pesanan",B:"Browser yang membuat request dan menerima response",C:"User yang melakukan pemesanan",D:"Koki yang menyiapkan hidangan",E:"DNS Server yang menerjemahkan domain"},a:"B",e:"Pelayan berperan sebagai perantara: mengantar permintaan (request) pelanggan ke dapur dan membawa kembali hasilnya (response) — persis seperti peran browser."},
{n:46,q:"Sebuah komputer yang menjalankan program untuk melayani data melalui protokol HTTP adalah definisi dari web server dalam sisi...",o:{A:"Software yang menghubungkan komputer dengan internet",B:"Hardware dengan spesifikasi tinggi dan hard drive besar",C:"ISP yang mengelola router khusus",D:"DNS Server yang menerjemahkan domain",E:"Client yang membuat HTTP request"},a:"A",e:"Definisi 'komputer yang menjalankan PROGRAM untuk melayani data' menunjuk pada sisi software web server, bukan spesifikasi hardware-nya."},
{n:47,q:"Ketika user mengetik nama domain di address bar browser, langkah pertama yang dilakukan browser adalah...",o:{A:"Langsung mengirim request ke web server",B:"Memeriksa DNS cache apakah mengenali domain tersebut",C:"Mengkonversi domain menjadi format binary",D:"Menghubungi ISP untuk mendapatkan akses internet",E:"Meminta izin dari hosting provider"},a:"B",e:"Browser lebih dulu mengecek DNS cache lokal untuk melihat apakah alamat IP domain tersebut sudah diketahui, sebelum melakukan lookup DNS penuh."},
{n:48,q:"Dalam tahapan pembangunan website, urutan yang benar adalah...",o:{A:"Desain Visual (CSS) → Fungsionalitas (JS) → Strukturisasi (HTML)",B:"Strukturisasi (HTML) → Fungsionalitas (JS) → Desain Visual (CSS)",C:"Fungsionalitas (JS) → Strukturisasi (HTML) → Desain Visual (CSS)",D:"Strukturisasi (HTML) → Desain Visual (CSS) → Fungsionalitas (JS)",E:"Desain Visual (CSS) → Strukturisasi (HTML) → Fungsionalitas (JS)"},a:"D",e:"Urutan logis: bangun struktur dulu (HTML), lalu percantik tampilan (CSS), baru tambahkan interaktivitas (JavaScript)."},
{n:49,q:"Peran JavaScript dalam pembangunan website adalah untuk...",o:{A:"Menentukan elemen pondasi seperti judul dan paragraf",B:"Mengontrol aspek visual mulai dari tipografi hingga warna",C:"Menambahkan interaktivitas, logika dinamis, dan membuat aplikasi web responsif secara perilaku",D:"Menyimpan file dan data website di server",E:"Menerjemahkan nama domain menjadi IP address"},a:"C",e:"JavaScript adalah bahasa perilaku/logika: menambahkan interaktivitas dan membuat website dinamis, berbeda dari HTML (struktur) dan CSS (tampilan)."},
{n:50,q:"Berdasarkan analogi tubuh manusia, CSS memiliki fungsi yang sama dengan...",o:{A:"Rangka tulang yang membentuk struktur dasar tubuh",B:"Kulit, bulu, dan warna yang memberikan estetika pada tubuh",C:"Otot dan saraf yang memungkinkan tubuh bergerak dan merespons",D:"Organ dalam yang mengatur fungsi vital tubuh",E:"Otak yang mengontrol seluruh sistem tubuh"},a:"B",e:"Sama seperti soal 44: CSS = kulit/estetika, HTML = rangka, JavaScript = otot & saraf (interaksi)."},
{n:51,q:"Apa perbedaan utama antara WordPress Hosting dan Shared Hosting biasa dalam hal optimasi server?",o:{A:"WordPress Hosting dirancang umum untuk berbagai platform, sedangkan Shared Hosting hanya untuk WordPress",B:"WordPress Hosting dikustomisasi khusus untuk arsitektur WordPress, sedangkan Shared Hosting dirancang umum untuk berbagai platform",C:"WordPress Hosting lebih murah dibandingkan Shared Hosting biasa",D:"WordPress Hosting tidak memerlukan pembaruan otomatis, sedangkan Shared Hosting memerlukan pembaruan manual",E:"WordPress Hosting menggunakan sumber daya server yang dibagi bersama dengan pengguna lain"},a:"B",e:"Pengulangan konsep no.36: WordPress Hosting dikustomisasi khusus WordPress, Shared Hosting bersifat umum untuk semua platform."},
{n:52,q:"Teknologi caching apa yang digunakan pada level server untuk meningkatkan Time to First Byte (TTFB) pada WordPress Hosting?",o:{A:"Database caching dan file caching",B:"LiteSpeed Cache, Varnish, atau Redis",C:"Browser caching dan HTTP caching",D:"CDN caching dan DNS caching",E:"Memory caching dan disk caching"},a:"B",e:"LiteSpeed Cache, Varnish, dan Redis adalah teknologi caching server-level yang disebutkan berulang kali dalam dokumen WordPress Hosting."},
{n:53,q:"Manakah dari pernyataan berikut yang merupakan kekurangan WordPress Hosting dibandingkan Shared Hosting?",o:{A:"WordPress Hosting memiliki kecepatan loading yang lebih lambat",B:"WordPress Hosting tidak menyediakan fitur instalasi satu-klik",C:"WordPress Hosting hanya cocok untuk WordPress dan tidak dirancang untuk menjalankan script atau CMS lain",D:"WordPress Hosting tidak memiliki sistem pengindeksan otomatis",E:"WordPress Hosting tidak menyediakan proteksi terhadap serangan brute-force"},a:"C",e:"Kekurangan utamanya adalah kurang fleksibel: server dioptimalkan khusus WordPress sehingga tidak cocok untuk CMS/script lain."},
{n:54,q:"Jenis website manakah yang paling cocok menggunakan WordPress Hosting?",o:{A:"Website dengan traffic ekstrem jutaan pengunjung per hari",B:"Aplikasi game online multiplayer dengan latency sangat rendah",C:"Blog & Media Personal, Website Portofolio, dan Bisnis Kecil & UMKM",D:"Platform streaming video dengan data pelanggan terenkripsi",E:"Aplikasi keuangan perbankan dengan pemrosesan data real-time"},a:"C",e:"Dokumen menyebutkan WordPress Hosting paling optimal untuk blog, portofolio, dan UMKM skala kecil-menengah."},
{n:55,q:"Berapa kisaran harga WordPress Hosting per bulan dibandingkan dengan Shared Hosting biasa menurut tabel perbandingan harga?",o:{A:"WordPress Hosting Rp15.000–Rp75.000, Shared Hosting Rp25.000–Rp100.000",B:"WordPress Hosting Rp25.000–Rp100.000, Shared Hosting Rp15.000–Rp75.000",C:"WordPress Hosting Rp80.000–Rp400.000+, Shared Hosting Rp25.000–Rp100.000",D:"WordPress Hosting Rp15.000–Rp50.000, Shared Hosting Rp80.000–Rp400.000+",E:"Kedua jenis hosting memiliki harga yang sama yaitu Rp50.000–Rp150.000"},a:"B",e:"Sesuai tabel dokumen: WordPress Hosting Rp25.000–Rp100.000, sedikit lebih mahal dari Shared Hosting Rp15.000–Rp75.000."},
{n:56,q:"Apa fitur utama yang biasanya disediakan pada WordPress Hosting untuk memudahkan pengelolaan website?",o:{A:"Instalasi server fisik manual dan konfigurasi IP address",B:"Instalasi satu-klik, pembaruan otomatis, dan staging environment",C:"Pembagian sumber daya server dengan pengguna lain dan shared database",D:"Akses root sepenuhnya dan kontrol database tanpa batasan",E:"Layanan konsultasi gratis seumur hidup dan upgrade hardware unlimited"},a:"B",e:"Fitur andalan WordPress Hosting adalah kemudahan pengelolaan: instalasi satu-klik, auto-update, dan staging environment."},
{n:57,q:"Manakah pernyataan berikut yang menunjukkan keunggulan WordPress Hosting dalam hal keamanan?",o:{A:"Menghilangkan kemungkinan malware sama sekali tanpa teknologi perlindungan",B:"Pemindaian malware otomatis, proteksi terhadap serangan brute-force, dan aturan firewall spesifik WordPress",C:"Tidak memerlukan update sistem dan tema karena sudah aman selamanya",D:"Mengenkripsi semua data pengguna menggunakan teknologi blockchain",E:"Memisahkan website sepenuhnya dari internet untuk menghindari serangan"},a:"B",e:"Keamanan WordPress Hosting mencakup malware scanning otomatis, proteksi brute-force, dan firewall rules yang spesifik untuk WordPress."},
{n:58,q:"Seorang web developer memiliki 15 pelanggan performa sedang. Jika memakai WordPress Hosting untuk tiap pelanggan biayanya sangat tinggi. Solusi hosting paling efisien secara finansial adalah:",o:{A:"Cloud Hosting, karena dapat menskalakan resource sesuai kebutuhan setiap pelanggan",B:"Reseller Hosting, karena developer dapat membeli satu paket besar dan membaginya kepada 15 pelanggan dengan harga lebih terjangkau",C:"Dedicated Server, karena dapat menampung semua website pelanggan dengan performa maksimal",D:"VPS, karena setiap pelanggan akan mendapatkan server virtual yang terisolasi sepenuhnya",E:"Shared Hosting biasa, karena paling murah meskipun risiko keamanan lebih tinggi"},a:"B",e:"Reseller Hosting adalah solusi paling efisien secara biaya: satu paket besar dibagi ke banyak pelanggan dengan margin, seperti pola soal 3, 11, 30, 35."},
{n:59,q:"Berdasarkan tabel perbandingan harga (Shared, WordPress, VPS, Dedicated Server), manakah pernyataan yang PALING AKURAT?",o:{A:"Dedicated Server selalu lebih mahal karena menawarkan performa tertinggi, cocok untuk semua jenis website",B:"WordPress Hosting lebih mahal dari Shared Hosting biasa karena dioptimalkan khusus dan memiliki fitur keamanan serta update otomatis yang tidak ada di Shared Hosting",C:"VPS harganya sama dengan WordPress Hosting, jadi keduanya memiliki fungsi dan kelebihan yang identik",D:"Shared Hosting adalah pilihan terbaik karena harganya paling murah dan cocok untuk semua jenis website tanpa terkecuali",E:"Cloud Hosting tidak ada di tabel karena tidak populer di Indonesia dan tidak pernah digunakan"},a:"B",e:"Selisih harga WordPress vs Shared Hosting mencerminkan nilai tambah fitur (keamanan, auto-update) yang tidak dimiliki Shared Hosting biasa."},
{n:60,q:"Mengapa Cloud Hosting (seperti AWS) menjadi pilihan utama untuk aplikasi seperti Netflix dibandingkan Dedicated Server?",o:{A:"Cloud Hosting lebih murah dibanding Dedicated Server dengan performa yang sama tingginya",B:"Cloud Hosting memiliki skalabilitas otomatis dan sistem cluster yang dapat menambah resource saat traffic tinggi, sementara Dedicated Server memiliki kapasitas tetap dan risiko downtime jika server bermasalah",C:"Dedicated Server tidak mendukung video streaming berkualitas tinggi, hanya Cloud Hosting yang mampu",D:"Cloud Hosting tidak memerlukan keamanan yang ketat, sedangkan Dedicated Server sangat ketat dalam hal keamanan",E:"Cloud Hosting adalah satu-satunya hosting yang dapat menangani jutaan pengguna secara bersamaan tanpa bantuan server lain"},a:"B",e:"Skalabilitas otomatis dan sistem cluster Cloud Hosting mengatasi kelemahan Dedicated Server yang kapasitasnya tetap dan rawan downtime."}
,
{n:61,q:"Pengusaha pemula modal terbatas (Rp100.000–500.000/bulan) merencanakan 10 pelanggan hosting dalam 6 bulan pertama. Strategi bisnis hosting manakah yang paling sesuai?",o:{A:"Membeli Dedicated Server seharga Rp3 juta/bulan agar dapat melayani banyak pelanggan sekaligus",B:"Menggunakan Cloud Hosting dengan bayar sesuai penggunaan untuk menekan biaya awal",C:"Membeli paket Reseller Hosting seharga Rp100.000–300.000/bulan, kemudian membagi resource menjadi paket yang dijual ke pelanggan seharga Rp25.000–50.000/akun",D:"Langsung menjual WordPress Hosting dengan membeli multiple paket dari provider untuk setiap pelanggan",E:"Membeli VPS Enterprise seharga Rp2–5 juta/bulan untuk setup infrastruktur profesional sejak awal"},a:"C",e:"Dengan modal terbatas, Reseller Hosting paling sesuai: biaya awal rendah dan cocok dibagi ke banyak pelanggan kecil, sesuai dengan kisaran modal yang tersedia."},
{n:62,q:"VPS dan Dedicated Server sama-sama menawarkan kontrol penuh atas server, namun ada perbedaan fundamental. Manakah pernyataan yang paling tepat?",o:{A:"VPS menggunakan satu server fisik yang dibagi menjadi beberapa server virtual melalui hypervisor, sedangkan Dedicated Server adalah server fisik penuh yang digunakan oleh satu pelanggan saja",B:"Dedicated Server lebih murah dari VPS karena menggunakan teknologi virtualisasi yang lebih efisien",C:"VPS memberikan performa yang lebih tinggi dibanding Dedicated Server karena menggunakan multiple server fisik sekaligus",D:"Keduanya memiliki cara kerja yang identik, hanya perbedaan harga saja yang membedakannya",E:"Dedicated Server menggunakan hypervisor seperti VPS, tetapi dengan fitur keamanan yang jauh lebih baik"},a:"A",e:"Perbedaan fundamental: VPS = satu server fisik dipecah jadi banyak server virtual (hypervisor); Dedicated Server = satu server fisik utuh untuk satu pelanggan."},
{n:63,q:"Platform e-commerce dengan 50.000 pengunjung/bulan, puncak traffic saat flash sale, memilih antara WordPress Hosting, VPS, dan Dedicated Server. Manakah yang paling sesuai?",o:{A:"WordPress Hosting, karena fitur keamanan dan auto-update sudah cukup untuk melindungi transaksi pelanggan",B:"VPS, karena mampu menangani traffic sedang (10.000–100.000 pengunjung/bulan), memberikan performa stabil saat flash sale, dan biaya lebih terjangkau dibanding Dedicated Server",C:"Dedicated Server, karena e-commerce memerlukan kontrol penuh dan server tidak boleh berbagi resource",D:"Cloud Hosting, karena skalabilitas otomatis menangani lonjakan traffic flash sale dengan sempurna",E:"Shared Hosting, karena biaya paling murah dan 50.000 pengunjung/bulan masih dalam kategori kecil"},a:"B",e:"Dengan traffic 50.000/bulan (kategori sedang) dan kebutuhan performa stabil saat flash sale, VPS adalah pilihan paling seimbang dari sisi performa dan biaya."},
{n:64,q:"Manakah pernyataan tentang perbedaan Shared Hosting dan WordPress Hosting yang SALAH?",o:{A:"WordPress Hosting memiliki sistem caching khusus di level server (seperti LiteSpeed Cache atau Varnish) yang lebih efisien dibanding Shared Hosting biasa",B:"WordPress Hosting menyediakan auto-update untuk core WordPress, tema, dan plugin, sementara Shared Hosting tidak selalu menyediakan fitur ini",C:"Shared Hosting dirancang umum untuk berbagai platform (PHP, HTML, Joomla, dll.), sedangkan WordPress Hosting dikustomisasi khusus untuk WordPress",D:"WordPress Hosting harganya selalu sama dengan Shared Hosting biasa karena keduanya termasuk kategori shared resource",E:"WordPress Hosting menyediakan staging environment untuk menguji perubahan sebelum dipublikasikan, sementara Shared Hosting biasa umumnya tidak memiliki fitur ini"},a:"D",e:"Pernyataan D SALAH — menurut tabel harga, WordPress Hosting (Rp25.000–Rp100.000) umumnya lebih mahal dari Shared Hosting (Rp15.000–Rp75.000), bukan selalu sama."},
{n:65,q:"Freelancer membeli reseller hosting Rp300.000/bulan, dijual ke 6 pelanggan seharga Rp75.000/akun. Berapa keuntungan kotor per bulan?",o:{A:"Rp150.000",B:"Rp200.000",C:"Rp450.000",D:"Rp525.000",E:"Rp750.000"},a:"A",e:"Pendapatan = 6 × Rp75.000 = Rp450.000. Biaya = Rp300.000. Keuntungan = Rp450.000 − Rp300.000 = Rp150.000."},
{n:66,q:"Apa keunggulan utama Cloud Hosting dibandingkan Dedicated Server dalam menangani lonjakan traffic yang tidak terduga?",o:{A:"Biaya sewa yang lebih murah dan stabil setiap bulannya",B:"Kemampuan skalabilitas otomatis untuk menambah sumber daya sesuai kebutuhan tanpa downtime",C:"Keamanan server yang lebih tinggi karena tidak bergantung pada internet",D:"Kontrol penuh atas perangkat keras fisik server tanpa pembatasan",E:"Tidak memerlukan pengelolaan teknis dan pembaruan sistem dari pengguna"},a:"B",e:"Konsisten dengan soal 4, 12, 16, 60: keunggulan Cloud Hosting adalah skalabilitas otomatis tanpa downtime."},
{n:67,q:"Platform streaming musik global menggunakan Google Cloud Platform untuk memproses data preferensi pengguna & memberikan rekomendasi real-time. Teknologi apa yang paling mendukung ini?",o:{A:"Compute Engine untuk memproses data dengan kapasitas CPU tinggi",B:"Cloud Storage untuk menyimpan file audio dalam jumlah besar",C:"Big Data & AI/ML yang dapat menganalisis miliaran data pengguna dengan cepat",D:"Virtual Machines untuk menjalankan server aplikasi musik",E:"Database relasional untuk mencatat setiap transaksi pengguna"},a:"C",e:"Rekomendasi personal berbasis analisis data preferensi pengguna dalam skala miliaran adalah kasus khas Big Data & AI/ML, bukan sekadar compute/storage."},
{n:68,q:"Toko online kecil (500 pengunjung/hari) memilih antara Shared Hosting (Rp50.000), WordPress Hosting (Rp60.000), VPS Basic (Rp75.000). Hosting manakah yang paling cost-effective dan sesuai?",o:{A:"Shared Hosting karena harga termurah dan website kecil tidak memerlukan optimasi khusus",B:"WordPress Hosting karena dioptimalkan untuk toko online WooCommerce dengan fitur keamanan dan performa lebih baik",C:"VPS Basic karena memberikan kontrol penuh dan skalabilitas tanpa biaya tambahan di masa depan",D:"Cloud Hosting karena dapat menyesuaikan resource secara otomatis saat ada promosi flash sale",E:"Dedicated Server karena menjamin stabilitas transaksi dan keamanan data pelanggan maksimal"},a:"B",e:"Untuk toko online kecil berbasis WooCommerce (biasanya WordPress), WordPress Hosting adalah pilihan paling seimbang antara harga dan optimasi fitur toko online."},
{n:69,q:"Manakah pernyataan berikut yang paling akurat mengenai perbedaan cara kerja antara Shared Hosting dan VPS?",o:{A:"Shared hosting membagi satu server untuk banyak pengguna dengan resource bersama, sementara VPS membagi satu server menjadi beberapa server virtual terisolasi dengan resource tersendiri",B:"Shared hosting menggunakan hypervisor untuk virtualisasi, sedangkan VPS menggunakan teknologi cloud computing terdepan",C:"Shared hosting lebih aman karena dikelola sepenuhnya oleh penyedia, sementara VPS memerlukan keahlian teknis tinggi untuk operasional dasar",D:"Shared hosting dapat menskalakan resource secara otomatis seperti cloud hosting, sedangkan VPS memiliki resource tetap",E:"VPS dan shared hosting memiliki cara kerja identik, hanya berbeda pada jumlah pelanggan yang dilayani"},a:"A",e:"Perbedaan intinya: Shared Hosting = resource dibagi bersama tanpa batas jelas; VPS = resource terpisah/tersendiri meski berbagi server fisik yang sama."},
{n:70,q:"Web developer agency ingin menjual hosting beserta jasa pembuatan website. Jenis hosting apa yang paling sesuai dengan model bisnis reseller hosting?",o:{A:"Shared hosting, karena paling murah dan mudah dijual ke pemula",B:"Reseller hosting, karena memungkinkan developer membeli resource dari provider lalu menjualnya kembali dengan merek sendiri",C:"Cloud hosting, karena memiliki skalabilitas tinggi untuk pertumbuhan bisnis jangka panjang",D:"Dedicated server, karena memberikan kontrol penuh dan performa terbaik untuk klien premium",E:"WordPress hosting, karena sudah dioptimalkan dan tinggal dijual tanpa perlu konfigurasi tambahan"},a:"B",e:"Reseller Hosting memang dirancang untuk model bisnis menjual kembali hosting dengan branding sendiri — sesuai kebutuhan agency."},
{n:71,q:"Portal berita nasional 2 juta pengunjung/bulan dengan traffic sangat volatile, terutama saat berita trending. Hosting manakah yang paling sesuai?",o:{A:"Shared hosting dengan upgrade bandwidth untuk mengantisipasi lonjakan traffic",B:"VPS menengah dengan resource besar dan upgrade kapan-kapan saat diperlukan",C:"Cloud hosting karena memiliki skalabilitas otomatis dan dapat menangani lonjakan traffic ekstrem tanpa perlu intervensi manual",D:"Dedicated server high-end karena memiliki performa stabil dan resource besar",E:"WordPress hosting karena menyediakan fitur caching khusus untuk website berita dengan traffic tinggi"},a:"C",e:"Traffic yang sangat volatile (naik-turun ekstrem) paling cocok ditangani Cloud Hosting karena resource menyesuaikan otomatis tanpa intervensi manual."},
{n:72,q:"Manakah dari berikut ini yang bukan merupakan penyedia WordPress Hosting lokal (Indonesia) menurut dokumen referensi?",o:{A:"Niagahoster",B:"DomaiNesia",C:"Dewaweb",D:"SiteGround",E:"IDCloudHost"},a:"D",e:"SiteGround adalah provider hosting internasional (berbasis luar negeri), bukan provider lokal Indonesia seperti Niagahoster, DomaiNesia, Dewaweb, dan IDCloudHost."},
{n:73,q:"UMKM kecil ingin membangun website company profile tanpa perlu mengelola masalah teknis server secara mendalam. Jenis hosting manakah yang paling sesuai?",o:{A:"Cloud Hosting dengan kontrol penuh infrastruktur",B:"Dedicated Server Hosting untuk kontrol maksimal",C:"WordPress Hosting yang dioptimalkan untuk stabilitas dan kemudahan manajemen",D:"VPS untuk fleksibilitas teknis tinggi",E:"Reseller Hosting untuk menjual kembali kepada pelanggan lain"},a:"C",e:"WordPress Hosting cocok untuk UMKM karena dikelola dan dioptimalkan penyedia, sehingga pemilik website tidak perlu mengurus hal teknis mendalam."},
{n:74,q:"Berdasarkan analogi dalam dokumen referensi, pernyataan manakah yang paling tepat menggambarkan perbedaan Shared Hosting dan Dedicated Server Hosting?",o:{A:"Keduanya sama-sama memberikan akses penuh ke server fisik",B:"Shared Hosting seperti tinggal di kos dengan fasilitas bersama, sedangkan Dedicated Server seperti memiliki rumah pribadi dengan fasilitas sendiri",C:"Dedicated Server lebih murah karena biaya infrastruktur dibagi dengan banyak pengguna",D:"Shared Hosting lebih aman karena pengguna tidak perlu mengelola keamanan sendiri",E:"Keduanya memiliki tingkat kontrol yang sama terhadap konfigurasi server"},a:"B",e:"Analogi dokumen: Shared Hosting = kos (fasilitas bersama), Dedicated Server = rumah pribadi (fasilitas sendiri sepenuhnya)."},
{n:75,q:"Startup teknologi mengalami pertumbuhan pengguna eksponensial dan memerlukan hosting yang dapat otomatis menambah/mengurangi sumber daya sesuai lonjakan traffic. Teknologi manakah yang paling ideal?",o:{A:"Shared Hosting karena harganya paling murah",B:"Dedicated Server karena memberikan kontrol penuh",C:"Cloud Hosting dengan kemampuan skalabilitas otomatis melalui cluster server",D:"WordPress Hosting dengan plugin optimasi",E:"VPS Basic dengan upgrade manual saat traffic meningkat"},a:"C",e:"Pertumbuhan eksponensial memerlukan penyesuaian resource otomatis — ini adalah keunggulan utama Cloud Hosting."},
{n:76,q:"Reseller membeli paket Rp400.000/bulan, menjual ke 8 pelanggan Rp80.000/akun. Berapa estimasi keuntungan kotor per bulan?",o:{A:"Rp240.000",B:"Rp320.000",C:"Rp480.000",D:"Rp640.000",E:"Rp800.000"},a:"A",e:"Pendapatan = 8 × Rp80.000 = Rp640.000. Biaya = Rp400.000. Keuntungan = Rp640.000 − Rp400.000 = Rp240.000 (sama seperti soal 11)."},
{n:77,q:"Berdasarkan tabel harga (Shared Rp15rb-75rb, WordPress Rp25rb-100rb, Cloud/VPS Rp80rb-400rb+), manakah pernyataan yang PALING AKURAT?",o:{A:"Shared Hosting adalah pilihan termurah dan tidak ada jenis hosting lain yang bisa lebih murah",B:"WordPress Hosting selalu lebih mahal daripada Shared Hosting biasa",C:"Ada rentang harga tumpang tindih antara WordPress Hosting dan Cloud/VPS Hosting",D:"Cloud Hosting/VPS tidak pernah semurah WordPress Hosting",E:"Harga Cloud Hosting selalu lebih dari Rp400.000 per bulan"},a:"C",e:"Rentang WordPress Hosting (Rp25rb–Rp100rb) dan Cloud/VPS (Rp80rb–Rp400rb+) beririsan di kisaran Rp80rb–Rp100rb, jadi memang ada tumpang tindih harga."},
{n:78,q:"Manakah dari fitur-fitur berikut yang merupakan keunggulan spesifik WordPress Hosting tetapi TIDAK selalu tersedia di Shared Hosting biasa?",o:{A:"Panel kontrol cPanel untuk mengelola file dan database",B:"Server-level caching khusus WordPress (seperti LiteSpeed Cache atau Varnish) dan plugin optimasi prainstal",C:"Kemampuan menyimpan data website di server",D:"Koneksi internet dengan kecepatan tinggi",E:"Backup data secara berkala untuk semua pengguna"},a:"B",e:"Caching server-level khusus WordPress dan plugin optimasi prainstal adalah fitur khas WordPress Hosting yang tidak selalu ada di Shared Hosting biasa."},
{n:79,q:"Administrator website WordPress Hosting mengalami plugin pihak ketiga yang ingin digunakan malah diblokir oleh penyedia hosting. Fenomena ini termasuk kekurangan WordPress Hosting yang mana?",o:{A:"Keterbatasan Fleksibilitas - WordPress Hosting hanya dirancang khusus untuk WordPress dan tidak cocok untuk CMS lain",B:"Restriksi Plugin - Beberapa penyedia menerapkan batasan atau melarang penggunaan plugin tertentu yang dianggap membebani server atau berbenturan dengan sistem caching bawaan",C:"Lebih Mahal - Biaya bulanan/tahunan umumnya lebih tinggi dibanding shared hosting standar",D:"Keamanan Ekstra - Fitur keamanan yang terlalu ketat membuat administrator kesulitan menginstal plugin tambahan",E:"Performa Terbatas - WordPress Hosting masih memiliki batasan dalam menangani plugin-plugin berat"},a:"B",e:"Kasus plugin diblokir secara spesifik termasuk kategori 'Restriksi Plugin' — pembatasan penyedia terhadap plugin yang membebani server atau bentrok dengan caching."},
{n:80,q:"Perusahaan IT mempertimbangkan Reseller Hosting Rp600.000/bulan vs Dedicated Server Rp2.000.000/bulan, melayani 20 pelanggan seharga Rp75.000/akun. Analisis mana yang paling tepat?",o:{A:"Reseller Hosting lebih menguntungkan karena omzet akan mencapai Rp1.500.000 dengan laba kotor Rp900.000, sementara Dedicated Server memerlukan biaya operasional yang jauh lebih besar untuk hasil yang serupa",B:"Dedicated Server lebih cocok karena memberikan kontrol penuh dan tidak bergantung pada provider, meskipun biayanya lebih tinggi",C:"Reseller Hosting kurang menguntungkan karena perusahaan harus memberikan customer support sendiri tanpa bantuan dari penyedia hosting",D:"Kedua pilihan memiliki keuntungan yang sama karena baik Reseller maupun Dedicated Server menawarkan skalabilitas yang identik",E:"Reseller Hosting lebih berisiko karena jika provider mengalami gangguan, semua 20 pelanggan perusahaan juga akan terdampak, sementara Dedicated Server bebas dari risiko tersebut"},a:"A",e:"Omzet 20×Rp75.000=Rp1.500.000, dikurangi biaya Rp600.000 = laba kotor Rp900.000 — jauh lebih hemat modal dibanding Dedicated Server Rp2.000.000/bulan."}
,
{n:81,q:"Apa yang dimaksud dengan website?",o:{A:"Kumpulan file yang disimpan di komputer lokal tanpa koneksi internet",B:"Kumpulan halaman yang saling terhubung dan dapat diakses melalui internet menggunakan browser",C:"Program aplikasi yang hanya berjalan di server tanpa dapat diakses pengguna",D:"Perangkat keras yang menghubungkan komputer ke jaringan lokal",E:"Bahasa pemrograman yang digunakan untuk membuat aplikasi desktop"},a:"B",e:"Website adalah kumpulan halaman yang saling terhubung dan dapat diakses melalui internet menggunakan browser."},
{n:82,q:"Protokol apa yang digunakan untuk mengirimkan data halaman web dari server ke browser klien?",o:{A:"FTP (File Transfer Protocol)",B:"SMTP (Simple Mail Transfer Protocol)",C:"HTTP/HTTPS (HyperText Transfer Protocol/Secure)",D:"DNS (Domain Name System)",E:"POP3 (Post Office Protocol)"},a:"C",e:"HTTP/HTTPS adalah protokol standar untuk mengirimkan data halaman web antara server dan browser."},
{n:83,q:"Apa peran utama dari Domain Name Server (DNS) dalam ekosistem internet?",o:{A:"Menyimpan semua file halaman web di server pusat",B:"Mengonversi nama domain (seperti www.google.com) menjadi alamat IP yang dapat dikenali komputer",C:"Mengenkripsi data sensitif pengguna saat browsing",D:"Mengelola bandwidth dan kecepatan koneksi internet",E:"Membuat backup otomatis dari semua website yang ada"},a:"B",e:"DNS berfungsi menerjemahkan nama domain yang mudah diingat manusia menjadi alamat IP yang dikenali komputer."},
{n:84,q:"Jika seorang developer ingin membuat website yang responsif dan dapat diakses di berbagai perangkat, teknologi mana yang paling relevan digunakan?",o:{A:"HTML dengan inline style tanpa framework apapun",B:"CSS Grid dan Flexbox untuk layout fleksibel, atau menggunakan framework seperti Bootstrap",C:"JavaScript vanila untuk mengubah ukuran elemen secara manual",D:"Database relasional untuk menyesuaikan tampilan konten",E:"Server-side rendering dengan PHP untuk setiap perangkat yang berbeda"},a:"B",e:"CSS Grid/Flexbox (atau framework seperti Bootstrap) adalah teknologi standar untuk membangun layout responsif lintas perangkat."},
{n:85,q:"Apa perbedaan utama antara website statis dan website dinamis?",o:{A:"Website statis lebih cepat, website dinamis lebih lambat tanpa alasan teknis",B:"Website statis menampilkan konten yang sama untuk semua pengguna, website dinamis menghasilkan konten berdasarkan permintaan dan data dari database",C:"Website statis memerlukan server, website dinamis tidak memerlukan server",D:"Website dinamis hanya dapat diakses oleh admin, website statis dapat diakses siapa saja",E:"Website statis menggunakan HTML, website dinamis tidak menggunakan HTML sama sekali"},a:"B",e:"Website statis = konten tetap/sama untuk semua orang; website dinamis = konten berubah sesuai permintaan/data dari database."},
{n:86,q:"Seorang pengguna menerima pesan bahwa sertifikat SSL pada website yang akan diakses tidak valid. Apa yang menjadi masalah utama?",o:{A:"Koneksi internet pengguna terlalu lambat untuk membuka website",B:"Website belum terdaftar di database search engine",C:"Sertifikat SSL/TLS website tidak valid atau expired, sehingga koneksi HTTPS tidak dapat dipercaya dan data pengguna berisiko",D:"Nama domain website tidak terdaftar secara resmi di registrar terpercaya",E:"Browser pengguna tidak mendukung protokol HTTP/2"},a:"C",e:"Pesan sertifikat tidak valid berarti sertifikat SSL/TLS bermasalah (expired/tidak valid), sehingga koneksi aman (HTTPS) tidak dapat dijamin."},
{n:87,q:"Dalam proses pengembangan website, apa fungsi utama dari version control system seperti Git?",o:{A:"Mengompresi ukuran file website agar loading lebih cepat",B:"Mencatat dan mengelola perubahan kode, memungkinkan kolaborasi tim, dan memudahkan rollback ke versi sebelumnya jika ada kesalahan",C:"Menghubungkan website dengan database secara otomatis",D:"Mengoptimalkan performa query database untuk kecepatan akses data",E:"Mengenkripsi semua file kode sumber agar tidak dapat diakses orang lain"},a:"B",e:"Git berfungsi mencatat riwayat perubahan kode, mendukung kolaborasi tim, dan memungkinkan rollback ke versi sebelumnya."},
{n:88,q:"Apa yang dimaksud dengan bandwidth dalam konteks pengelolaan website?",o:{A:"Kecepatan prosesor server dalam memproses data",B:"Jumlah data maksimal yang dapat ditransfer antara server dan client dalam periode waktu tertentu",C:"Kapasitas penyimpanan data di server web",D:"Kecepatan akses database website",E:"Batas jumlah pengguna yang dapat mengakses website secara bersamaan"},a:"B",e:"Bandwidth adalah jumlah data maksimal yang dapat ditransfer antara server dan client dalam periode waktu tertentu."},
{n:89,q:"Dalam pengelolaan website, apa fungsi utama dari file robots.txt?",o:{A:"Mengenkripsi semua data pengguna yang masuk ke server",B:"Mengatur pesan error ketika halaman tidak ditemukan",C:"Menginstruksikan search engine crawler mengenai halaman mana yang boleh atau tidak boleh diindeks",D:"Mengontrol akses pengguna berdasarkan lokasi geografis",E:"Membatasi ukuran file yang dapat diupload ke website"},a:"C",e:"robots.txt memberi instruksi kepada crawler mesin pencari tentang halaman mana yang boleh/tidak boleh diindeks."},
{n:90,q:"Manakah dari berikut ini yang bukan merupakan fungsi dari Content Delivery Network (CDN)?",o:{A:"Mendistribusikan konten ke server di berbagai lokasi geografis untuk mempercepat loading",B:"Melindungi website dari serangan DDoS",C:"Memperbaiki syntax error pada kode website secara otomatis",D:"Mengurangi latensi dengan menyajikan konten dari server terdekat dengan pengguna",E:"Meningkatkan skalabilitas website untuk menangani traffic tinggi"},a:"C",e:"CDN tidak memperbaiki kode/syntax error — itu bukan fungsinya; CDN fokus pada distribusi konten, kecepatan, dan proteksi traffic."},
{n:91,q:"Apa perbedaan utama antara HTTP dan HTTPS dalam aspek keamanan transmisi data?",o:{A:"HTTP lebih cepat karena tidak menggunakan enkripsi, sedangkan HTTPS lebih lambat",B:"HTTP menggunakan enkripsi SSL/TLS, sedangkan HTTPS tidak memerlukan enkripsi",C:"HTTPS menggunakan enkripsi SSL/TLS untuk melindungi data, sementara HTTP mengirimkan data tanpa enkripsi",D:"Keduanya menggunakan enkripsi yang sama, hanya berbeda pada port yang digunakan",E:"HTTP lebih aman karena tersertifikasi, sedangkan HTTPS tidak memerlukan sertifikat"},a:"C",e:"HTTPS mengenkripsi data dengan SSL/TLS, sedangkan HTTP mengirim data tanpa enkripsi (lebih rentan disadap)."},
{n:92,q:"Dalam mengelola website, apa yang dimaksud dengan caching dan apa manfaatnya?",o:{A:"Proses menghapus data lama dari server secara berkala",B:"Menyimpan salinan data atau halaman di lokasi terdekat untuk akses lebih cepat dan mengurangi beban server",C:"Proses backup otomatis data website ke cloud storage",D:"Membatasi jumlah koneksi simultan dari pengguna",E:"Mengenkripsi semua komunikasi antara client dan server"},a:"B",e:"Caching menyimpan salinan data agar akses berikutnya lebih cepat dan beban server berkurang."},
{n:93,q:"Apa yang dimaksud dengan metadata website dan mengapa penting untuk SEO?",o:{A:"Data tentang jumlah pengguna yang mengakses website setiap hari",B:"Informasi deskriptif tentang halaman web seperti title, description, dan keywords yang membantu search engine memahami konten",C:"Informasi tentang kecepatan loading website",D:"Data tentang browser dan perangkat yang digunakan pengunjung",E:"Informasi lokasi server tempat website di-hosting"},a:"B",e:"Metadata (title, description, keywords) membantu search engine memahami dan mengindeks konten halaman dengan tepat."},
{n:94,q:"Dalam mengelola website, apa fungsi utama dari file .htaccess?",o:{A:"Mengonfigurasi pengaturan server Apache, termasuk rewrite rules dan kontrol akses",B:"Menyimpan informasi login pengguna website",C:"Mengenkripsi semua file di server secara otomatis",D:"Membuat backup otomatis dari database website",E:"Mengatur tema dan desain tampilan website"},a:"A",e:".htaccess adalah file konfigurasi server Apache, digunakan untuk rewrite rules dan kontrol akses."},
{n:95,q:"Apa yang dimaksud dengan Hosting dalam konteks pengelolaan website?",o:{A:"Layanan penyewaan ruang penyimpanan data di server untuk menyimpan file-file website agar dapat diakses melalui internet",B:"Proses pembelian nama domain untuk website agar mudah diingat oleh pengunjung",C:"Software yang digunakan untuk mendesain tampilan website secara visual",D:"Teknik mengoptimalkan kecepatan loading halaman website menggunakan kompres file",E:"Protokol keamanan yang digunakan untuk mengenkripsi komunikasi antara client dan server"},a:"A",e:"Hosting adalah layanan penyewaan ruang penyimpanan server agar file website dapat diakses melalui internet."},
{n:96,q:"Dalam pengelolaan website, apa yang dimaksud dengan uptime dan mengapa penting untuk bisnis online?",o:{A:"Waktu yang diperlukan untuk mengunggah file ke server hosting website",B:"Persentase waktu server website beroperasi dengan normal dan dapat diakses oleh pengunjung",C:"Durasi maksimal yang diizinkan untuk melakukan backup data website secara berkala",D:"Kecepatan internet yang dibutuhkan untuk membuka website dengan lancar tanpa buffering",E:"Jumlah pengunjung yang dapat mengakses website secara bersamaan tanpa lag"},a:"B",e:"Uptime adalah persentase waktu server beroperasi normal dan dapat diakses pengunjung — penting karena downtime berarti kehilangan bisnis/pengunjung."},
{n:97,q:"Apa yang dimaksud dengan User Experience (UX) dalam desain dan pengelolaan website?",o:{A:"Kemampuan website untuk beradaptasi dengan berbagai ukuran layar perangkat pengguna",B:"Pengalaman keseluruhan pengguna saat berinteraksi dengan website, termasuk kemudahan navigasi, kecepatan, dan kepuasan",C:"Fitur analitik yang melacak perilaku pengunjung dalam menggunakan website secara detail",D:"Strategi pemasaran digital yang digunakan untuk menarik pengunjung baru ke website",E:"Proses mengoptimalkan konten website agar mudah ditemukan di mesin pencari"},a:"B",e:"UX adalah pengalaman keseluruhan pengguna saat berinteraksi dengan website: navigasi, kecepatan, dan kepuasan."},
{n:98,q:"Apa peran dari footer dalam struktur dan pengelolaan website yang baik?",o:{A:"Menampilkan animasi menarik untuk meningkatkan interaktivitas halaman website",B:"Bagian bawah halaman yang berisi informasi penting seperti copyright, contact, sitemap, dan link footer lainnya",C:"Elemen navigasi utama untuk memudahkan pengguna berpindah antar halaman website",D:"Area untuk menampilkan iklan dan konten promosi dari mitra bisnis",E:"Section yang khusus dirancang untuk menampilkan testimonial dan review dari pelanggan"},a:"B",e:"Footer adalah bagian bawah halaman berisi informasi pelengkap seperti copyright, kontak, dan sitemap."},
{n:99,q:"Dalam pengelolaan website, apa yang dimaksud dengan Web Analytics dan informasi apa yang dapat diperoleh?",o:{A:"Proses pemantauan keamanan server untuk mencegah serangan cyber dan hacking pada website",B:"Pengumpulan dan analisis data tentang perilaku pengunjung website seperti traffic, durasi kunjungan, bounce rate, dan sumber pengunjung",C:"Layanan pencadangan data website secara berkala untuk mencegah kehilangan data penting",D:"Teknik optimasi database untuk mempercepat query dan response time server website",E:"Strategi pembaruan konten website secara rutin untuk meningkatkan relevansi di mesin pencari"},a:"B",e:"Web Analytics mengumpulkan & menganalisis data perilaku pengunjung: traffic, durasi kunjungan, bounce rate, sumber trafik, dsb."},
{n:100,q:"Apa yang dimaksud dengan Responsive Design dalam konteks pengembangan website modern?",o:{A:"Desain website yang dapat menyesuaikan layout dan konten secara otomatis sesuai ukuran layar perangkat yang digunakan pengunjung",B:"Kecepatan website dalam merespons perintah dari server ketika pengguna melakukan interaksi",C:"Kemampuan website untuk mendeteksi lokasi geografis pengunjung dan menampilkan konten yang relevan",D:"Fitur website yang memungkinkan pengguna untuk memberikan feedback dan komentar secara real-time",E:"Sistem keamanan website yang responsif terhadap ancaman keamanan dan dapat memblokir akses berbahaya"},a:"A",e:"Responsive Design berarti layout dan konten website menyesuaikan otomatis dengan ukuran layar perangkat pengunjung."}
,
{n:101,q:"Apa yang dimaksud dengan World Wide Web (WWW) dalam konteks internet?",o:{A:"Sebuah sistem jaringan komputer yang menghubungkan seluruh perangkat di dunia",B:"Sistem untuk berbagi dokumen dan informasi melalui internet menggunakan protokol HTTP/HTTPS",C:"Sebuah aplikasi perangkat lunak untuk mengelola basis data besar",D:"Protokol komunikasi yang digunakan hanya untuk mengirim email",E:"Sebuah mesin pencari yang mengindeks semua situs web di internet"},a:"B",e:"WWW adalah sistem berbagi dokumen/informasi melalui internet menggunakan protokol HTTP/HTTPS, berbeda dari internet itu sendiri (infrastruktur jaringan)."},
{n:102,q:"Dalam struktur URL https://www.example.com:8080/path/page.html?id=123, bagian manakah yang merupakan port?",o:{A:"https",B:"www.example.com",C:"8080",D:"/path/page.html",E:"id=123"},a:"C",e:"Angka setelah tanda titik dua (:) pada URL adalah nomor port — di sini 8080."},
{n:103,q:"Manakah dari pernyataan berikut yang BENAR tentang perbedaan website statis dan website dinamis?",o:{A:"Website statis diperbarui secara real-time, sedangkan website dinamis memerlukan pembaruan manual",B:"Website statis menampilkan konten yang sama untuk semua pengunjung, website dinamis dapat menampilkan konten berbeda berdasarkan input pengguna",C:"Website dinamis tidak memerlukan server untuk berfungsi, sementara website statis memerlukan server khusus",D:"Website statis lebih aman karena tidak terhubung dengan basis data, namun lebih mahal untuk dikembangkan",E:"Website dinamis hanya dapat diakses melalui protokol FTP, sedangkan website statis menggunakan HTTP"},a:"B",e:"Sama seperti soal 85: statis = konten sama untuk semua orang; dinamis = konten berubah berdasarkan input pengguna/data."},
{n:104,q:"Apa fungsi utama dari Domain Name System (DNS) dalam infrastruktur website?",o:{A:"Mengenkripsi data pengguna saat bertransaksi di website",B:"Mengubah alamat IP numerik menjadi nama domain yang mudah diingat",C:"Menyimpan semua file dan database website di server",D:"Mengontrol akses pengguna ke halaman-halaman tertentu di website",E:"Mempercepat kecepatan loading website dengan cache data"},a:"B",e:"DNS berfungsi menerjemahkan (dua arah, tapi umumnya digambarkan) antara nama domain dan alamat IP agar mudah diakses manusia."},
{n:105,q:"Protokol mana yang digunakan untuk mentransfer file dengan aman ke server web, dan protokol manakah yang digunakan untuk browsing konten web?",o:{A:"SFTP untuk transfer file, FTP untuk browsing",B:"FTP untuk transfer file, HTTP untuk browsing",C:"SFTP untuk transfer file, HTTPS untuk browsing",D:"HTTP untuk transfer file, HTTPS untuk browsing",E:"HTTPS untuk transfer file, DNS untuk browsing"},a:"C",e:"SFTP (secure FTP) digunakan untuk transfer file yang AMAN, sedangkan HTTPS digunakan untuk browsing konten web yang aman."},
{n:106,q:"Dalam mengelola website, hosting dapat diartikan sebagai?",o:{A:"Proses mendaftarkan nama domain ke registrar",B:"Layanan menyimpan file website dan membuat website dapat diakses 24/7 melalui internet",C:"Aplikasi software untuk membuat dan mengedit konten website",D:"Protokol komunikasi antara browser dan server web",E:"Proses mengoptimalkan website agar tampil di halaman pertama mesin pencari"},a:"B",e:"Hosting adalah layanan menyimpan file website sekaligus membuatnya dapat diakses 24/7 melalui internet."},
{n:107,q:"Apa keuntungan utama menggunakan HTTPS dibandingkan HTTP pada sebuah website?",o:{A:"HTTPS lebih cepat dalam mentransfer data karena menggunakan kompresi otomatis",B:"HTTPS mengenkripsi data komunikasi antara browser dan server, sehingga lebih aman dari ancaman keamanan",C:"HTTPS memerlukan biaya hosting yang lebih murah dibanding HTTP",D:"HTTPS tidak memerlukan sertifikat SSL, sehingga lebih mudah diimplementasikan",E:"HTTPS hanya dapat digunakan untuk website e-commerce, bukan untuk website informasi"},a:"B",e:"Keuntungan utama HTTPS adalah enkripsi data komunikasi, melindungi data dari penyadapan/manipulasi."},
{n:108,q:"Perusahaan ingin membangun website e-commerce dengan fitur real-time inventory dan transaksi pembayaran online. Jenis website apakah yang paling sesuai?",o:{A:"Website statis karena lebih cepat dan mudah diakses",B:"Website dinamis karena dapat memproses data dan berinteraksi dengan database",C:"Website responsif karena dapat diakses dari berbagai perangkat",D:"Website portal karena menyediakan banyak layanan dalam satu tempat",E:"Website blog karena dapat diupdate secara berkala dengan informasi terbaru"},a:"B",e:"Fitur real-time inventory dan transaksi online memerlukan pemrosesan data & interaksi database — ini ciri website dinamis."},
{n:109,q:"Apa yang akan terjadi jika layanan DNS mengalami gangguan?",o:{A:"Website akan menampilkan konten dengan kecepatan lebih lambat",B:"User tidak dapat mengakses website karena browser tidak bisa menemukan alamat IP dari domain",C:"Website akan secara otomatis beralih ke protokol HTTP",D:"Server web akan menolak semua permintaan koneksi dari user",E:"Konten website akan dienkripsi dan tidak bisa ditampilkan"},a:"B",e:"Tanpa DNS berfungsi, browser tidak bisa menerjemahkan domain menjadi IP address, sehingga website tidak dapat diakses sama sekali."},
{n:110,q:"Manakah strategi berikut yang PALING efektif untuk mengoptimalkan performa website dengan mengurangi waktu loading?",o:{A:"Menambah jumlah halaman website agar konten lebih banyak",B:"Menggunakan Content Delivery Network (CDN) untuk mendistribusikan konten dari server yang lebih dekat dengan user",C:"Mengubah warna desain website menjadi lebih cerah",D:"Mengganti hosting dengan paket yang lebih mahal",E:"Menambahkan lebih banyak plugin dan script pihak ketiga"},a:"B",e:"CDN mendistribusikan konten dari server terdekat dengan pengguna, secara langsung mengurangi latensi dan waktu loading."},
{n:111,q:"Apa risiko utama jika sebuah website tidak melakukan backup secara berkala?",o:{A:"Website akan mengalami penurunan traffic pengunjung",B:"Data website dapat hilang selamanya jika terjadi kerusakan server atau serangan cyber",C:"Biaya hosting akan meningkat secara otomatis setiap bulannya",D:"Semua user akan kehilangan akses ke akun mereka tanpa bisa dipulihkan",E:"Desain website akan berubah menjadi tidak valid menurut standar HTML"},a:"B",e:"Tanpa backup berkala, data website berisiko hilang permanen jika terjadi kerusakan server atau serangan siber."},
{n:112,q:"Apa yang ditunjukkan oleh padlock icon dan 'HTTPS' pada address bar browser?",o:{A:"Website telah dipercaya oleh semua antivirus di dunia",B:"Koneksi antara browser dan server dienkripsi dan data pengguna terlindungi dari penyadapan",C:"Website tidak pernah akan mengalami serangan malware atau phishing",D:"Server website berlokasi di negara dengan standar keamanan tertinggi",E:"Semua file yang diunduh dari website dijamin 100% aman dan tidak berisi virus"},a:"B",e:"Padlock + HTTPS menandakan koneksi terenkripsi (SSL/TLS), melindungi data dari penyadapan — bukan jaminan bebas malware sepenuhnya."},
{n:113,q:"Manakah pernyataan yang PALING TEPAT mendeskripsikan perbedaan frontend dan backend?",o:{A:"Frontend adalah bagian server dan backend adalah bagian yang dilihat user di browser",B:"Frontend adalah tampilan dan interaksi user di browser, sedangkan backend mengelola logika bisnis, database, dan pemrosesan data di server",C:"Frontend menggunakan bahasa pemrograman Python dan backend menggunakan HTML",D:"Frontend lebih penting daripada backend untuk menentukan kecepatan website",E:"Frontend dan backend tidak perlu berkomunikasi satu sama lain dalam operasional website"},a:"B",e:"Frontend = apa yang dilihat/diinteraksikan user di browser; backend = logika bisnis, database, dan pemrosesan data di sisi server."},
{n:114,q:"Apa manfaat utama dari penerapan responsive design pada sebuah website?",o:{A:"Mengurangi biaya hosting dan server website",B:"Website dapat menyesuaikan tampilan dan layout secara otomatis sesuai dengan ukuran layar perangkat yang mengaksesnya",C:"Meningkatkan kecepatan loading website hingga 10 kali lipat",D:"Melindungi website dari serangan hacker dan malware",E:"Memastikan semua user menggunakan browser yang sama untuk pengalaman optimal"},a:"B",e:"Sama seperti soal 100: manfaat utamanya adalah tampilan menyesuaikan otomatis dengan ukuran layar berbagai perangkat."},
{n:115,q:"Dalam pengelolaan website, Content Delivery Network (CDN) berfungsi untuk?",o:{A:"Mengenkripsi semua data yang ditransmisikan antara client dan server",B:"Mendistribusikan konten website ke berbagai server di lokasi geografis berbeda untuk mempercepat akses",C:"Mengelola database website dan menyimpan informasi pengguna",D:"Mengubah kode HTML menjadi format yang dapat dipahami oleh browser",E:"Memverifikasi identitas pemilik website melalui sertifikat digital"},a:"B",e:"CDN mendistribusikan konten ke server di berbagai lokasi geografis agar akses lebih cepat bagi pengguna di lokasi mana pun."},
{n:116,q:"Administrator website ingin mengetahui jumlah pengunjung harian, halaman paling banyak dikunjungi, dan asal traffic. Tool apa yang paling tepat digunakan?",o:{A:"Firewall dan Access Control List",B:"Web Analytics seperti Google Analytics",C:"SSH dan Remote Desktop Protocol",D:"File Transfer Protocol dan SFTP",E:"Load Balancer dan Monitoring Server"},a:"B",e:"Web Analytics (misal Google Analytics) adalah tool tepat untuk melacak jumlah pengunjung, halaman populer, dan sumber traffic."},
{n:117,q:"Ketika sebuah website tiba-tiba tidak dapat diakses meskipun server masih aktif, masalah mana yang paling mungkin terjadi?",o:{A:"Sertifikat SSL/TLS website telah kadaluarsa",B:"Kapasitas RAM server tidak mencukupi",C:"Domain website belum didaftarkan di registrar domain",D:"Konfigurasi DNS pointer tidak mengarah ke IP address server yang benar",E:"Konten website menggunakan format file yang tidak kompatibel dengan browser"},a:"D",e:"Jika server aktif tapi website tak bisa diakses, kemungkinan besar DNS pointer (A record) salah arah sehingga permintaan tidak sampai ke server yang benar."},
{n:118,q:"Manakah pernyataan yang paling akurat tentang fungsi API (Application Programming Interface) dalam konteks website?",o:{A:"API adalah protokol khusus yang menggantikan HTTP untuk komunikasi lebih cepat",B:"API memungkinkan aplikasi frontend dan backend berkomunikasi serta bertukar data dengan cara yang terdefinisi",C:"API adalah teknologi enkripsi yang melindungi semua data dalam transit",D:"API adalah server web yang khusus digunakan hanya untuk menyimpan gambar dan video",E:"API adalah standar penamaan file yang digunakan dalam penamaan resource website"},a:"B",e:"API adalah antarmuka yang memungkinkan dua sistem (misal frontend & backend) berkomunikasi dan bertukar data secara terstruktur."},
{n:119,q:"Developer ingin mengoptimalkan ukuran file gambar tanpa mengurangi kualitas visual secara signifikan. Teknik mana yang paling sesuai?",o:{A:"Menghapus semua gambar dari website dan menggantinya dengan teks deskriptif",B:"Meningkatkan kapasitas RAM server untuk mempercepat pemrosesan gambar",C:"Menggunakan format file gambar yang lebih modern dengan kompresi lebih baik, seperti WebP atau AVIF",D:"Membuat salinan website di server yang berbeda untuk membagi beban kerja",E:"Mengubah protokol dari HTTP menjadi HTTPS untuk mengakselerasi transfer data"},a:"C",e:"Format gambar modern seperti WebP/AVIF memberikan kompresi lebih baik tanpa banyak mengorbankan kualitas visual."},
{n:120,q:"Apa tujuan utama dari implementasi security headers seperti Content-Security-Policy (CSP) dan X-Frame-Options?",o:{A:"Mempercepat waktu loading halaman website secara keseluruhan",B:"Melindungi website dari serangan keamanan tertentu seperti XSS, clickjacking, dan injeksi konten berbahaya",C:"Mengurangi jumlah request HTTP yang dikirim oleh browser ke server",D:"Memaksa browser untuk selalu menggunakan HTTPS dalam setiap koneksi ke website",E:"Mengatur izin akses pengguna terhadap fitur-fitur tertentu dalam website"},a:"B",e:"Security headers seperti CSP dan X-Frame-Options dirancang khusus untuk melindungi website dari serangan seperti XSS dan clickjacking."}
,
{n:121,q:"Apa yang dimaksud dengan website statis?",o:{A:"Website yang kontennya dapat berubah secara real-time tanpa perlu reload halaman",B:"Website yang kontennya tidak berubah dan ditampilkan sama untuk semua pengunjung",C:"Website yang hanya dapat diakses oleh admin dan pengguna terdaftar",D:"Website yang menggunakan basis data untuk menyimpan semua kontennya",E:"Website yang dirancang khusus untuk perangkat mobile saja"},a:"B",e:"Website statis menampilkan konten tetap yang sama untuk setiap pengunjung, tanpa personalisasi berbasis database."},
{n:122,q:"Protokol mana yang umumnya digunakan untuk mentransfer file ke web server saat melakukan upload ke hosting?",o:{A:"HTTP",B:"SMTP",C:"FTP",D:"DNS",E:"SSL"},a:"C",e:"FTP (File Transfer Protocol) adalah protokol standar untuk mengunggah/mentransfer file ke web server hosting."},
{n:123,q:"Dalam pengelolaan website, apa fungsi utama dari Content Management System (CMS)?",o:{A:"Mengatur keamanan server dan mencegah serangan malware",B:"Menyediakan antarmuka untuk mengelola konten website tanpa perlu coding",C:"Menyimpan semua data pribadi pengunjung website",D:"Mengoptimalkan kecepatan loading website secara otomatis",E:"Menerjemahkan konten website ke berbagai bahasa"},a:"B",e:"CMS (seperti WordPress) memberikan antarmuka untuk mengelola konten website tanpa perlu menulis kode dari nol."},
{n:124,q:"Apa perbedaan utama antara domain dan hosting?",o:{A:"Domain adalah nama website, hosting adalah tempat penyimpanan file website",B:"Domain adalah tempat penyimpanan file, hosting adalah nama website",C:"Domain dan hosting adalah hal yang sama, hanya istilah berbeda",D:"Domain digunakan untuk email, hosting untuk file website",E:"Domain adalah layanan gratis, hosting harus dibayar"},a:"A",e:"Domain adalah alamat/nama website yang mudah diingat; hosting adalah tempat penyimpanan file-file website di server."},
{n:125,q:"Tool apa yang paling tepat digunakan untuk mengedit dan membuat struktur HTML/CSS sebuah website secara lokal?",o:{A:"Text Editor atau Code Editor seperti Visual Studio Code",B:"Web Browser seperti Chrome atau Firefox",C:"CMS seperti WordPress tanpa menggunakan hosting",D:"Database management tool seperti PhpMyAdmin",E:"FTP Client seperti FileZilla saja tanpa tools lain"},a:"A",e:"Code Editor seperti VS Code adalah tool standar untuk menulis dan mengedit struktur HTML/CSS secara lokal."},
{n:126,q:"Mengapa HTTPS lebih aman daripada HTTP untuk mengelola website?",o:{A:"HTTPS memiliki loading yang lebih cepat dibanding HTTP",B:"HTTPS mengenkripsi data yang dikirim antara browser dan server, sedangkan HTTP tidak",C:"HTTPS menggunakan lebih banyak server dibanding HTTP",D:"HTTPS tidak memerlukan sertifikat SSL seperti HTTP",E:"HTTPS hanya digunakan untuk website e-commerce, HTTP untuk website lain"},a:"B",e:"HTTPS mengenkripsi komunikasi data browser-server dengan SSL/TLS, sementara HTTP mengirim data secara terbuka/tidak terenkripsi."},
{n:127,q:"Dalam mengelola website, apa yang dimaksud dengan SEO (Search Engine Optimization)?",o:{A:"Teknik untuk meningkatkan ranking website di hasil pencarian search engine",B:"Proses menghapus semua link eksternal dari website",C:"Sistem keamanan untuk melindungi database website dari hacker",D:"Fitur yang memungkinkan website diakses offline tanpa internet",E:"Tool untuk mengompres semua file website agar lebih ringan"},a:"A",e:"SEO adalah teknik/strategi untuk meningkatkan peringkat website di hasil pencarian mesin pencari."},
{n:128,q:"Apa yang dimaksud dengan bandwidth dalam konteks pengelolaan website?",o:{A:"Jumlah ruang penyimpanan data pada server web",B:"Kecepatan transfer data antara server dan client dalam periode waktu tertentu",C:"Jenis protokol yang digunakan untuk mengenkripsi data website",D:"Nama domain alternatif yang digunakan untuk website backup",E:"Jumlah pengunjung yang dapat mengakses website secara bersamaan"},a:"B",e:"Bandwidth mengacu pada kecepatan/kapasitas transfer data antara server dan client dalam periode waktu tertentu (sama seperti soal 88)."},
{n:129,q:"Dalam pengelolaan website, apa fungsi utama dari DNS (Domain Name System)?",o:{A:"Mengenkripsi komunikasi antara browser dan server",B:"Menerjemahkan nama domain menjadi alamat IP server",C:"Menyimpan file dan database website di server",D:"Mengontrol akses pengguna ke halaman website tertentu",E:"Mengoptimalkan kecepatan loading halaman website"},a:"B",e:"Fungsi utama DNS adalah menerjemahkan nama domain menjadi alamat IP server (sama seperti soal 83 & 104)."},
{n:130,q:"Apa yang dimaksud dengan caching dalam konteks pengelolaan dan performa website?",o:{A:"Proses backup data website secara berkala ke server cadangan",B:"Menyimpan salinan data atau halaman web di memori untuk akses lebih cepat",C:"Proses kompresi file untuk mengurangi ukuran transfer data",D:"Sistem keamanan yang melindungi website dari serangan malware",E:"Metode untuk mengalihkan traffic website ke server lain saat overload"},a:"B",e:"Caching menyimpan salinan data/halaman di memori agar akses berikutnya lebih cepat, sama seperti definisi di soal 92."},
{n:131,q:"Apa fungsi utama dari file robots.txt dalam pengelolaan website?",o:{A:"Mengamankan website dari serangan brute force",B:"Mengatur izin akses web crawler atau bot untuk mengindex halaman website",C:"Mengoptimalkan gambar dan file media di website",D:"Membuat backup otomatis dari semua file website",E:"Mengenkripsi komunikasi antara client dan server web"},a:"B",e:"robots.txt mengatur izin akses crawler/bot mesin pencari terhadap halaman website (sama seperti soal 89)."},
{n:132,q:"Dalam pengelolaan website, apa yang dimaksud dengan uptime?",o:{A:"Waktu yang diperlukan untuk mengupload file ke server",B:"Persentase waktu server website aktif dan dapat diakses pengunjung",C:"Jumlah pembaruan konten yang dilakukan dalam sebulan",D:"Kecepatan internet yang dibutuhkan untuk mengakses website",E:"Waktu tunggu respons dari server saat pertama kali diakses"},a:"B",e:"Uptime adalah persentase waktu server aktif dan dapat diakses, sama seperti definisi soal 96."},
{n:133,q:"Apa perbedaan utama antara web server dan application server dalam pengelolaan website?",o:{A:"Web server hanya melayani file statis, sementara application server menjalankan kode dinamis",B:"Web server lebih cepat, application server lebih aman",C:"Web server untuk website kecil, application server untuk website besar",D:"Web server menggunakan HTTP, application server menggunakan protokol khusus",E:"Web server terletak di client, application server terletak di cloud"},a:"A",e:"Web server umumnya melayani konten statis (HTML/gambar), sementara application server menjalankan logika/kode dinamis (memproses data)."},
{n:134,q:"Apa yang dimaksud dengan redirect dan kapan biasanya digunakan?",o:{A:"Mengarahkan pengguna dari satu URL ke URL lain, digunakan saat mengganti alamat website atau menghapus halaman lama",B:"Proses mengubah kode HTML menjadi tampilan visual di browser",C:"Metode untuk menyembunyikan alamat IP server dari pengunjung",D:"Sistem pencegahan akses otomatis ke halaman yang sedang dimaintenance",E:"Teknik untuk membagi traffic website ke beberapa server berbeda"},a:"A",e:"Redirect mengarahkan pengguna dari satu URL ke URL lain, umumnya dipakai saat alamat berubah atau halaman lama dihapus."},
{n:135,q:"Apa yang dimaksud dengan responsive design dalam pengembangan website modern?",o:{A:"Desain website yang hanya dapat diakses melalui perangkat desktop dengan resolusi tinggi",B:"Desain website yang menyesuaikan tampilannya secara otomatis sesuai ukuran layar dan perangkat yang digunakan",C:"Desain website yang memberikan respons feedback kepada setiap klik pengguna dengan animasi",D:"Desain website yang menggunakan banyak warna-warna responsif dan kontras tinggi",E:"Desain website yang hanya mengoptimalkan kecepatan loading di perangkat mobile"},a:"B",e:"Responsive design menyesuaikan tampilan secara otomatis sesuai ukuran layar/perangkat, sama seperti definisi soal 100 & 114."},
{n:136,q:"Dalam pengelolaan website, apa yang dimaksud dengan sitemap?",o:{A:"Peta geografis yang menunjukkan lokasi server website Anda berada",B:"File atau halaman yang berisi daftar lengkap URL dan struktur hirarki website untuk membantu mesin pencari dan pengunjung navigasi",C:"Desain visual layout website yang menampilkan semua warna dan font yang digunakan",D:"Program yang memetakan setiap klik pengguna untuk analisis perilaku browsing",E:"Sertifikat keamanan yang memvalidasi kepemilikan website di mesin pencari"},a:"B",e:"Sitemap adalah daftar lengkap URL dan struktur hirarki website yang membantu mesin pencari (dan pengunjung) melakukan navigasi."},
{n:137,q:"Apa fungsi utama dari web analytics dalam pengelolaan website?",o:{A:"Menganalisis kode HTML dan CSS untuk menemukan error dalam struktur halaman",B:"Mengumpulkan, mengukur, dan menganalisis data tentang perilaku pengunjung website untuk optimasi performa dan strategi",C:"Mengelola dan mengorganisir semua file gambar yang digunakan di website",D:"Menjamin keamanan data pelanggan melalui enkripsi tingkat tinggi",E:"Membuat laporan statistik tentang jumlah server yang menampilkan website Anda"},a:"B",e:"Web analytics mengumpulkan dan menganalisis data perilaku pengunjung untuk mendukung optimasi performa dan strategi bisnis."},
{n:138,q:"Dalam pengelolaan website, apa yang dimaksud dengan metadata?",o:{A:"Data yang menyimpan semua informasi pribadi pengunjung website secara otomatis",B:"Informasi deskriptif tentang halaman web (seperti title, description, keywords) yang membantu mesin pencari memahami konten",C:"Struktur database yang digunakan untuk menyimpan semua konten website",D:"Jenis file yang hanya dapat dibuka oleh administrator website",E:"Sistem notifikasi otomatis ketika ada perubahan pada halaman website"},a:"B",e:"Metadata adalah informasi deskriptif (title, description, keywords) yang membantu mesin pencari memahami konten halaman, sama seperti soal 93."},
{n:139,q:"Apa perbedaan utama antara staging environment dan production environment dalam pengelolaan website?",o:{A:"Staging adalah backup server, sedangkan production adalah server utama yang aktif melayani pengunjung",B:"Staging digunakan untuk testing dan pengembangan sebelum diluncurkan, sementara production adalah environment live yang diakses pengunjung nyata",C:"Staging lebih cepat daripada production dalam memproses data pengunjung",D:"Staging menggunakan HTTPS sementara production menggunakan HTTP untuk efisiensi",E:"Production adalah tempat menyimpan backup data, sedangkan staging adalah tempat menjalankan website asli"},a:"B",e:"Staging = lingkungan uji coba sebelum rilis; production = lingkungan live yang diakses pengunjung sesungguhnya."},
{n:140,q:"Apa yang dimaksud dengan 404 error dan apa penyebabnya?",o:{A:"Error yang terjadi ketika server website tidak memiliki cukup kapasitas penyimpanan",B:"Error yang muncul ketika pengunjung mencoba mengakses halaman atau resource yang tidak ditemukan atau telah dihapus dari server",C:"Error keamanan yang mengindikasikan akses tidak sah ke file-file website",D:"Error yang terjadi ketika database website mengalami kegagalan koneksi",E:"Error yang ditampilkan ketika browser tidak kompatibel dengan teknologi website"},a:"B",e:"404 Not Found muncul ketika halaman/resource yang diminta tidak ditemukan atau telah dihapus dari server."}
];

const STORAGE_KEY = 'wp-hosting-quiz-progress-v1';
let state = { answers: {}, current: 1 };

function loadState(){
  try{
    const raw = localStorage.getItem(STORAGE_KEY);
    if(raw){
      const parsed = JSON.parse(raw);
      if(parsed && typeof parsed === 'object' && parsed.answers){
        state = parsed;
      }
    }
  }catch(e){ /* ignore, start fresh */ }
}
function saveState(){
  try{ localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); }catch(e){ /* ignore */ }
}

const quizArea = document.getElementById('quizArea');
const summaryArea = document.getElementById('summaryArea');
const jumpWrap = document.getElementById('jumpWrap');
const jumpGrid = document.getElementById('jumpGrid');
const barFill = document.getElementById('barFill');
const scorePill = document.getElementById('scorePill');

function answeredCount(){ return Object.keys(state.answers).length; }
function correctCount(){
  let c = 0;
  for(const k in state.answers){
    const q = QUIZ.find(x=>x.n===Number(k));
    if(q && state.answers[k] === q.a) c++;
  }
  return c;
}

function updateProgress(){
  const total = QUIZ.length;
  const ans = answeredCount();
  barFill.style.width = (ans/total*100).toFixed(1) + '%';
  scorePill.textContent = ans + ' / ' + total + ' terjawab · ' + correctCount() + ' benar';
}

function renderJumpGrid(){
  jumpGrid.innerHTML = '';
  QUIZ.forEach(q=>{
    const b = document.createElement('button');
    b.className = 'jbtn';
    b.textContent = q.n;
    const ans = state.answers[q.n];
    if(q.n === state.current) b.classList.add('current');
    if(ans){
      b.classList.add(ans === q.a ? 'ok' : 'no');
    }
    b.addEventListener('click', ()=>{ state.current = q.n; saveState(); renderAll(); window.scrollTo({top:0, behavior:'smooth'}); });
    jumpGrid.appendChild(b);
  });
}

function renderQuestion(){
  const q = QUIZ.find(x=>x.n===state.current);
  if(!q){ quizArea.innerHTML=''; return; }
  const chosen = state.answers[q.n];
  const card = document.createElement('div');
  card.className = 'card';

  const num = document.createElement('div');
  num.className = 'qnum';
  num.textContent = 'Soal ' + q.n + ' dari ' + QUIZ.length;
  card.appendChild(num);

  const qt = document.createElement('p');
  qt.className = 'qtext';
  qt.textContent = q.q;
  card.appendChild(qt);

  const opts = document.createElement('div');
  opts.className = 'options';
  ['A','B','C','D','E'].forEach(letter=>{
    const btn = document.createElement('button');
    btn.className = 'opt';
    btn.innerHTML = '<span class="letter">'+letter+'</span><span>'+q.o[letter]+'</span>';
    if(chosen){
      btn.disabled = true;
      if(letter === q.a) btn.classList.add('correct');
      else if(letter === chosen) btn.classList.add('wrong');
    }
    btn.addEventListener('click', ()=>{
      if(state.answers[q.n]) return;
      state.answers[q.n] = letter;
      saveState();
      renderAll();
    });
    opts.appendChild(btn);
  });
  card.appendChild(opts);

  const fb = document.createElement('div');
  fb.className = 'feedback' + (chosen ? ' show ' + (chosen===q.a ? 'ok':'no') : '');
  if(chosen){
    fb.innerHTML = '<b>' + (chosen===q.a ? '✓ Benar!' : '✗ Kurang tepat — jawaban benar: ' + q.a) + '</b><span class="expl">' + q.e + '</span>';
  }
  card.appendChild(fb);

  const nav = document.createElement('div');
  nav.className = 'navrow';
  const prevBtn = document.createElement('button');
  prevBtn.className = 'navbtn';
  prevBtn.textContent = '← Sebelumnya';
  prevBtn.disabled = q.n <= 1;
  prevBtn.addEventListener('click', ()=>{ state.current = Math.max(1, q.n-1); saveState(); renderAll(); window.scrollTo({top:0,behavior:'smooth'}); });
  nav.appendChild(prevBtn);

  const nextBtn = document.createElement('button');
  nextBtn.className = 'navbtn primary';
  nextBtn.textContent = q.n >= QUIZ.length ? 'Lihat hasil →' : 'Berikutnya →';
  nextBtn.addEventListener('click', ()=>{
    if(q.n >= QUIZ.length){
      state.current = QUIZ.length + 1;
    } else {
      state.current = q.n + 1;
    }
    saveState(); renderAll(); window.scrollTo({top:0,behavior:'smooth'});
  });
  nav.appendChild(nextBtn);
  card.appendChild(nav);

  quizArea.innerHTML = '';
  quizArea.appendChild(card);
}

function renderSummary(){
  const total = QUIZ.length;
  const correct = correctCount();
  const ans = answeredCount();
  const pct = total ? Math.round(correct/total*100) : 0;

  const box = document.createElement('div');
  box.className = 'summary';
  box.innerHTML =
    '<h2>Hasil Latihan</h2>' +
    '<div class="bigscore">' + correct + ' / ' + total + '</div>' +
    '<p>' + pct + '% benar · ' + ans + ' dari ' + total + ' soal sudah dijawab.</p>';

  const wrong = QUIZ.filter(q => state.answers[q.n] && state.answers[q.n] !== q.a);
  if(wrong.length){
    const h3 = document.createElement('p');
    h3.style.fontWeight='600'; h3.style.color='var(--ink)'; h3.style.marginTop='4px';
    h3.textContent = 'Soal yang perlu dipelajari ulang (' + wrong.length + '):';
    box.appendChild(h3);
    wrong.forEach(q=>{
      const item = document.createElement('div');
      item.className = 'review-item';
      item.innerHTML = '<div class="rq">Soal ' + q.n + '. ' + q.q + '</div>' +
        '<div class="ra">Jawabanmu: ' + state.answers[q.n] + ' — Jawaban benar: ' + q.a + '. ' + q.e + '</div>';
      box.appendChild(item);
    });
  } else if(ans === total){
    const p = document.createElement('p');
    p.textContent = 'Mantap, semua soal yang dijawab benar!';
    box.appendChild(p);
  }

  const resetBtn = document.createElement('button');
  resetBtn.className = 'resetbtn';
  resetBtn.textContent = 'Ulangi dari awal';
  resetBtn.addEventListener('click', ()=>{
    if(confirm('Reset semua jawaban dan mulai ulang?')){
      state = { answers: {}, current: 1 };
      saveState(); renderAll(); window.scrollTo({top:0,behavior:'smooth'});
    }
  });
  box.appendChild(resetBtn);

  const backBtn = document.createElement('button');
  backBtn.className = 'navbtn';
  backBtn.style.width = '100%';
  backBtn.style.marginTop = '10px';
  backBtn.textContent = 'Kembali ke soal terakhir';
  backBtn.addEventListener('click', ()=>{
    state.current = Math.min(QUIZ.length, total);
    saveState(); renderAll(); window.scrollTo({top:0,behavior:'smooth'});
  });
  box.appendChild(backBtn);

  summaryArea.innerHTML = '';
  summaryArea.appendChild(box);
}

function renderAll(){
  updateProgress();
  renderJumpGrid();
  if(state.current > QUIZ.length){
    quizArea.innerHTML = '';
    jumpWrap.style.display = 'block';
    renderSummary();
  } else {
    summaryArea.innerHTML = '';
    jumpWrap.style.display = 'block';
    renderQuestion();
  }
}

loadState();
renderAll();
</script>
</body>
</html>
