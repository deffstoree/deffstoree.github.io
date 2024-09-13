<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Paket Siluman - Pembelian</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            color: #333;
            padding-bottom: 60px; /* Ruang tambahan di bawah konten untuk footer */
        }
        header {
            background-color: #4CAF50;
            color: white;
            padding: 20px;
            text-align: center;
        }
        .container {
            max-width: 800px;
            margin: auto;
            padding: 20px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin-top: 20px;
        }
        h1 {
            font-size: 24px;
            margin-bottom: 10px;
        }
        h2 {
            font-size: 20px;
            margin-bottom: 15px;
        }
        form {
            max-width: 600px;
            margin: auto;
        }
        label {
            display: block;
            margin-top: 10px;
            font-weight: bold;
        }
        input, select, button {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            font-size: 16px;
            border-radius: 4px;
            border: 1px solid #ddd;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
            margin-top: 10px;
        }
        button:hover {
            background-color: #45a049;
        }
        .error {
            color: red;
            margin-top: 5px;
        }
        .total {
            font-weight: bold;
            margin-top: 10px;
        }
        .harga-coret {
            text-decoration: line-through;
            color: red;
            margin-right: 10px;
        }
        #pembayaranSection {
            display: none; /* Tersembunyi hingga form dikirim */
            margin-top: 20px;
        }
        #pembayaranSection img {
            width: 100%;
            max-width: 300px;
            margin-bottom: 10px;
        }
        #whatsappButton {
            margin-top: 10px;
            background-color: #25d366; /* Warna khas WhatsApp */
            border: none;
        }
        #whatsappButton:hover {
            background-color: #1ebe57;
        }
        .placeholder {
            color: #aaa;
        }
        .instructions {
            margin-top: 20px;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            background-color: #fafafa;
        }
        .app-info {
            margin-top: 20px;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            background-color: #f9f9f9;
        }
        footer {
            position: fixed;
            bottom: 0;
            width: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            color: white;
            text-align: center;
            padding: 5px;
            font-size: 8px;
            border-top: 1px solid #ddd;
        }
        footer a {
            color: #00C851; /* Warna tautan yang kontras */
            text-decoration: none;
        }
        footer a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>

    <header>
        <h1>Welcome to Paket Siluman</h1>
    </header>

    <div class="container">
        <h2>Pembelian Server Siluman</h2>

        <form id="hwidForm">
            <label for="nama">Nama (tanpa spasi):</label>
            <input type="text" id="nama" name="nama" placeholder="Masukkan username" required>
            <span id="namaError" class="error"></span>

            <label for="kodeHwid">Kode HWID / Device ID:</label>
            <input type="text" id="kodeHwid" name="kodeHwid" placeholder="Masukkan kode HWID / Device ID" required>

            <label for="platform">Pilih Platform:</label>
            <select id="platform" name="platform" required>
                <option value="" disabled selected>Pilih platform</option>
                <option value="android">Android</option>
                <option value="ios">iOS/iPhone</option>
            </select>

            <label for="server">Pilih Server:</label>
            <select id="server" name="server" required>
                <option value="" disabled selected>Pilih server</option>
                <option value="Singapore">Singapore</option>
                <option value="Indonesia">Indonesia</option>
            </select>

            <label for="bulan">Pilih Durasi (bulan):</label>
            <select id="bulan" name="bulan" required>
                <option value="" disabled selected>Pilih durasi bulan</option>
                <option value="1">1 Bulan</option>
                <option value="2">2 Bulan</option>
                <option value="3">3 Bulan</option>
                <option value="4">4 Bulan</option>
                <option value="5">5 Bulan</option>
                <option value="6">6 Bulan (Diskon 10%)</option>
                <option value="7">7 Bulan (Diskon 10%)</option>
                <option value="8">8 Bulan (Diskon 10%)</option>
                <option value="9">9 Bulan (Diskon 10%)</option>
                <option value="10">10 Bulan (Diskon 10%)</option>
                <option value="11">11 Bulan (Diskon 10%)</option>
                <option value="12">12 Bulan (Diskon 17%)</option>
            </select>

            <div class="total">
                Total Harga: <span id="totalHarga"></span>
            </div>

            <button type="submit">Lanjutkan Pembayaran</button>
        </form>

        <!-- Bagian informasi pembayaran -->
        <div id="pembayaranSection">
            <h3>Informasi Pembayaran</h3>
            <p>Scan kode QRIS berikut untuk melakukan pembayaran:</p>
            <img src="https://i.ibb.co.com/ZMv88X6/QRIS-SYIFA-PAYMENT.jpg" alt="QRIS Payment">

            <p>Pilih metode pembayaran lain:</p>
            <label for="bank">Pilih Bank:</label>
            <select id="bank" name="bank">
                <option value="" disabled selected class="placeholder">Pilih bank pembayaran</option>
                <option value="bsi">Bank BSI</option>
                <option value="bankjago">Bank Jago</option>
                <option value="seabank">SeaBank</option>
                <option value="dana">DANA</option>
            </select>

            <p>Nomor Rekening: <span id="rekening"></span></p>

            <p>Tanggal Pembelian: <span id="tanggalPembelian"></span></p>
            <p>Masa Berakhir: <span id="masaBerakhir"></span></p>

            <!-- Tombol Kirim ke WhatsApp -->
            <button id="whatsappButton">Kirim ke WhatsApp</button>
        </div>

        <!-- Penjelasan Cara Pembelian -->
        <div class="instructions">
            <h3>Cara Pembelian</h3>
            <ol>
                <li><strong>Isi Formulir:</strong> Masukkan nama (tanpa spasi), kode HWID, pilih platform, server, dan durasi paket yang diinginkan.</li>
                <li><strong>Klik "Kirim & Beli":</strong> Setelah mengisi formulir, klik tombol "Kirim & Beli" untuk melanjutkan ke halaman pembayaran.</li>
                <li><strong>Informasi Pembayaran:</strong> Di halaman pembayaran, Anda akan melihat kode QRIS untuk pembayaran. Pilih bank jika ingin membayar melalui transfer bank.</li>
                <li><strong>Lakukan Pembayaran:</strong> Scan kode QRIS dengan aplikasi pembayaran Anda atau transfer ke nomor rekening yang tertera.</li>
                <li><strong>Kirim Konfirmasi:</strong> Klik tombol "Kirim ke WhatsApp" untuk mengirim detail pembelian dan konfirmasi pembayaran melalui WhatsApp.</li>
                <li><strong>Konfirmasi:</strong> Setelah pembayaran, Anda akan menerima konfirmasi dan informasi lebih lanjut melalui WhatsApp.</li>
            </ol>
        </div>

        <!-- Informasi Aplikasi -->
        <div class="app-info">
            <h3>Informasi Aplikasi yang Harus Diunduh</h3>
            <p><strong>Untuk Android:</strong> Unduh aplikasi <a href="https://play.google.com/store/apps/details?id=xyz.easypro.httpcustom" target="_blank">HTTP Custom</a> di Google Play Store.</p>
            <p><strong>Untuk iOS/iPhone:</strong> Unduh aplikasi <a href="https://apps.apple.com/id/app/v2box-v2ray-client/id6446814690?l=id" target="_blank">V2Box</a> di App Store.</p>
        </div>
    </div>

    <footer>
        <p>&copy; 2024 Paket Siluman. All rights reserved. | <a href="mailto:info@paketsiluman.com">info@paketsiluman.com</a> | <a href="https://wa.me/6285930313182" target="_blank">WhatsApp: +62 859-3031-3182</a></p>
    </footer>

    <script>
        // Fungsi untuk memeriksa validitas nama
        function isValidUsername(username) {
            return !/\s/.test(username);
        }

        // Fungsi untuk menghitung total harga berdasarkan platform, server, jumlah bulan, dan diskon
        function hitungTotalHarga() {
            let server = document.getElementById('server').value;
            let bulan = document.getElementById('bulan').value;
            let platform = document.getElementById('platform').value;

            let hargaPerBulan = 0;

            if (platform === "android") {
                if (server === "Singapore") {
                    hargaPerBulan = 10000; // Harga per bulan untuk Android di Singapore
                } else if (server === "Indonesia") {
                    hargaPerBulan = 15000; // Harga per bulan untuk Android di Indonesia
                }
            } else if (platform === "ios") {
                if (server === "Singapore") {
                    hargaPerBulan = 15000; // Harga per bulan untuk iOS/iPhone di Singapore
                } else if (server === "Indonesia") {
                    hargaPerBulan = 20000; // Harga per bulan untuk iOS/iPhone di Indonesia
                }
            }

            let hargaSebelumDiskon = hargaPerBulan * bulan;
            let totalHarga = hargaSebelumDiskon;

            // Diskon 10% untuk 6-11 bulan
            if (bulan >= 6 && bulan <= 11) {
                totalHarga *= 0.9; // Diskon 10%
            }

            // Diskon 17% untuk 12 bulan
            if (bulan == 12) {
                totalHarga *= 0.83; // Diskon 17%
            }

            let totalHargaEl = document.getElementById('totalHarga');

            // Jika ada diskon, tampilkan harga dicoret
            if (totalHarga < hargaSebelumDiskon) {
                totalHargaEl.innerHTML = `<span class="harga-coret">Rp ${hargaSebelumDiskon.toLocaleString('id-ID')}</span> Rp ${totalHarga.toLocaleString('id-ID')}`;
            } else {
                totalHargaEl.textContent = `Rp ${totalHarga.toLocaleString('id-ID')}`;
            }

            return totalHarga; // Mengembalikan total harga
        }

        // Fungsi untuk menghitung tanggal berakhir
        function hitungTanggalBerakhir(bulan) {
            let tanggalPembelian = new Date();
            let tanggalBerakhir = new Date();
            tanggalBerakhir.setMonth(tanggalPembelian.getMonth() + parseInt(bulan));

            return {
                tanggalPembelian: tanggalPembelian.toLocaleDateString('id-ID'),
                tanggalBerakhir: tanggalBerakhir.toLocaleDateString('id-ID')
            };
        }

        // Event listener untuk update harga saat platform, server, atau bulan berubah
        document.getElementById('platform').addEventListener('change', hitungTotalHarga);
        document.getElementById('server').addEventListener('change', hitungTotalHarga);
        document.getElementById('bulan').addEventListener('change', function() {
            hitungTotalHarga();
            let bulan = this.value;
            let { tanggalPembelian, tanggalBerakhir } = hitungTanggalBerakhir(bulan);
            document.getElementById('tanggalPembelian').textContent = tanggalPembelian;
            document.getElementById('masaBerakhir').textContent = tanggalBerakhir;
        });

        // Event listener saat tombol form dikirim
        document.getElementById('hwidForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Mencegah form submit secara default

            let nama = document.getElementById('nama').value;
            let kodeHwid = document.getElementById('kodeHwid').value;
            let server = document.getElementById('server').value;
            let bulan = document.getElementById('bulan').value;
            let platform = document.getElementById('platform').value;
            let namaError = document.getElementById('namaError');

            // Validasi username agar tidak ada spasi
            if (!isValidUsername(nama)) {
                namaError.textContent = 'Nama tidak boleh mengandung spasi.';
                return;
            } else {
                namaError.textContent = ''; // Hapus pesan error jika valid
            }

            // Hitung total harga dan tanggal
            hitungTotalHarga();
            let { tanggalPembelian, tanggalBerakhir } = hitungTanggalBerakhir(bulan);
            document.getElementById('tanggalPembelian').textContent = tanggalPembelian;
            document.getElementById('masaBerakhir').textContent = tanggalBerakhir;

            // Tampilkan bagian pembayaran
            document.getElementById('pembayaranSection').style.display = 'block';
        });

        // Event listener untuk menampilkan nomor rekening saat memilih bank
        document.getElementById('bank').addEventListener('change', function() {
            let rekening = '';

            switch (this.value) {
                case 'bsi':
                    rekening = '1059536911';
                    break;
                case 'bankjago':
                    rekening = '106429349064';
                    break;
                case 'seabank':
                    rekening = '901867668250';
                    break;
                case 'dana':
                    rekening = '085260600594';
                    break;
            }

            document.getElementById('rekening').textContent = rekening;
        });

        // Fungsi untuk membuat pesan WhatsApp
        function buatPesanWhatsApp() {
            let nama = document.getElementById('nama').value;
            let kodeHwid = document.getElementById('kodeHwid').value;
            let server = document.getElementById('server').value;
            let bulan = document.getElementById('bulan').value;
            let platform = document.getElementById('platform').value;
            let bank = document.getElementById('bank').value;
            let rekening = document.getElementById('rekening').textContent;
            let totalHarga = hitungTotalHarga();
            let tanggalPembelian = document.getElementById('tanggalPembelian').textContent;
            let tanggalBerakhir = document.getElementById('masaBerakhir').textContent;

            // Format pesan yang akan dikirim ke WhatsApp
            let pesan = `*Pembelian Server*\n\n` +
                        `*Nama:* ${nama}\n` +
                        `*Kode HWID / Device ID:* ${kodeHwid}\n` +
                        `*Platform:* ${platform === "android" ? "Android" : "iOS/iPhone"}\n` +
                        `*Server:* ${server}\n` +
                        `*Durasi:* ${bulan} bulan\n` +
                        `*Total Harga:* Rp ${totalHarga.toLocaleString('id-ID')}\n` +
                        `*Tanggal Pembelian:* ${tanggalPembelian}\n` +
                        `*Masa Berakhir:* ${tanggalBerakhir}\n\n` +
                        `Mohon segera lakukan pembayaran melalui:\n` +
                        `- QRIS (scan kode QR di web), atau\n` +
                        `- ${bank.toUpperCase()} nomor rekening: ${rekening}\n\n` +
                        `Terima kasih!`;

            return pesan;
        }

        // Event listener untuk tombol WhatsApp
        document.getElementById('whatsappButton').addEventListener('click', function() {
            let nomorWhatsApp = '6285930313182'; // Nomor WhatsApp tujuan (format internasional tanpa tanda '+')
            let pesan = buatPesanWhatsApp();
            let url = `https://wa.me/${nomorWhatsApp}?text=${encodeURIComponent(pesan)}`;

            // Buka WhatsApp
            window.open(url, '_blank');
        });

    </script>

</body>
</html>
