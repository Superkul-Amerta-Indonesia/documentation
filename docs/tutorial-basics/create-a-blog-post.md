---
sidebar_position: 3
---

# Instant Delivery

Instant delivery merupakan layanan pengiriman langsung antar dengan jaminan paket diantar sampai tujuan paling lambat 2 jam.

### Jenis Kendaraan
<p style={{marginLeft: "20px"}}>Jenis kendaraan yang tersedia untuk layanan sameday delivery hanya motor saja. Jenis kendaraan wajib diisi oleh customer</p>

```md =Vehicle-Type
   "vehicleType": "Bike"
```


### Layanan Tambahan
<p style={{marginLeft: "20px"}}>Layanan Tambahan merupakan layanan yang bersifat opsional yang disediakan oleh Superkul, yang artinya customer tidak harus mengisi layanan tambahan ini.</p>

```md =
   Nama variable: additionalService
```

### Data Penjemputan

<p style={{marginLeft: "20px"}}>Data penjemputan berisi informasi yang diperlukan untuk melakukan penjemputan. </p>

```json title="Variable"
  "pickUp": [{
		"notes": "Rumah warna biru yang pintu nya 2 miliar",
		"senderName": "Faisal Kusuma",
		"pickPhoneName": "Faisal",
		"pickPhoneNumber": "0812345468576",
		"pickAddress": "Gilang Seluler, Jalan Kampung Kelapa, Pabuaran, Bogor Regency, West Java, Indonesia",
		"pickLabel": "Gilang Seluler",
		"pickLocation": [106.8043952, -6.4610789],
		"item": [...]
    }]
```
- Label

  Merupakan informasi untuk menandai data alamat ketika disimpan ke bookmark (bersifat opsional).

- Alamat Penjemputan

  Informasi yang diisi oleh customer agar driver bisa tahu lokasi penjemputan yang ingin dituju.

- Latitude & Longitude

  Titik lokasi yang dapat diperoleh dari proses geocoding.

- Nama Pengirim

  Nama orang yang bertanggung jawab di lapangan pada saat driver sedang melakukan penjemputan.

- Nomor Handphone

  Nomor handphone dari orang yang bertanggung jawab di lapangan pada saat driver sedang melakukan penjemputan.

- Catatan

  Catatan merupakan kolom yang dapat diisi oleh customer untuk menyampaikan pesan ke driver yang melakukan penjemputan. Catatan tidak wajib diisi oleh customer (boleh dikosongkan).



### Data Pengantaran

<p style={{marginLeft: "20px"}}>Data pengantaran berisi informasi yang diperlukan untuk melakukan pengantaran paket</p>

- Label

  Merupakan informasi untuk menandai data alamat ketika disimpan ke bookmark (bersifat opsional).

- Alamat Penjemputan

  Informasi yang diisi oleh customer agar driver bisa tahu lokasi penjemputan yang ingin dituju.

- Latitude & Longitude

  Titik lokasi yang dapat diperoleh dari proses geocoding.

- Nama Pengirim

  Nama orang yang bertanggung jawab di lapangan pada saat driver sedang melakukan penjemputan.

- Nomor Handphone

  Nomor handphone dari orang yang bertanggung jawab di lapangan pada saat driver sedang melakukan penjemputan.

- Catatan

  Catatan merupakan kolom yang dapat diisi oleh customer untuk menyampaikan pesan ke driver yang melakukan penjemputan. Catatan tidak wajib diisi oleh customer (boleh dikosongkan).


### Data Paket

<p style={{marginLeft: "20px"}}>Data paket dibutuhkan untuk mengkategorikan apakah paket dikirim dalam satu armada atau tidak berdasarkan suhu, berat, dan volume.</p>

```json title="Variable"
  "item": [{
			"itemCategory": "Makanan",
			"weight": 10,
			"height": 10,
			"width": 10,
			"lenght": 10,
			"itemTmp": 0,
			"itemQty": 10,
			"dropOff": [...]
      }]
```
- Kategori Paket

nama variabel: itemCategoty
value: makanan; minuman; obat-obatan; Lainnya

- Berat Paket

<p style={{marginLeft: "20px"}}>nama variabel: weight</p>

- Panjang Paket

nama variabel: length
- Lebah Paket

nama variabel: width
- Tinggi Paket

nama variabel: height

- Suhu Paket

nama variabel: itemTmp

- Kuantitas Paket

Saat ini kuantitas paket tidak digunakan, sehingga nilai kunatitas paket selalu satu “1”.
nama variabel: itemQty