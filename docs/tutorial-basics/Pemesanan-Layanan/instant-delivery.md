---
sidebar_position: 3
---

# Instant Delivery

Instant delivery merupakan layanan pengiriman langsung antar dengan jaminan paket diantar sampai tujuan paling lambat 2 jam.

# Jenis Layanan

`serviceName`


- `[instant_delivery];` -->

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
		"pickPhoneNumber": "0812345468576",
		"pickAddress": "Gilang Seluler, Jalan Kampung Kelapa, Pabuaran, Bogor Regency, West Java, Indonesia",
		"pickLabel": "Gilang Seluler",
		"pickLocation": [106.8043952, -6.4610789],
		"item": [...]
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

`["weight"]`

- Panjang Paket

`["lenght"]`


- Lebar Paket

`["width"]`

- Tinggi Paket

`["height"]`

- Suhu Paket

`["itemTmp"]`

- Kuantitas Paket

`["itemQty"]`


### Data Pengantaran

<p style={{marginLeft: "20px"}}>Data pengantaran berisi informasi yang diperlukan untuk melakukan pengantaran paket</p>

```json
"dropOff": {
				"dropNotes": "Ggh",
				"receiverName": "Ggh",
				"dropPhoneName": "Ggh",
				"dropPhoneNumber": "08751213434546",
				"dropAddress": "Citayam, Bogor Regency, West Java, Indonesia",
				"dropLabel": "Citayam",
				"dropLocation": [106.7500025, -6.442421700000001]
			}
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


## Action

Parameter ini digunakan untuk memberikan aksi pada permintaan yang dikirimkan. Terdapat 2 aksi yang dapat disematkan yaitu ``order`` dan ``check_price``.

 

``order`` digunakan untuk melakukan proses order kedalam sistem.

 

``check_price`` digunakan hanya untuk memeriksa harga dari data yang dimasukan.



##  Example Instant Order:

```http request
# Header method POST

curl --location 'https://sandbox-api.superkul.id/api/order' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'x-auth-token' \
```

```js



{   "action" : "order",

    "externalId": "ORDER-001",

    "serviceName": "instant_delivery",

    "vehicleType": "Bike",

    "datePick": "2022-11-30",

    "timePick": "12:55",

    "optimizeRoute": false,

    "additionalService": [],

    "pickUp": [

        {

            "notes": "Kantor ",

            "senderName": "Ifa",

            "pickLabel": "",

            "pickPhoneName": "",

            "pickPhoneNumber": "62811111",

            "pickAddress": "Mega Plaza",

            "pickLocation": [

               106.6179987244524, -6.2114553365783305

            ],

            "item": [

                {

                    "itemCategory": "Makanan",

                    "weight": 27,

                    "lenght": 11,

                    "width": 12,

                    "height": 1,

                    "itemTmp": 1,

                    "itemQty": 1,

                    "dropOff": {

                        "dropNotes": "Rumah warna biru",

                        "dropLabel": "",

                        "receiverName": "Indah",

                        "dropPhoneName": "",

                        "dropPhoneNumber": "6281111111",

                        "dropAddress": "Jalan Sawo Jakarta Barat",

                        "dropLocation": [

                           106.85543419022837, -6.229138885971657

                        ]

                    }

                }

                

                

                 

            ]

        }

    ]

}

```


## Example Response :

```js


{
    "data": {
        "order": {
            "_id": "6438d213b7bd0bea150cfd32",
            "serviceName": "Instant Delivery",
            "orderNumber": "ID-2023041455fd32",
            "invoiceNumber": "INV-ID-2023041455fd32",
            "datePick": "2022-11-30",
            "timePick": "12:55",
            "vehicleType": "Bike",
            "additionalService": [
                {
                    "name": "Handling Fee",
                    "price": 5000,
                    "is_mandatory": 1
                }
            ],
            "customerFirstName": "Faisal",
            "customerLastName": "Aji",
            "customerPhone": "6282210860366",
            "customerEmail": "faisalkusumaaji123@gmail.com",
            "orderStatus": "SCHEDULED",
            "priceTotal": 161000,
            "distanceTotal": 39,
            "durationTotal": 5125,
            "totalDestination": 1,
            "externalId": "ORDER-001"
        },
        "trip": [
            {
                "_id": "6438d214b7bd0bea150cfd33",
                "tripNumber": "ID-2023041455fd32-TR0",
                "pick": [
                    {
                        "pickNotes": "Kantor",
                        "senderName": "Ifa",
                        "pickPhoneName": "Ifa",
                        "pickPhoneNumber": "62811111",
                        "pickAddress": "Mega Plaza",
                        "pickLabel": null,
                        "pickLocation": [
                            106.6179987244524,
                            -6.2114553365783305
                        ]
                    }
                ],
                "drop": [
                    {
                        "itemCategory": "Makanan",
                        "weight": 27,
                        "lenght": 11,
                        "width": 12,
                        "height": 1,
                        "itemTmp": 1,
                        "itemQty": 1,
                        "dropOff": {
                            "dropNotes": "Rumah warna biru",
                            "dropLabel": null,
                            "receiverName": "Indah",
                            "dropPhoneName": null,
                            "dropPhoneNumber": "6281111111",
                            "dropAddress": "Jalan Sawo Jakarta Barat",
                            "dropLocation": [
                                106.85543419022837,
                                -6.229138885971657
                            ]
                        }
                    }
                ],
                "distance": 39,
                "duration": 5125,
                "tripStatus": "Menunggu Pembayaran"
            }
        ]
    },
    "message": "ok",
    "status": "success"
}

```

```js



{   "action" : "price_check",

    "externalId": "ORDER-001",

    "serviceName": "instant_delivery",

    "vehicleType": "Bike",

    "datePick": "2022-11-30",

    "timePick": "12:55",

    "optimizeRoute": false,

    "additionalService": [],

    "pickUp": [

        {

            "notes": "Kantor ",

            "senderName": "Ifa",

            "pickLabel": "",

            "pickPhoneName": "",

            "pickPhoneNumber": "62811111",

            "pickAddress": "Mega Plaza",

            "pickLocation": [

               106.6179987244524, -6.2114553365783305

            ],

            "item": [

                {

                    "itemCategory": "Makanan",

                    "weight": 27,

                    "lenght": 11,

                    "width": 12,

                    "height": 1,

                    "itemTmp": 1,

                    "itemQty": 1,

                    "dropOff": {

                        "dropNotes": "Rumah warna biru",

                        "dropLabel": "",

                        "receiverName": "Indah",

                        "dropPhoneName": "",

                        "dropPhoneNumber": "6281111111",

                        "dropAddress": "Jalan Sawo Jakarta Barat",

                        "dropLocation": [

                           106.85543419022837, -6.229138885971657

                        ]

                    }

                }

                

                

                 

            ]

        }

    ]

}

```


## Example Response :

```js

{

    "data": {

        "duration": 243,

        "eta": "17:28",

        "distance": 105,

        "priceTotal": 382500,

        "totalDrop": 3

    },

    "message": "ok",

    "status": "success"

}

```