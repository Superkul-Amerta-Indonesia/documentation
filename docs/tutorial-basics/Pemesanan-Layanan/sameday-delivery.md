---
sidebar_position: 2
---

# Sameday Delivery

Sameday delivery merupakan **layanan pengiriman terjadwal** yang dapat mengantarkan lebih dari satu alamat tujuan pengantaran dalam satu pemesanan.

# Jenis Layanan

`serviceName`

- `[sameday_delivery];`

## Information Host

### Sandbox

- `api-test` https://test-api.superkul.id/api/order

### Production

- `api` https://external.superkul.id/api/order

### Waktu Pengambilan

<p style={{marginLeft: "30px"}}> Waktu pengambilan untuk layanan sameday delivery setidaknya H+ 2 jam dari waktu pemesanan. Jam pengambilan dimulai dari pukul 08:00 - 16:00 dengan jarak waktu per 30 menit (08:00; 08:30; 09:00; 09:30; 10:00; 10:30; dan seterusnya).

Waktu pengambilan wajib diisi oleh customer

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

- Berat Paket,

`["weight"]` (INT)

- Panjang Paket,

`["lenght"]` (INT)

- Lebar Paket,

`["width"]` (INT)

- Tinggi Paket,

`["height"]` (INT)

- Suhu Paket,

`["itemTmp"]` (INT)

- Kuantitas Paket,

`["itemQty"]` (INT)

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

### Pelacakan Pesanan

Untuk melakukan pelacakan pesanan dalam menggunakan cara seperti dibawah ini:

`{orderId}` = ID order yang didapat ketika melakukan pemesanan atau externalId yang dimasukkan ketika membuat pesanan

#### API-TEST

```http request
## Header method GET

curl
--location 'https://external.superkul.id/api/order/{orderId}'
--header 'Accept: application/json'
--header 'Content-Type: application/json'
--header 'x-auth-token'
```

#### API

```http request
## Header method GET

curl
--location 'https://external.superkul.id/api/order/{orderId}'
--header 'Accept: application/json'
--header 'Content-Type: application/json'
--header 'x-auth-token'
```

### Pelacakan Pesanan dengan Document External

Untuk melakukan pelacakan pesanan dalam menggunakan cara seperti dibawah ini:

`{docExternal}` = Nomor Document order yang didapat ketika melakukan pemesanan atau yang dimasukkan ketika membuat pesanan

#### Request

```http request
## Header method GET

curl
--location 'https://external.superkul.id/api/tracking?so_number='
--header 'Accept: application/json'
--header 'Content-Type: application/json'
--header 'x-auth-token'
```

#### Response Description

<table>
  <thead>
    <tr>
      <th scope="col">Field</th>
      <th scope="col">Type</th>
      <th scope="col">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td data-label="Field">tripNumber</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Number of Trip</td>
    </tr>
    <tr>
      <td data-label="Field">soNumber</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Number of External Document</td>
    </tr>
    <tr>
      <td data-label="Field">status</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Status of Trip</td>
    </tr>
    <tr>
      <td data-label="Field">deliveryStatus</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Status of Delivery</td>
    </tr>
    <tr>
      <td data-label="Field">reportTime</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Report time when Item delivered</td>
    </tr>
    <tr>
      <td data-label="Field">locationReport</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Location when Item Delivered</td>
    </tr>
    <tr>
      <td data-label="Field">receiverName</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Receiver of Item</td>
    </tr>
    <tr>
      <td data-label="Field">podPhoto1</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Photo when Item Delivered</td>
    </tr>
    <tr>
      <td data-label="Field">driverName</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Name of Driver</td>
    </tr>
    <tr>
      <td data-label="Field">driverVehicleNumber</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Number of vehicle</td>
    </tr>
    <tr>
      <td data-label="Field">requestTime</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Time of request Endpoint</td>
    </tr>
    <tr>
      <td data-label="Field">temp</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Temperature of Item</td>
    </tr>
    <tr>
      <td data-label="Field">liveTemp</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Live Temperature of Vehicle</td>
    </tr>
    <tr>
      <td data-label="Field">liveTemp</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Live Temperature of Vehicle</td>
    </tr>
    <tr>
      <td data-label="Field">liveLocationDriver</td>
      <td data-label="Type">String</td>
      <td data-label="Description">Live Location of Driver</td>
    </tr>
  </tbody>
</table>

### Pembatalan

Untuk melakukan pembatalan pesanan dalam menggunakan cara seperti dibawah ini:

`{orderId}` = ID order yang didapat ketika melakukan pemesanan atau externalId yang dimasukkan ketika membuat pesanan

#### API-TEST

```http request
## Header method GET

curl
--location 'https://external.superkul.id/api/cancel-order/{orderId}'
--header 'Accept: application/json'
--header 'Content-Type: application/json'
--header 'x-auth-token'
```

