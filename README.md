<html><html lang="id"><head><meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>SPMB SMPN 1 Lingga Tahun Pelajaran 2026/2027</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
<style>
body{margin:0;background:#f0f7ff;font-family:system-ui,sans-serif}
.wrap{max-width:440px;margin:auto;padding:16px 16px 90px}
.card{background:rgba(255,255,255,.8);backdrop-filter:blur(20px);border:1px solid rgba(255,255,255,.9);border-radius:24px;padding:18px}
.nav{position:fixed;bottom:0;left:0;right:0;height:64px;background:#fff;display:flex;justify-content:space-around;align-items:center}
.barbg{height:18px;background:#e5e7eb;border-radius:20px}.bar{height:18px;border-radius:20px}
input,button{width:100%;padding:12px;border-radius:14px}
.hidden{display:none}
</style></head><body>
<div class='wrap'>
<div id='home' class='hidden'><div class='card'>
<h2>Rekap Jalur Seleksi</h2>
<p>Afirmasi: 32</p><div class='barbg'><div class='bar' style='width:57%;background:#34d399'></div></div>
<p>Prestasi: 25</p><div class='barbg'><div class='bar' style='width:45%;background:#93c5fd'></div></div>
<p>Zonasi: 56</p><div class='barbg'><div class='bar' style='width:100%;background:#fdbb74'></div></div>
<p><b>Pendaftaran Ulang Tanggal 29–30 Juni 2026 sesuai jadwal nama pada tabel kelulusan.</b></p>
</div></div>

<div id='hasil'><div class='card'>
<h2>Hasil Seleksi SPMB SMP Negeri 1 Lingga</h2>
<input id='q' placeholder='Ketik nama siswa'>
<button onclick='cari()'>Hasil Seleksi</button>
<div id='out'></div>
</div></div>
</div>
<div class='nav'>
<div onclick="show('home')"><i class="fa-solid fa-chart-simple"></i><br>Home</div>
<div onclick="show('hasil')"><i class="fa-solid fa-address-card"></i><br>Hasil Seleksi</div>
</div>
<script>
const siswa=[
{name:"AFIKA DWI KAILA",Sekolah Asal:"SDN 001 LINGGA UTARA",Jalur pendaftaran:"AFIRMASI",Jadwal daftar ulang:"29 Juni 2026 08.00 WIB"},
{name:"AL HAWARY",Sekolah asal:"SDN 013 LINGGA",Jalur pendaftaran:"AFIRMASI",Jadwal daftar ulang:"29 Juni 2026 08.00 WIB"},
{name:"AL MUKRAMIN RABBANI",asal:"SDN 012 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"ALHADI NURHIDAYAT",asal:"SDN 009 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"ANUGRAH DWI HERISKA",asal:"SDN 012 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"APITRA DLARA",asal:"SDN 009 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"ARMAN SYAPUTRA",asal:"SDN 006 GUNUNG KIJANG",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"AUFAR",asal:"SDN 002 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"AYUP KURNIAWAN",asal:"SDN 006 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"BAYU GIFBRAN AL-GAZALY",asal:"SDN 006 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"DEKA AVINO ARASYID",asal:"SDN 014 LINGGA UTARA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"ELITA NOVIANTI",asal:"SDN 012 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"ERNI YUSNITA",asal:"SDN 013 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"FAHREZA ALVAREZQI",asal:"SDN 006 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"GHAZIA HAFIZHA",asal:"SDN 003 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"M. ALFIZZA SABIQ",asal:"SDN 006 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"M. REZA AL-FIQRI",asal:"SDN 006 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"MUHAMMAD RAFFI",asal:"SDN 012 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"MUHAMMAD THORIQ AL FAQIH",asal:"SDN 001 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"MUHAMMAD WILDAN FADAIL",asal:"SDN 001 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.15 WIB"},
{name:"NUR'AINA SHOLEHAH",asal:"SDN 003 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"OKY SAPUTRA LINGGA",asal:"SDN 002 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"QANITA SAJIDAH",asal:"SDN 009 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"QEYSA AULIA",asal:"SDN 006 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"RAJA AGUENSA",asal:"SDN 012 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"RARA ANDRIYANI",asal:"SDN 006 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"RAYYAN ILMARIZKI",asal:"SDN 001 LINGGA UTARA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"RESYA NURFAZWA",asal:"SDN 001 LINGGA UTARA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"RIA OKTIFIANA",asal:"SDN 009 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"SITI QOMARI LAILATUS SA'ADAH",asal:"SDN 003 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.30 WIB"},
{name:"SUCI SILVITA",asal:"SDN 012 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.45 WIB"},
{name:"ZAKY RAMADHAN",asal:"SDN 009 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.45 WIB"},

// PRESTASI
{name:"ALBY LUTHFY PRATAMA",asal:"SDN 013 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 08.45 WIB"},
{name:"ALFIRA KHAIRUNNISA",asal:"SDN 007 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 08.45 WIB"},
{name:"BALQIS QUDRATUNNADA",asal:"-",jalur:"PRESTASI",jadwal:"29 Juni 2026 08.45 WIB"},
{name:"DHIYA QISTINA SETIANIE",asal:"-",jalur:"PRESTASI",jadwal:"29 Juni 2026 08.45 WIB"},
{name:"DRAKIRA AQIFA NAYLA",asal:"SDN 001 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 08.45 WIB"},
{name:"JIA FISSILMIKAFFAH",asal:"SDN 004 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 08.45 WIB"},
{name:"KIASATINA FAEZYA",asal:"SDN 001 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 08.45 WIB"},
{name:"MOHAMMAD MA'RUF",asal:"SDN 012 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 08.45 WIB"},
// PRESTASI (lanjutan)
{name:"MUHAMMAD FHERALDI NOVIYANDA",asal:"-",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"NAYLA RAMADHANI",asal:"SDN 004 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"NAYRA AYU SABILA",asal:"SDN 009 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"SALWA SALSABILA PRASILIA",asal:"SDN 001 LINGGA UTARA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"SASKIA EKA PUTRI",asal:"SDN 004 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"SHAFIYYA RAMIKA WAHYUNI",asal:"SDN 004 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"TAUFIQUL HAKIM",asal:"SDII LUQMAN AL HAKIM",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"ALTHAR AKHTAR AL WAHID",asal:"-",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"ARIZTA RIZTY SAFITRI",asal:"-",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"ASHOFIA MARITZAHANA",asal:"SDN 004 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.00 WIB"},
{name:"ELZA DESVARIANI",asal:"-",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"HAFIS RIZAY RAMADHANI",asal:"SDN 003 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"HAZIQ AL - FARIZKY",asal:"SDN 013 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"KHAIRINNISWA",asal:"SDN 003 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"MALKA ATRIAYA FAWWAZI",asal:"-",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"NAWLA MIZWA AMBARIN",asal:"SDII LUQMAN AL HAKIM",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"ZHULFAIRA RAFIFA RHAMADANI B.",asal:"SDN 003 LINGGA",jalur:"PRESTASI",jadwal:"29 Juni 2026 09.15 WIB"},

// ZONASI
{name:"ADE RAHMA YULIA",asal:"SDN 006 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"AISHA FAZILLA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"ALFIAN FAHMI",asal:"SDN 007 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.15 WIB"},
{name:"ALISHA ZULFA KHAIRINA",asal:"SDN 006 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"ALLISA MAGFIRA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"ALYA KHAIRUNNISA",asal:"SDN 002 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"ANGMAR JUANGGI",asal:"SDN 007 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"AQMAL LUTHFILLAH FERNANDO",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"ARDIAN",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"DAFIYA CHALESTA",asal:"SDN 002 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"DANENDRA ALTAF FADHALISHABIR",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"DARIN FEBRI MAHARANI",asal:"SDN 003 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"DEWI MAHA TIKA",asal:"SDN 003 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.30 WIB"},
{name:"ELMIRA RISQI AULIA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"ERNA WATI",asal:"SDN 003 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"FAIDA ANNAILA",asal:"SDN 007 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"FAZA JULIANDA PUTRA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"FAZILLA MASTURA",asal:"SDN 007 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"INTAN NOVILA SARI",asal:"SDN 004 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"JIHAN TALITA ULFA",asal:"SDN 007 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"KENNETH JORDAN TEO",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"KENZIE KIRANA RAJNI",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"KHAIRA NADHIFA AZZAHRA",asal:"SDN 004 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 09.45 WIB"},
{name:"M.ZHAFRAN SYADRIFAL",asal:"SDN 013 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"MAULANADI RANGGA",asal:"SDII LUQMAN AL HAKIM",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"MAULIDIA NADIA",asal:"SDN 004 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"MIA FATIHA SYAHADA",asal:"SDN 006 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD ALGHIAN RADITHYA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD ALIF MIRZA",asal:"SDII LUQMAN AL HAKIM",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD FACHRY ALZAKI",asal:"SDIT AL-MADANI",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD FEZI JAYANDA",asal:"SDN 003 LUNGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD IQBAL",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"NAZHIFA AMEERA",asal:"SDN 003 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.00 WIB"},
{name:"NILA PRATAMI PUTRI",asal:"SDN 002 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"NUR KHAIRUNNISA",asal:"SDN 004 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"NURFATIHA AQILA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"NUSYAHIRA",asal:"SDN 002 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"PUTRI SELFY RAMADANI",asal:"SDN 006 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"RAFFA AKBAR AL QORI",asal:"SDN 004 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"RAFFI NAMZARI",asal:"SDN 006 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"RAFIE ILHAMSYAH",asal:"SDN 004 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"RAJA LETISHA ULFAIRA DIANNISA",asal:"SDN 004 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"REWIS LIANSYAH",asal:"SDN 003 LUNGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.15 WIB"},
{name:"RINDAYANI NURSALSABELLA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"RIZA AHMAD",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"ROZAQ ANDIKA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"SITI EARLYTA MUTIA",asal:"SDN 013 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"SOFIYA BAHAR",asal:"SDN 004 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"SYAFIRA SEPTIANA",asal:"SDN 006 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"SYAKILA WARDATUL UFAIRA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"TENGKU SALSABILA QURROTA A'YUN",asal:"SDII LUQMAN AL HAKIM",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"THIERRY SIMAMORA",asal:"SDN 01 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"YASMIN ALIFA VIANDARA",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"ZEYADATE UBAIDILLAH",asal:"SDN 001 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"KELVIN HAZIMULFIKRI",asal:"SDN 006 LINGGA",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
{name:"MUHAMMAD FAEYZA",asal:"SDII LUQMAN AL HAKIM",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"},
];
function show(id){home.classList.add('hidden');hasil.classList.add('hidden');document.getElementById(id).classList.remove('hidden')}
function cari(){
let q=document.getElementById('q').value.toUpperCase();
let r=siswa.filter(s=>s.name.toUpperCase().includes(q));
out.innerHTML=r.length?r.map(s=>`<div class='card'><h3>${s.name}</h3><p>${s.asal}</p><p>${s.jalur}</p><p>${s.jadwal}</p></div>`).join(''):'Data tidak ditemukan';
}
show('hasil');
</script></body></html>
