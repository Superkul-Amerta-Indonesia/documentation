---
sidebar_position: 2
---

# Sameday Delivery

Sameday delivery merupakan **layanan pengiriman terjadwal** yang dapat mengantarkan lebih dari satu alamat tujuan pengantaran dalam satu pemesanan.

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


## Example Request Body:

```http request
# Header method POST

curl --location 'https://sandbox-api.superkul.id/api/order' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--header 'x-auth-token' \
```

```js

{
    "serviceName": "sameday_delivery",
    "vehicleType": "Bike",
    "datePick": "2022-02-03",
    "timePick": "12:55",
    "optimizeRoute": true,
    "additionalService": [],
    "pickUp": [
        {
            "notes": "Kantor ",
            "senderName": "Ifa",
            "pickLabel": "",
            "pickPhoneName": "",
            "pickPhoneNumber": "0811111",
            "pickAddress": "Mega Plaza",
            "pickLocation": [
               106.6179987244524, -6.2114553365783305
            ],
            "item": [
                {
                    "itemCategory": "Minuman",
                    "weight": 3, 
                    "lenght": 11,
                    "width": 12,
                    "height": 1,
                    "itemTmp": 1,
                    "itemQty": 1,
                    "dropOff": {
                        "dropNotes": "Anggrek",
                        "dropLabel": "",
                        "receiverName": "Indah",
                        "dropPhoneName": "",
                        "dropPhoneNumber": "081111111",
                        "dropAddress": "Mall Taman Anggrek",
                        "dropLocation": [
                           106.85543419022837, -6.229138885971657
                        ]
                    }
                },
                {
                    "itemCategory": "Makanan",
                    "weight": 10,
                    "lenght": 11,
                    "width": 12,
                    "height": 1,
                    "itemTmp": 1,
                    "itemQty": 1,
                    "dropOff": {
                        "dropNotes": "Anggrek",
                        "dropLabel": "",
                        "receiverName": "Indah",
                        "dropPhoneName": "",
                        "dropPhoneNumber": "081111111",
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
                        "dropNotes": "Anggrek",
                        "dropLabel": "",
                        "receiverName": "Indah",
                        "dropPhoneName": "",
                        "dropPhoneNumber": "081111111",
                        "dropAddress": "Mall Taman Anggrek",
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

## Response Example

```json
{
  "message":"ok",
  "status":"success",
  "data":{
    "_id":"63ce0ee5d9b6df34ad011652",
    "serviceName":"Sameday Delivery",
    "orderNumber":"SD-202301231652",
    "datePick":"2022-01-30",
    "timePick":"07:00",
    "vehicleType":"Bike",
    "additionalService":[
      {
        "name":"Handling Fee",
        "price":5000,
        "is_mandatory":1
      }
    ],
    "customerFirstName":"Faisal",
    "customerLastName":"Kusuma",
    "customerPhone":"087780177",
    "customerEmail":"abc@mail.com",
    "promoCode":"USERBARU",
    "promoAmount":100000,
    "orderStatus":"SCHEDULED",
    "priceTrip":438500,
    "priceTotal":338500,
    "subTotal":438500,
    "distanceTotal":121,
    "durationTotal":16121,
    "basicPrice":423500,
    "handlingPrice":15000,
    "totalDestination":2,
    "updated_at":"2023-01-23T04:36:53.180000Z",
    "created_at":"2023-01-23T04:36:53.179000Z",
    "invoiceNumber":"INV-SD-202301231652",
    "trip_planning":[
      {
        "tripNumber":"SD-202301231652-TR0",
        "pick":[
          {
            "pickNotes":"Kantor",
            "senderName":"Ifa",
            "pickPhoneName":null,
            "pickPhoneNumber":"0811111",
            "pickAddress":"Mega Plaza",
            "pickLabel":null,
            "pickLocation":[
              106.6179987244524,
              -6.2114553365783305
            ]
          }
        ],
        "drop":[
          {
            "itemCategory":"Cinta",
            "weight":10,
            "lenght":11,
            "width":12,
            "height":1,
            "itemTmp":1,
            "itemQty":1,
            "dropOff":{
              "dropNotes":"Anggrek",
              "dropLabel":null,
              "receiverName":"Indah",
              "dropPhoneName":null,
              "dropPhoneNumber":"081111111",
              "dropAddress":"Mall Taman Anggrek",
              "dropLocation":[
                106.85543419022837,
                -6.229138885971657
              ]
            }
          },
          {
            "itemCategory":"Cinta",
            "weight":10,
            "lenght":11,
            "width":12,
            "height":1,
            "itemTmp":1,
            "itemQty":1,
            "dropOff":{
              "dropNotes":"Anggrek",
              "dropLabel":null,
              "receiverName":"Indah",
              "dropPhoneName":null,
              "dropPhoneNumber":"081111111",
              "dropAddress":"Mall Taman Anggrek",
              "dropLocation":[
                106.57502079883348,
                -6.109522568622347
              ]
            }
          },
          {
            "itemCategory":"Cinta",
            "weight":10,
            "lenght":11,
            "width":12,
            "height":1,
            "itemTmp":1,
            "itemQty":1,
            "dropOff":{
              "dropNotes":"Anggrek",
              "dropLabel":null,
              "receiverName":"Indah",
              "dropPhoneName":null,
              "dropPhoneNumber":"081111111",
              "dropAddress":"Mall Taman Anggrek",
              "dropLocation":[
                106.78418469307513,
                -6.241519278210899
              ]
            }
          }
        ],
        "distance":121,
        "duration":16121,
        "tripStatus":"Driver Ditemukan",
        "updated_at":"2023-01-23T04:36:53.317000Z",
        "created_at":"2023-01-23T04:36:53.183000Z",
        "driverName":"Alfianto B",
        "driverPhone":"629181911010",
        "driverPhoto":"K7eZ8GBiyM0VV9gnZlr3GTa4Tu0FAjmlpY7P12XS.png",
        "driverVehicleName":"Bike",
        "driverVehicleNumber":"B 1234 CAA"
      }
    ]
  }
}

```