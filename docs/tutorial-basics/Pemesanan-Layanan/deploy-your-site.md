---
sidebar_position: 5
---

# Superkul Truck

Superkul Truck merupakan layanan penglayanan pengiriman Superkul menggunakan truk untuk pengiriman dalam kota maupun luar kota. Saat ini, Superkul truck delivery hanya menjangkau area **JaBoDeTaBek**.

# Jenis Layanan

`serviceName`

- `[superkul_truck];` -->

### Waktu Pengambilan

<p style={{marginLeft: "30px"}}> Waktu pengambilan untuk layanan sameday delivery setidaknya H+ 1 hari dari waktu pemesanan. Jam pengambilan dimulai dari pukul 08:00 - 16:00 dengan jarak waktu per 30 menit (08:00; 08:30; 09:00; 09:30; 10:00; 10:30; dan seterusnya). Waktu pengambilan wajib diisi oleh customer
</p>

```md title=Format
datePick: YYYY-MM-DD
timePick: hh:mm
```
```md title="Contoh" {2-3}
  ---
	"datePick": "2022-12-06",
	"timePick": "02:27",
  ---
```
### Jenis Kendaraan
<p style={{marginLeft: "20px"}}>Jenis kendaraan yang tersedia untuk layanan sameday delivery hanya CDE saja. Jenis kendaraan wajib diisi oleh customer</p>

```md =Vehicle-Type
   "vehicleType": "CDE"
```

### Data Penjemputan

<p style={{marginLeft: "20px"}}>Data penjemputan berisi informasi yang diperlukan untuk melakukan penjemputan. </p>

```json title="Variable"
  "pickUp": [{
		"pickUp": {
		"pickNotes": "",
		"senderName": "Gagah",
		"pickPhoneName": "Gagah",
		"pickPhoneNumber": "6281316009497",
		"pickAddress": "Gilang Seluler, Jalan Kampung Kelapa, Pabuaran, Bogor Regency, West Java, Indonesia",
		"pickLabel": "Gilang Seluler",
		"pickLocation": [106.8043952, -6.4610789],
		"itemTmp": 0
	},
    }]
```
- Label

  `["pickLabel"]`

  Merupakan informasi yang berisi alamat singkat untuk  alamat penjemputan.

- Alamat Penjemputan

  `["pickAddress"]`

  Informasi yang diisi oleh customer agar driver bisa tahu lokasi penjemputan yang ingin dituju.

- Latitude & Longitude

  `["pickLocation"]`

  Titik lokasi yang dapat diperoleh dari proses geocoding.

- Nama Pengirim

  `["senderName"]`

  Nama orang yang bertanggung jawab di lapangan pada saat driver sedang melakukan penjemputan.

- Nomor Handphone

  `["pickPhoneNumber"]`

  Nomor handphone dari orang yang bertanggung jawab di lapangan pada saat driver sedang melakukan penjemputan.

- Catatan

  `["notes"]`

  Catatan merupakan kolom yang dapat diisi oleh customer untuk menyampaikan pesan ke driver yang melakukan penjemputan. Catatan tidak wajib diisi oleh customer (boleh dikosongkan).

- Suhu Paket

  `["itemTmp"]`



### Data Pengantaran

<p style={{marginLeft: "20px"}}>Data pengantaran berisi informasi yang diperlukan untuk melakukan pengantaran paket</p>

```json 
    "dropOff": [{
		"dropNotes": "",
		"receiverName": "IzMie Ij0 LuMuETzz CaHhh HaaLu",
		"dropPhoneName": "IzMie Ij0 LuMuETzz CaHhh HaaLu",
		"dropPhoneNumber": "6289506678342",
		"dropAddress": "Jl. Panjang Arteri Klp. Dua Raya No.8, Kedoya Utara, Kec. Kb. Jeruk, Kota Jakarta Barat, Daerah Khusus Ibukota Jakarta 11520",
		"dropLabel": "Superkul",
		"dropLocation": [106.7623628, -6.1625573]
	}]
```

- Label

  `["dropLabel"]`

  Merupakan informasi yang berisi alamat singkat untuk  alamat pengantaran.

- Alamat Pengantaran

  `["dropAddress"]`

  Informasi yang diisi oleh customer agar driver bisa tahu lokasi penjemputan yang ingin dituju.

- Latitude & Longitude

  `["dropLocation"]`

  Titik lokasi yang dapat diperoleh dari proses geocoding.

- Nama Pengirim

  `["receiverName"]`

  Nama orang yang bertanggung jawab di lapangan pada saat driver sedang melakukan penjemputan.

- Nomor Handphone

  `["dropPhoneNumber"]`

  Nomor handphone dari orang yang bertanggung jawab di lapangan pada saat driver sedang melakukan penjemputan.

- Catatan

  `["notes"]`

  Catatan merupakan kolom yang dapat diisi oleh customer untuk menyampaikan pesan ke driver yang melakukan pengantaran. Catatan tidak wajib diisi oleh customer (boleh dikosongkan).