#### API

```http request
## Header method GET

curl
--location 'https://external.superkul.id/api/cancel-order/{orderId}'
--header 'Accept: application/json'
--header 'Content-Type: application/json'
--header 'x-auth-token'
```

## Action

Parameter ini digunakan untuk memberikan aksi pada permintaan yang dikirimkan. Terdapat 2 aksi yang dapat disematkan yaitu `order` dan `price_check`.

`order` digunakan untuk melakukan proses order kedalam sistem.

`price_check` digunakan hanya untuk memeriksa harga dari data yang dimasukan.

## Example Sameday Order:

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

    "serviceName": "sameday_delivery",

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

                },

                {

                    "itemCategory": "Minuman",

                    "weight": 10,

                    "lenght": 11,

                    "width": 12,

                    "height": 1,

                    "itemTmp": 1,

                    "itemQty": 1,

                    "dropOff": {

                        "dropNotes": "Rumah warna kuning",

                        "dropLabel": "",

                        "receiverName": "Ardi",

                        "dropPhoneName": "",

                        "dropPhoneNumber": "6281111111",

                        "dropAddress": "Mall Taman Anggrek",

                        "dropLocation": [

                           106.78418469307513, -6.241519278210899

                        ]

                    }

                },

                 {

                    "itemCategory": "Minuman",

                    "weight": 10,

                    "lenght": 11,

                    "width": 12,

                    "height": 1,

                    "itemTmp": 1,

                    "itemQty": 1,

                    "dropOff": {

                        "dropNotes": "Rumah sebelah kanan",

                        "dropLabel": "",

                        "receiverName": "Dini",

                        "dropPhoneName": "",

                        "dropPhoneNumber": "6281111111",

                        "dropAddress": "Jalan Panjang Jakarta Barat",

                        "dropLocation": [

                           106.57502079883348,-6.109522568622347

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

            "_id": "6438b6f757d02e91c90ffa2a",

            "serviceName": "Sameday Delivery",

            "orderNumber": "SD-2023041415fa2a",

            "invoiceNumber": "INV-SD-2023041415fa2a",

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

            "priceTotal": 382500,

            "distanceTotal": 105,

            "durationTotal": 14602,

            "totalDestination": 3,

            "externalId": "ORDER-001"

        },

        "trip": [

            {

                "_id": "6438b6f857d02e91c90ffa2b",

                "tripNumber": "SD-2023041415fa2a-TR0",

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

            },

            {

                "_id": "6438b6f857d02e91c90ffa2e",

                "tripNumber": "SD-2023041415fa2a-TR1",

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

                        "itemCategory": "Minuman",

                        "weight": 10,

                        "lenght": 11,

                        "width": 12,

                        "height": 1,

                        "itemTmp": 1,

                        "itemQty": 1,

                        "dropOff": {

                            "dropNotes": "Rumah warna kuning",

                            "dropLabel": null,

                            "receiverName": "Ardi",

                            "dropPhoneName": null,

                            "dropPhoneNumber": "6281111111",

                            "dropAddress": "Mall Taman Anggrek",

                            "dropLocation": [

                                106.78418469307513,

                                -6.241519278210899

                            ]

                        }

                    },

                    {

                        "itemCategory": "Minuman",

                        "weight": 10,

                        "lenght": 11,

                        "width": 12,

                        "height": 1,

                        "itemTmp": 1,

                        "itemQty": 1,

                        "dropOff": {

                            "dropNotes": "Rumah sebelah kanan",

                            "dropLabel": null,

                            "receiverName": "Dini",

                            "dropPhoneName": null,

                            "dropPhoneNumber": "6281111111",

                            "dropAddress": "Jalan Panjang Jakarta Barat",

                            "dropLocation": [

                                106.57502079883348,

                                -6.109522568622347

                            ]

                        }

                    }

                ],

                "distance": 66,

                "duration": 9477,

                "tripStatus": "Menunggu Pembayaran"

            }

        ]

    },

    "message": "ok",

    "status": "success"

}

```

## Example Sameday Check Price:

```http request
# Header method POST

curl --location 'https://sandbox-api.superkul.id/api/order' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'x-auth-token' \
```

```js



