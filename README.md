<html><html lang="id"><head><meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Hasil Seleksi SPMB SMPN 1 Lingga TP. 2026/2027</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
<style>
body{margin:0;background:#f0f7ff;font-family:system-ui,sans-serif}
.wrap{max-width:440px;margin:auto;padding:16px 16px 90px}
.card{background:rgba(255,255,255,.8);backdrop-filter:blur(20px);border:1px solid rgba(255,255,255,.9);border-radius:24px;padding:18px}
.nav{position:fixed;bottom:0;left:0;right:0;height:64px;background:#fff;display:flex;justify-content:space-around;align-items:center}
.barbg{height:18px;background:#e5e7eb;border-radius:20px}.bar{height:18px;border-radius:20px}
input,button{width:100%;padding:12px;border-radius:14px}
.hidden{display:none}

/* EFEK BINTANG KEJORA KELULUSAN */
.star-field-overlay{
position:fixed;
top:0;left:0;width:100vw;height:100vh;
pointer-events:none;
z-index:999;
overflow:hidden;
display:none;
}
.kejora-star{
position:absolute;
color:#fbbf24;
filter:drop-shadow(0 0 8px #f59e0b);
animation:kejoraFly 2.8s ease-out forwards;
}
@keyframes kejoraFly{
0%{transform:scale(.2) translate(0,0) rotate(0deg);opacity:0}
20%{opacity:1;transform:scale(1.4) translate(10px,-20px) rotate(45deg)}
100%{opacity:0;transform:scale(.3) translate(60px,-120px) rotate(180deg)}
}
.lulus-banner{
margin-top:15px;
padding:18px;
border-radius:20px;
text-align:center;
background:linear-gradient(135deg,#2563eb,#1d4ed8);
color:white;
font-weight:700;
box-shadow:0 8px 20px rgba(37,99,235,.3);
animation:popLulus .6s ease;
}
@keyframes popLulus{
from{transform:scale(.5);opacity:0}
to{transform:scale(1);opacity:1}
}

</style></head><body>
<div id='kejora-overlay' class='star-field-overlay'></div>
<div class='wrap'>
<div id='home' class='hidden'><div class='card'>
<h2>Rekap Jalur Seleksi</h2>
<p>Afirmasi: 32</p><div class='barbg'><div class='bar' style='width:57%;background:#34d399'></div></div>
<p>Prestasi: 25</p><div class='barbg'><div class='bar' style='width:45%;background:#93c5fd'></div></div>
<p>Zonasi: 56</p><div class='barbg'><div class='bar' style='width:100%;background:#fdbb74'></div></div>
<p><b>daftar ulang tanggal sesuai jadwal, melengkapi persyaratan bagi yang belum lengkap, siswa menggunakan seragam SD dan membawa pena</b></p>
</div></div>

<div id='hasil'><div class='card'>
<h2>Hasil Seleksi</h2>
<input id='q' placeholder='Ketik 2 suku kata nama siswa'>
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
{name:"AFIKA DWI KAILA",asal:"SDN 001 LINGGA UTARA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"AL HAWARY",asal:"SDN 013 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"AL MUKRAMIN RABBANI",asal:"SDN 012 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"ALHADI NURHIDAYAT",asal:"SDN 009 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"ANUGRAH DWI HERISKA",asal:"SDN 012 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"APITRA DLARA",asal:"SDN 009 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"ARMAN SYAPUTRA",asal:"SDN 006 GUNUNG KIJANG",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"AUFAR",asal:"SDN 002 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"AYUP KURNIAWAN",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"BAYU GIFBRAN AL-GAZALY",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.00 WIB"},
{name:"DEKA AVINO ARASYID",asal:"SDN 014 LINGGA UTARA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"ELITA NOVIANTI",asal:"SDN 012 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"ERNI YUSNITA",asal:"SDN 013 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"FAHREZA ALVAREZQI",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"GHAZIA HAFIZHA",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"M. ALFIZZA SABIQ",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"M. REZA AL-FIQRI",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"MUHAMMAD RAFFI",asal:"SDN 012 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"MUHAMMAD THORIQ AL FAQIH",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"MUHAMMAD WILDAN FADAIL",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.15 WIB"},
{name:"NUR'AINA SHOLEHAH",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"OKY SAPUTRA LINGGA",asal:"SDN 002 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"QANITA SAJIDAH",asal:"SDN 009 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"QEYSA AULIA",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"RAJA AGUENSA",asal:"SDN 012 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"RARA ANDRIYANI",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"RAYYAN ILMARIZKI",asal:"SDN 001 LINGGA UTARA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"RESYA NURFAZWA",asal:"SDN 001 LINGGA UTARA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"RIA OKTIFIANA",asal:"SDN 009 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"SITI QOMARI LAILATUS SA'ADAH",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.30 WIB"},
{name:"SUCI SILVITA",asal:"SDN 012 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"ZAKY RAMADHAN",asal:"SDN 009 LINGGA",jalur:"Lolos Jalur AFIRMASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"ALBY LUTHFY PRATAMA",asal:"SDN 013 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"ALFIRA KHAIRUNNISA",asal:"SDN 007 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"BALQIS QUDRATUNNADA",asal:"-",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"DHIYA QISTINA SETIANIE",asal:"-",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"DRAKIRA AQIFA NAYLA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"JIA FISSILMIKAFFAH",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"KIASATINA FAEZYA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"MOHAMMAD MA'RUF",asal:"SDN 012 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 08.45 WIB"},
{name:"MUHAMMAD FHERALDI NOVIYANDA",asal:"-",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"NAYLA RAMADHANI",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"NAYRA AYU SABILA",asal:"SDN 009 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"SALWA SALSABILA PRASILIA",asal:"SDN 001 LINGGA UTARA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"SASKIA EKA PUTRI",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"SHAFIYYA RAMIKA WAHYUNI",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"TAUFIQUL HAKIM",asal:"SDII LUQMAN AL HAKIM",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"ALTHAR AKHTAR AL WAHID",asal:"-",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"ARIZTA RIZTY SAFITRI",asal:"-",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"ASHOFIA MARITZAHANA",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.00 WIB"},
{name:"ELZA DESVARIANI",asal:"-",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"HAFIS RIZAY RAMADHANI",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"HAZIQ AL - FARIZKY",asal:"SDN 013 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"KHAIRINNISWA",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"MALKA ATRIAYA FAWWAZI",asal:"-",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"NAWLA MIZWA AMBARIN",asal:"SDII LUQMAN AL HAKIM",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"ZHULFAIRA RAFIFA RHAMADANI B.",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur PRESTASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"ADE RAHMA YULIA",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"AISHA FAZILLA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"ALFIAN FAHMI",asal:"SDN 007 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.15 WIB"},
{name:"ALISHA ZULFA KHAIRINA",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"ALLISA MAGFIRA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"ALYA KHAIRUNNISA",asal:"SDN 002 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"ANGMAR JUANGGI",asal:"SDN 007 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"AQMAL LUTHFILLAH FERNANDO",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"ARDIAN",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"DAFIYA CHALESTA",asal:"SDN 002 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"DANENDRA ALTAF FADHALISHABIR",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"DARIN FEBRI MAHARANI",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"DEWI MAHA TIKA",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.30 WIB"},
{name:"ELMIRA RISQI AULIA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"ERNA WATI",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"FAIDA ANNAILA",asal:"SDN 007 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"FAZA JULIANDA PUTRA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"FAZILLA MASTURA",asal:"SDN 007 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"INTAN NOVILA SARI",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"JIHAN TALITA ULFA",asal:"SDN 007 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"KENNETH JORDAN TEO",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"KENZIE KIRANA RAJNI",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"KHAIRA NADHIFA AZZAHRA",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 09.45 WIB"},
{name:"M.ZHAFRAN SYADRIFAL",asal:"SDN 013 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"MAULANADI RANGGA",asal:"SDII LUQMAN AL HAKIM",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"MAULIDIA NADIA",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"MIA FATIHA SYAHADA",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD ALGHIAN RADITHYA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD ALIF MIRZA",asal:"SDII LUQMAN AL HAKIM",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD FACHRY ALZAKI",asal:"SDIT AL-MADANI",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD FEZI JAYANDA",asal:"SDN 003 LUNGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"MUHAMMAD IQBAL",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"NAZHIFA AMEERA",asal:"SDN 003 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.00 WIB"},
{name:"NILA PRATAMI PUTRI",asal:"SDN 002 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"NUR KHAIRUNNISA",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"NURFATIHA AQILA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"NUSYAHIRA",asal:"SDN 002 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"PUTRI SELFY RAMADANI",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"RAFFA AKBAR AL QORI",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"RAFFI NAMZARI",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"RAFIE ILHAMSYAH",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"RAJA LETISHA ULFAIRA DIANNISA",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"REWIS LIANSYAH",asal:"SDN 003 LUNGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.15 WIB"},
{name:"RINDAYANI NURSALSABELLA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"RIZA AHMAD",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"ROZAQ ANDIKA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"SITI EARLYTA MUTIA",asal:"SDN 013 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"SOFIYA BAHAR",asal:"SDN 004 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"SYAFIRA SEPTIANA",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"SYAKILA WARDATUL UFAIRA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"TENGKU SALSABILA QURROTA A'YUN",asal:"SDII LUQMAN AL HAKIM",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"THIERRY SIMAMORA",asal:"SDN 01 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"YASMIN ALIFA VIANDARA",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"ZEYADATE UBAIDILLAH",asal:"SDN 001 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"KELVIN HAZIMULFIKRI",asal:"SDN 006 LINGGA",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
{name:"MUHAMMAD FAEYZA",asal:"SDII LUQMAN AL HAKIM",jalur:"Lolos Jalur ZONASI",jadwal:"Daftar Ulang pada 29 Juni 2026 10.30 WIB"},
];
function show(id){home.classList.add('hidden');hasil.classList.add('hidden');document.getElementById(id).classList.remove('hidden')}

function triggerKejoraEffect(){
 const overlay=document.getElementById('kejora-overlay');
 overlay.innerHTML='';
 overlay.style.display='block';

 for(let i=0;i<40;i++){
   let star=document.createElement('i');
   star.className='fa-solid fa-star kejora-star';
   star.style.left=Math.random()*100+'vw';
   star.style.top=Math.random()*100+'vh';
   star.style.fontSize=(10+Math.random()*18)+'px';
   star.style.animationDelay=Math.random()*1+'s';
   overlay.appendChild(star);
 }

 setTimeout(()=>overlay.style.display='none',3500);
}

function cari(){
let q=document.getElementById('q').value.trim().toUpperCase();

let jumlahKata = q.split(/\s+/).filter(k=>k.length>0).length;

if(jumlahKata < 2){
out.innerHTML = `
<div class='card' style='text-align:center;color:#dc2626'>
<i class='fa-solid fa-triangle-exclamation' style='font-size:30px'></i>
<h3>Masukkan Nama Lengkap</h3>
<p>Silakan ketik minimal <b>2 suku kata</b> dari nama lengkap siswa.</p>
</div>`;
return;
}

let r=siswa.filter(s=>s.name.toUpperCase().includes(q));
out.innerHTML=r.length?r.map(s=>`
<div class='card'>
<div class='lulus-banner'>
🎉 SELAMAT, ANDA DINYATAKAN LULUS<br>
<span>${s.jalur}</span>
</div>
<h3>${s.name}</h3>
<p>${s.asal}</p>
<p>${s.jalur}</p>
<p>${s.jadwal}</p>
</div>`).join(''):'Data tidak ditemukan';

if(r.length){ triggerKejoraEffect(); }
}
show('hasil');
</script></body></html>
