<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Paket Siluman - Pembelian</title>
    <style>
        /* Menghilangkan scroll horizontal */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            color: #333;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            overflow-x: hidden; /* Mencegah scroll horizontal */
        }

        header {
            background-color: #4CAF50;
            color: white;
            padding: 10px;
            text-align: center;
            width: 100%;
            box-sizing: border-box;
        }
        
        .container {
            max-width: 500px;
            margin: 0 auto;
            padding: 10px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin-top: 10px;
            flex: 1;
            box-sizing: border-box; /* Memastikan padding di dalam batas */
        }
        
        h1, h2 {
            font-size: 1.2rem;
            margin-bottom: 10px;
            text-align: center;
        }
        
        form {
            max-width: 100%;
            margin: auto;
        }
        
        label {
            display: block;
            margin-top: 10px;
            font-weight: bold;
            font-size: 0.9rem;
        }
        
        input, select, button {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            font-size: 14px;
            border-radius: 4px;
            border: 1px solid #ddd;
            box-sizing: border-box;
        }

        input[readonly] {
            background-color: #e9e9e9; /* Warna latar belakang untuk input non-editable */
            color: #555; /* Warna teks untuk input non-editable */
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

        .button-container {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }

        .button-container button {
            width: 30%; /* Ukuran tombol disesuaikan agar sejajar */
        }

        .error {
            color: red;
            margin-top: 5px;
            font-size: 0.8rem;
        }
        
        .total {
            font-weight: bold;
            margin-top: 10px;
            font-size: 1rem;
        }
        
        .harga-coret {
            text-decoration: line-through;
            color: red;
            margin-right: 10px;
        }
        
        #pembayaranSection, #pembayaranSectionPaket {
            display: none;
            margin-top: 20px;
        }
        
        #pembayaranSection img, #pembayaranSectionPaket img {
            width: 100%;
            max-width: 100%;
            margin-bottom: 10px;
        }
        
        #whatsappButton, #whatsappButtonPaket {
            margin-top: 10px;
            background-color: #25d366;
            border: none;
            padding: 10px;
        }
        
        #whatsappButton:hover, #whatsappButtonPaket:hover {
            background-color: #1ebe57;
        }
        
        .instructions, .app-info {
            margin-top: 20px;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            background-color: #f9f9f9;
            font-size: 0.9rem;
        }

        .app-info img {
            width: 20px;
            height: 20px;
            vertical-align: middle;
            margin-left: 5px; /* Jarak antara teks dan gambar */
        }

        footer {
            background-color: rgba(0, 0, 0, 0.8);
            color: white;
            text-align: center;
            padding: 10px;
            font-size: 12px;
            border-top: 1px solid #ddd;
            position: relative;
            bottom: 0;
            width: 100%;
            box-sizing: border-box;
        }

        footer a {
            color: #00C851;
            text-decoration: none;
        }

        footer a:hover {
            text-decoration: underline;
        }

        /* Modal Styles */
        #modalHWID, #modalHarga, #modalBeli, #modalBeliPaket {
            display: none; 
            position: fixed; 
            z-index: 1; 
            left: 0;
            top: 0;
            width: 100%; 
            height: 100%; 
            overflow: auto; 
            background-color: rgba(0, 0, 0, 0.4); 
        }

        #modalContent, #modalContentHarga, #modalContentBeli, #modalContentBeliPaket {
            background-color: #fff;
            margin: 10% auto;
            padding: 20px;
            border-radius: 8px;
            width: 90%;
            max-width: 600px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        #closeModal, #closeModalHarga, #closeModalBeli, #closeModalBeliPaket {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }

        #closeModal:hover, #closeModal:focus, #closeModalHarga:hover, #closeModalHarga:focus, #closeModalBeli:hover, #closeModalBeli:focus, #closeModalBeliPaket:hover, #closeModalBeliPaket:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }

        .modal-section {
            margin-bottom: 20px;
        }

        .modal-section h2 {
            font-size: 1.3rem;
            margin-bottom: 10px;
        }

        .modal-section p {
            font-size: 1rem;
            margin-bottom: 10px;
        }

        .modal-section ul {
            list-style-type: none;
            padding: 0;
        }

        .modal-section ul li {
            background-color: #f9f9f9;
            margin: 5px 0;
            padding: 10px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .images-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
            gap: 10px;
        }

        .images-container img {
            width: 120px;
            height: auto;
            border: 1px solid #ddd;
            border-radius: 5px;
            box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1);
        }

        @media (min-width: 600px) {
            .container {
                max-width: 500px;
            }
            h1, h2 {
                font-size: 1.5rem;
            }
            input, select, button {
                font-size: 16px;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1>Welcome to Paket Siluman</h1>
    </header>

    <div class="container">
        <h2>Pembelian Server Siluman</h2>
        <p style="font-size: 0.8rem; text-align: center; margin-top: -8px;">Silakan lengkapi informasi di bawah untuk melanjutkan pembelian</p>

        <!-- Form Pembelian Server -->
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

            <!-- Kolom Kartu Perdana (Non-editable) -->
            <label for="kartuPerdana">Kartu Perdana:</label>
            <input type="text" id="kartuPerdana" name="kartuPerdana" value="TELKOMSEL" readonly>

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

            <button id="whatsappButton">Kirim ke WhatsApp</button>
        </div>

        <div class="instructions">
            <h3>Cara Pembelian</h3>
            <ol>
                <li><strong>Isi Formulir:</strong> Masukkan nama (tanpa spasi), kode HWID, pilih platform, server, dan durasi paket yang diinginkan.</li>
                <li><strong>Klik "Lanjutkan Pembayaran":</strong> Setelah mengisi formulir, klik tombol "Lanjutkan Pembayaran" untuk melanjutkan ke halaman pembayaran.</li>
                <li><strong>Informasi Pembayaran:</strong> Di halaman pembayaran, Anda akan melihat kode QRIS untuk pembayaran. Pilih bank jika ingin membayar melalui transfer bank.</li>
                <li><strong>Lakukan Pembayaran:</strong> Scan kode QRIS dengan aplikasi pembayaran Anda atau transfer ke nomor rekening yang tertera.</li>
                <li><strong>Kirim Konfirmasi:</strong> Klik tombol "Kirim ke WhatsApp" untuk mengirim detail pembelian dan konfirmasi pembayaran melalui WhatsApp.</li>
                <li><strong>Konfirmasi:</strong> Setelah pembayaran, Anda akan menerima konfirmasi dan informasi lebih lanjut melalui WhatsApp.</li>
            </ol>
        </div>

        <!-- Tombol Beli Paket Disini -->
        <button id="btnBeliPaketDisini">Beli Paket Disini</button>

        <div class="app-info">
            <h3>Informasi Aplikasi yang Harus Diunduh</h3>
            <p><strong>Untuk Android:</strong> Unduh aplikasi <a href="https://play.google.com/store/apps/details?id=xyz.easypro.httpcustom" target="_blank">HTTP Custom</a><img src="https://i.ibb.co.com/5rYmX78/unnamed.webp" alt=""> di Google Play Store.</p>
            <p><strong>Untuk iOS/iPhone:</strong> Unduh aplikasi <a href="https://apps.apple.com/id/app/v2box-v2ray-client/id6446814690?l=id" target="_blank">V2Box</a><img src="https://i.ibb.co.com/drZ6hB2/unnamed.png" alt=""> di App Store.</p>
        </div>

        <!-- Tombol di bawah halaman -->
        <div class="button-container">
            <button type="button" id="btnHWID">Cara Cek HWID/Device ID</button>
            <button type="button" id="btnBeliPaket">Cara Beli Paket Siluman</button>
            <button type="button" id="btnHargaPaket">Cek Harga Paket Siluman</button>
        </div>
    </div>

    <!-- Modal untuk Cara Cek HWID -->
    <div id="modalHWID">
        <div id="modalContent">
            <span id="closeModal">&times;</span>
            <div class="modal-section">
                <h2>Cara Cek HWID/Device ID</h2>
                <p><strong>Untuk HTTP Custom:</strong> Buka aplikasi, klik <strong>"Garis Tiga"</strong> di pojok kiri atas, scroll ke bawah, klik <strong>"HWID"</strong>, lalu klik <strong>"Salin"</strong>. Tempelkan kode di kolom Kode HWID / Device ID. Seperti pada gambar berikut:</p>
                <div class="images-container">
                    <img src="https://i.ibb.co.com/BPrxnv1/http-1.jpg" alt="Langkah 1 HTTP Custom">
                    <img src="https://i.ibb.co.com/jvdBXZ2/http-2.jpg" alt="Langkah 2 HTTP Custom">
                    <img src="https://i.ibb.co.com/3Md4X4q/http-3.jpg" alt="Langkah 3 HTTP Custom">
                    <img src="https://i.ibb.co.com/54sXQNJ/http-4.jpg" alt="Langkah 4 HTTP Custom">
                </div>
                <br>
       <br>     <br>
                <p><strong>Untuk V2Box:</strong> Buka aplikasi, klik <strong>"Pengaturan/Settings"</strong>, lalu klik <strong>"Tombol Salin"</strong> di samping kodenya. Tempelkan kode di kolom Kode HWID / Device ID. Seperti pada gambar berikut:</p>
                <div class="images-container">
                    <img src="https://i.ibb.co.com/MR0sjW2/v2box-1.jpg" alt="Langkah 1 V2Box">
                    <img src="https://i.ibb.co.com/KVNbVq7/v2box-2.jpg" alt="Langkah 2 V2Box">
                    <img src="https://i.ibb.co.com/NtfSvR6/v2box-3.jpg" alt="Langkah 3 V2Box">
                </div>
            </div>
        </div>
    </div>

    <!-- Modal untuk Cek Harga Paket -->
    <div id="modalHarga">
        <div id="modalContentHarga">
            <span id="closeModalHarga">&times;</span>
            <div class="modal-section">
                <h2>Daftar Harga Paket Siluman</h2>
                <ul>
                    <li>1 GB / 1 Hari: Rp1.100 </li>
                    <li>10 GB / 1 Hari: Rp3.300 </li>
                    <li>5 GB / 3 Hari: Rp3.300 </li>
                    <li>11 GB / 3 Hari: Rp5.500 </li>
                    <li>17 GB / 3 Hari: Rp7.700 </li>
                    <li>11 GB / 7 Hari: Rp9.300 </li>
                    <li>17 GB / 7 Hari: Rp11.500 </li>
                    <li>28 GB / 7 Hari: Rp13.100 </li>
                    <li>11 GB / 30 Hari: Rp25.000 </li>
                    <li>22 GB / 30 Hari: Rp40.000 </li>
                    
                </ul>
                <p><strong>Spesial:</strong> 30 GB / 30 Hari: Rp50.000</p>
                <p><strong>Pembayaran tersedia melalui QRIS atau transfer ke bank pilihan Anda.</strong></p>
               
            </div>
        </div>
    </div>

    <!-- Modal untuk Cara Beli Paket -->
    <div id="modalBeli">
        <div id="modalContentBeli">
            <span id="closeModalBeli">&times;</span>
            <div class="modal-section">
                <h2>Cara Beli Paket Siluman</h2>
                <p><strong>Cara 1: <br>Melalui MyTelkomsel:</strong> <br>Buka aplikasi MyTelkomsel, klik <strong>"Beli Paket"</strong>, geser ke kiri, pilih <strong>"Belajar/Kerja"</strong>, scroll ke bawah di <strong>"Pendidikan"</strong>, klik <strong>Lihat Semua"</strong> dan pilih paket <strong>"Ketengan Ilmupedia"</strong>. Seperti gambar berikut:</p>
                <div class="images-container">
                    <img src="https://i.ibb.co.com/NyS04mm/beli-paket-1.jpg" alt="Langkah 1 MyTelkomsel">
                    <img src="https://i.ibb.co.com/42hqR95/beli-paket-2.jpg" alt="Langkah 2 MyTelkomsel">
                    <img src="https://i.ibb.co.com/WkFgd25/beli-paket-3.jpg" alt="Langkah 3 MyTelkomsel">
                    <img src="https://i.ibb.co.com/BLVmWbD/beli-paket-4.jpg" alt="Langkah 4 MyTelkomsel">
                    <img src="https://i.ibb.co.com/kX8C2Mx/beli-paket-5.jpg" alt="Langkah 5 MyTelkomsel">
                </div>
                <p><strong>Cara 2: <br>Melalui kode *363#:</strong> <br>Ketik <strong>"*363*844#"</strong>, pilih Paket <strong>"3.Ilmupedia"</strong>, lalu beli paket sesuai kebutuhan Anda. Seperti gambar berikut:</p>
                <div class="images-container">
                    <img src="https://i.ibb.co.com/RpjVG62/beli-paket-11.jpg" alt="Langkah 1 Kode USSD">
                    <img src="https://i.ibb.co.com/c8zj8Bc/beli-paket-12.jpg" alt="Langkah 2 Kode USSD">
                    <img src="https://i.ibb.co.com/gdJ0MHF/beli-paket-13.jpg" alt="Langkah 3 Kode USSD">
                </div>
            </div>
        </div>
    </div>

    <!-- Modal untuk Pembelian Paket -->
    <div id="modalBeliPaket">
        <div id="modalContentBeliPaket">
            <span id="closeModalBeliPaket">&times;</span>
            <div class="modal-section">
                <h2>Pembelian Paket Internet</h2>
                <form id="paketForm">
                    <label for="nomorHp">Masukkan Nomor HP:</label>
                    <input type="text" id="nomorHp" name="nomorHp" placeholder="08xxxxxxxxxx" required>

                    <label for="pilihPaket">Pilih Paket:</label>
                    <select id="pilihPaket" name="pilihPaket" required>
                        <option value="" disabled selected>Pilih Paket</option>
                        <option value="1">1 GB / 1 Hari Rp1.100</option>
                        <option value="2">10 GB / 1 Hari Rp3.300</option>
                        <option value="3">5 GB / 3 Hari Rp3.300</option>
                        <option value="4">11 GB / 3 Hari Rp5.500</option>
                        <option value="5">17 GB / 3 Hari Rp7.700</option>
                        <option value="6">11 GB / 7 Hari Rp9.300</option>
                        <option value="7">17 GB / 7 Hari Rp11.500</option>
                        <option value="8">28 GB / 7 Hari Rp13.100</option>
                        <option value="9">11 GB / 30 Hari Rp25.000</option>
                        <option value="10">22 GB / 30 Hari Rp40.000</option>
                        <option value="11">30 GB / 30 Hari Rp50.000</option>
                    </select>

                    <label for="hargaAdmin">Harga Admin:</label>
                    <input type="text" id="hargaAdmin" name="hargaAdmin" readonly>

                    <div class="total">
                        Total Harga: <span id="totalHargaPaket"></span>
                    </div>

                    <button type="submit">Lanjutkan Pembayaran</button>
                </form>

                <!-- Bagian informasi pembayaran paket -->
                <div id="pembayaranSectionPaket">
                    <h3>Informasi Pembayaran</h3>
                    <p>Scan kode QRIS berikut untuk melakukan pembayaran:</p>
                    <img src="https://i.ibb.co.com/ZMv88X6/QRIS-SYIFA-PAYMENT.jpg" alt="QRIS Payment">
                    <p>Pilih metode pembayaran lain:</p>
                    <label for="bankPaket">Pilih Bank:</label>
                    <select id="bankPaket" name="bankPaket">
                        <option value="" disabled selected>Pilih bank pembayaran</option>
                        <option value="bsi">Bank BSI</option>
                        <option value="bankjago">Bank Jago</option>
                        <option value="seabank">SeaBank</option>
                        <option value="dana">DANA</option>
                    </select>

                    <p>Nomor Rekening: <span id="rekeningPaket"></span></p>

                    <button id="whatsappButtonPaket">Kirim ke WhatsApp</button>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2024 Paket Siluman. All rights reserved. <br> <a href="mailto:info@paketsiluman.com">info@paketsiluman.com</a> | <a href="https://wa.me/6285930313182" target="_blank">WhatsApp: +62 859-3031-3182</a></p>
    </footer>

    <script>
        const hargaServer = {
            "android": { "Singapore": 10000, "Indonesia": 15000 },
            "ios": { "Singapore": 15000, "Indonesia": 20000 }
        };

        const paketHargaAdmin = {
            "1": { harga: 1100, admin: 1900 },
            "2": { harga: 3300, admin: 1700 },
            "3": { harga: 3300, admin: 1700 },
            "4": { harga: 5500, admin: 1500 },
            "5": { harga: 7700, admin: 2300 },
            "6": { harga: 9300, admin: 1700 },
            "7": { harga: 11500, admin: 1500 },
            "8": { harga: 13100, admin: 1900 },
            "9": { harga: 25000, admin: 2000 },
            "10": { harga: 40000, admin: 2000 },
            "11": { harga: 50000, admin: 0 },
        };

        const bankRekening = {
            "bsi": "1059536911",
            "bankjago": "106429349064",
            "seabank": "901867668250",
            "dana": "085260600594"
        };

        // Fungsi hitung total harga untuk server
        document.getElementById('platform').addEventListener('change', hitungTotalHarga);
        document.getElementById('server').addEventListener('change', hitungTotalHarga);
        document.getElementById('bulan').addEventListener('change', function () {
            hitungTotalHarga();
            let bulan = this.value;
            let { tanggalPembelian, tanggalBerakhir } = hitungTanggalBerakhir(bulan);
            document.getElementById('tanggalPembelian').textContent = tanggalPembelian;
            document.getElementById('masaBerakhir').textContent = tanggalBerakhir;
        });

        function hitungTotalHarga() {
            let platform = document.getElementById('platform').value;
            let server = document.getElementById('server').value;
            let bulan = parseInt(document.getElementById('bulan').value);
            let hargaPerBulan = hargaServer[platform][server];
            let hargaSebelumDiskon = hargaPerBulan * bulan;
            let totalHarga = hargaSebelumDiskon;

            // Diskon untuk durasi lebih panjang
            if (bulan >= 6 && bulan <= 11) {
                totalHarga *= 0.9;
            } else if (bulan == 12) {
                totalHarga *= 0.83;
            }

            let totalHargaEl = document.getElementById('totalHarga');
            if (totalHarga < hargaSebelumDiskon) {
                totalHargaEl.innerHTML = `<span class="harga-coret">Rp ${hargaSebelumDiskon.toLocaleString('id-ID')}</span> Rp ${totalHarga.toLocaleString('id-ID')}`;
            } else {
                totalHargaEl.textContent = `Rp ${totalHarga.toLocaleString('id-ID')}`;
            }
            return totalHarga;
        }

        function hitungTanggalBerakhir(bulan) {
            let tanggalPembelian = new Date();
            let tanggalBerakhir = new Date();
            tanggalBerakhir.setMonth(tanggalPembelian.getMonth() + parseInt(bulan));
            return {
                tanggalPembelian: tanggalPembelian.toLocaleDateString('id-ID'),
                tanggalBerakhir: tanggalBerakhir.toLocaleDateString('id-ID')
            };
        }

        // Menampilkan nomor rekening sesuai pilihan bank
        document.getElementById('bank').addEventListener('change', function () {
            let rekening = bankRekening[this.value];
            document.getElementById('rekening').textContent = rekening;
        });

        document.getElementById('hwidForm').addEventListener('submit', function (event) {
            event.preventDefault();
            let nama = document.getElementById('nama').value;
            let namaError = document.getElementById('namaError');

            if (!isValidUsername(nama)) {
                namaError.textContent = 'Nama tidak boleh mengandung spasi.';
                return;
            } else {
                namaError.textContent = '';
            }

            hitungTotalHarga();
            document.getElementById('pembayaranSection').style.display = 'block';
        });

        function isValidUsername(username) {
            return !/\s/.test(username);
        }

        document.getElementById('whatsappButton').addEventListener('click', function () {
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

            let pesan = `*Pembelian Server*\n\n` +
                        `*Nama:* ${nama}\n` +
                        `*Kode HWID / Device ID:* ${kodeHwid}\n` +
                        `*Platform:* ${platform}\n` +
                        `*Server:* ${server}\n` +
                        `*Durasi:* ${bulan} bulan\n` +
                        `*Total Harga:* Rp ${totalHarga.toLocaleString('id-ID')}\n` +
                        `*Tanggal Pembelian:* ${tanggalPembelian}\n` +
                        `*Masa Berakhir:* ${tanggalBerakhir}\n\n` +
                        `Mohon segera lakukan pembayaran melalui:\n` +
                        `- QRIS (scan kode QR di web), atau\n` +
                        `- ${bank.toUpperCase()} nomor rekening: ${rekening}\n\n` +
                        `Terima kasih!`;

            const nomorWhatsApp = '6285930313182';
            const url = `https://wa.me/${nomorWhatsApp}?text=${encodeURIComponent(pesan)}`;

            window.open(url, '_blank');
        });

        // Logika untuk pembelian paket
        document.getElementById('pilihPaket').addEventListener('change', function () {
            const selectedPaket = this.value;
            const hargaPaket = paketHargaAdmin[selectedPaket].harga;
            const admin = paketHargaAdmin[selectedPaket].admin;

            document.getElementById('hargaAdmin').value = `Rp${admin.toLocaleString('id-ID')}`;
            document.getElementById('totalHargaPaket').textContent = `Rp${(hargaPaket + admin).toLocaleString('id-ID')}`;
        });

        document.getElementById('paketForm').addEventListener('submit', function (event) {
            event.preventDefault();
            document.getElementById('pembayaranSectionPaket').style.display = 'block';
        });

        document.getElementById('whatsappButtonPaket').addEventListener('click', function () {
            const nomorHp = document.getElementById('nomorHp').value;
            const paket = document.getElementById('pilihPaket').options[document.getElementById('pilihPaket').selectedIndex].text;
            const admin = document.getElementById('hargaAdmin').value;
            const totalHarga = document.getElementById('totalHargaPaket').textContent;

            const pesanPaket = `*Pembelian Paket Internet*\n\n` +
                        `*Nomor HP:* ${nomorHp}\n` +
                        `*Paket:* ${paket}\n` +
                        `*Harga Admin:* ${admin}\n` +
                        `*Total Harga:* ${totalHarga}\n\n` +
                        `Mohon segera lakukan pembayaran.`;

            const nomorWhatsApp = '6285930313182';
            const urlPaket = `https://wa.me/${nomorWhatsApp}?text=${encodeURIComponent(pesanPaket)}`;

            window.open(urlPaket, '_blank');
        });

        // Menampilkan nomor rekening sesuai pilihan bank untuk paket
        document.getElementById('bankPaket').addEventListener('change', function () {
            const selectedBank = this.value;
            const rekening = bankRekening[selectedBank] || 'Nomor rekening tidak tersedia';
            document.getElementById('rekeningPaket').textContent = rekening;
        });

        // Script modal untuk Cara Cek HWID
        var modalHWID = document.getElementById("modalHWID");
        var btnHWID = document.getElementById("btnHWID");
        var closeModal = document.getElementById("closeModal");

        btnHWID.onclick = function() {
            modalHWID.style.display = "block";
        }

        closeModal.onclick = function() {
            modalHWID.style.display = "none";
        }

        window.onclick = function(event) {
            if (event.target == modalHWID) {
                modalHWID.style.display = "none";
            }
        }

        // Script modal untuk Cek Harga Paket
        var modalHarga = document.getElementById("modalHarga");
        var btnHargaPaket = document.getElementById("btnHargaPaket");
        var closeModalHarga = document.getElementById("closeModalHarga");

        btnHargaPaket.onclick = function() {
            modalHarga.style.display = "block";
        }

        closeModalHarga.onclick = function() {
            modalHarga.style.display = "none";
        }

        window.onclick = function(event) {
            if (event.target == modalHarga) {
                modalHarga.style.display = "none";
            }
        }

        // Script modal untuk Cara Beli Paket
        var modalBeli = document.getElementById("modalBeli");
        var btnBeliPaket = document.getElementById("btnBeliPaket");
        var closeModalBeli = document.getElementById("closeModalBeli");

        btnBeliPaket.onclick = function() {
            modalBeli.style.display = "block";
        }

        closeModalBeli.onclick = function() {
            modalBeli.style.display = "none";
        }

        window.onclick = function(event) {
            if (event.target == modalBeli) {
                modalBeli.style.display = "none";
            }
        }

        // Script modal untuk Pembelian Paket
        var modalBeliPaket = document.getElementById("modalBeliPaket");
        var btnBeliPaketDisini = document.getElementById("btnBeliPaketDisini");
        var closeModalBeliPaket = document.getElementById("closeModalBeliPaket");

        btnBeliPaketDisini.onclick = function() {
            modalBeliPaket.style.display = "block";
        }

        closeModalBeliPaket.onclick = function() {
            modalBeliPaket.style.display = "none";
        }

        window.onclick = function(event) {
            if (event.target == modalBeliPaket) {
                modalBeliPaket.style.display = "none";
            }
        }
    </script>

</body>
</html>