{   "action" : "price_check",

    "externalId": "ORDER-001",

    "serviceName": "sameday_delivery",

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

                },

                {

                    "itemCategory": "Minuman",

                    "weight": 10,

                    "lenght": 11,

                    "width": 12,

                    "height": 1,

                    "itemTmp": 1,

                    "itemQty": 1,

                    "dropOff": {

                        "dropNotes": "Rumah warna kuning",

                        "dropLabel": "",

                        "receiverName": "Ardi",

                        "dropPhoneName": "",

                        "dropPhoneNumber": "6281111111",

                        "dropAddress": "Mall Taman Anggrek",

                        "dropLocation": [

                           106.78418469307513, -6.241519278210899

                        ]

                    }

                },

                 {

                    "itemCategory": "Minuman",

                    "weight": 10,

                    "lenght": 11,

                    "width": 12,

                    "height": 1,

                    "itemTmp": 1,

                    "itemQty": 1,

                    "dropOff": {

                        "dropNotes": "Rumah sebelah kanan",

                        "dropLabel": "",

                        "receiverName": "Dini",

                        "dropPhoneName": "",

                        "dropPhoneNumber": "6281111111",

                        "dropAddress": "Jalan Panjang Jakarta Barat",

                        "dropLocation": [

                           106.57502079883348,-6.109522568622347

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

## Example Driver not Available or Schedule Response:

```js

{
    "message": "driver not available, please try another date and time",
    "status": "other"
}

```

## Example Pelacakan Pesanan Response:

```js

{
    "data": [
        {
            "order": {
                "_id": "641d42fb40f8fcfbc00c08c2",
                "serviceName": "Sameday Delivery",
                "orderNumber": "SD-2023032408c2",
                "invoiceNumber": "INV-SD-2023032408c2",
                "datePick": "2022-02-03",
                "timePick": "12:55",
                "vehicleType": "Bike",
                "additionalService": [
                    {
                        "name": "Handling Fee",
                        "price": 5000,
                        "is_mandatory": 1
                    }
                ],
                "customerFirstName": "Neji",
                "customerLastName": "Yuga",
                "customerPhone": "082213215732",
                "customerEmail": "yuga@gmail.com",
                "orderStatus": "SCHEDULED",
                "priceTotal": 361503,
                "distanceTotal": 93,
                "durationTotal": 12868,
                "totalDestination": 3,
                "externalId": "ORDER-001"
            },
            "trip": {
                "trip 1": [
                    {
                        "_id": "641d42fb40f8fcfbc00c08c3",
                        "tripNumber": "SD-2023032408c2-TR0",
                        "pick": [
                            {
                                "pickNotes": "Kantor",
                                "senderName": "Ifa",
                                "pickPhoneName": null,
                                "pickPhoneNumber": "0811111",
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
                                "itemCategory": "Cinta",
                                "weight": 27,
                                "lenght": 11,
                                "width": 12,
                                "height": 1,
                                "itemTmp": 1,
                                "itemQty": 1,
                                "dropOff": {
                                    "dropNotes": "Anggrek",
                                    "dropLabel": null,
                                    "receiverName": "Indah",
                                    "dropPhoneName": null,
                                    "dropPhoneNumber": "081111111",
                                    "dropAddress": "Mall Taman Anggrek",
                                    "dropLocation": [
                                        106.85543419022837,
                                        -6.229138885971657
                                    ]
                                }
                            }
                        ],
                        "distance": 39,
                        "duration": 5099,
                        "tripStatus": "Mencari Driver"
                    }
                ],
                "trip 2": [
                    {
                        "_id": "641d42fb40f8fcfbc00c08c6",
                        "tripNumber": "SD-2023032408c2-TR1",
                        "pick": [
                            {
                                "pickNotes": "Kantor",
                                "senderName": "Ifa",
                                "pickPhoneName": null,
                                "pickPhoneNumber": "0811111",
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
                                "itemCategory": "Cinta",
                                "weight": 10,
                                "lenght": 11,
                                "width": 12,
                                "height": 1,
                                "itemTmp": 1,
                                "itemQty": 1,
                                "dropOff": {
                                    "dropNotes": "Anggrek",
                                    "dropLabel": null,
                                    "receiverName": "Indah",
                                    "dropPhoneName": null,
                                    "dropPhoneNumber": "081111111",
                                    "dropAddress": "Mall Taman Anggrek",
                                    "dropLocation": [
                                        106.78418469307513,
                                        -6.241519278210899
                                    ]
                                }
                            },
                            {
                                "itemCategory": "Cinta",
                                "weight": 10,
                                "lenght": 11,
                                "width": 12,
                                "height": 1,
                                "itemTmp": 1,
                                "itemQty": 1,
                                "dropOff": {
                                    "dropNotes": "Anggrek",
                                    "dropLabel": null,
                                    "receiverName": "Indah",
                                    "dropPhoneName": null,
                                    "dropPhoneNumber": "081111111",
                                    "dropAddress": "Mall Taman Anggrek",
                                    "dropLocation": [
                                        106.57502079883348,
                                        -6.109522568622347
                                    ]
                                }
                            }
                        ],
                        "distance": 54,
                        "duration": 7769,
                        "tripStatus": "Mencari Driver"
                    }
                ]
            }
        }
    ],
    "message": "ok",
    "status": "success"
}

```
