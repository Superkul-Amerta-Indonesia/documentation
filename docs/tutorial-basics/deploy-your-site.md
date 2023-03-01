---
sidebar_position: 5
---

# Superkul Truck

Superkul Truck merupakan layanan penglayanan pengiriman Superkul menggunakan truk untuk pengiriman dalam kota maupun luar kota. Saat ini, Superkul truck delivery hanya menjangkau area **JaBoDeTaBek**.

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

- Suhu Paket

  nama variabel: itemTmp



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
