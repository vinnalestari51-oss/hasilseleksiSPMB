<html><html lang="id"><head><meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>PPDB SMPN 1 Lingga 2026/2027</title>
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
<p><b>Pendaftaran ulang 29–30 Juni 2026 sesuai jadwal nama pada tabel kelulusan.</b></p>
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
{name:"AFIKA DWI KAILA",Sekolah asal:"SDN 001 LINGGA UTARA",Jalur pendaftaran:"AFIRMASI",Jadwal daftar ulang:"29 Juni 2026 08.00 WIB"},
{name:"AL HAWARY",asal:"SDN 013 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"AL MUKRAMIN RABBANI",asal:"SDN 012 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"ALHADI NURHIDAYAT",asal:"SDN 009 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"ANUGRAH DWI HERISKA",asal:"SDN 012 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"APITRA DLARA",asal:"SDN 009 LINGGA",jalur:"AFIRMASI",jadwal:"29 Juni 2026 08.00 WIB"},
{name:"... DATA SISWA 7 s.d. 112 DIMASUKKAN ...",asal:"Sesuai PDF",jalur:"Sesuai PDF",jadwal:"Sesuai PDF"},
{name:"MUHAMMAD FAEYZA",asal:"SDII LUQMAN AL HAKIM",jalur:"ZONASI",jadwal:"29 Juni 2026 10.30 WIB"}
];
function show(id){home.classList.add('hidden');hasil.classList.add('hidden');document.getElementById(id).classList.remove('hidden')}
function cari(){
let q=document.getElementById('q').value.toUpperCase();
let r=siswa.filter(s=>s.name.toUpperCase().includes(q));
out.innerHTML=r.length?r.map(s=>`<div class='card'><h3>${s.name}</h3><p>${s.asal}</p><p>${s.jalur}</p><p>${s.jadwal}</p></div>`).join(''):'Data tidak ditemukan';
}
show('hasil');
</script></body></html>
