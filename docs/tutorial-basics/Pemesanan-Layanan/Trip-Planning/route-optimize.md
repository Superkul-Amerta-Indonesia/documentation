---
sidebar_position: 4
---

# Optimize Route

Proses pembuatan trip dari sebuah pesanan pengiriman. Untuk layanan sameday delivery yang bisa memiliki lebih dari satu pengantaran, pengantaran bisa jadi dipecah menjadi lebih dari satu trip apabila ada salah satu kondisi yang mengharuskannya. Beberapa kondisi tersebut adalah: Berat paket melebihi kapasitas maksimal, volume paket melebihi kapasitas maksimal, serta suhu dari paket berbeda satu dengan yang lain.

<p style={{marginLeft: "30px"}}> Route Optimize </p>

<p style={{marginLeft: "30px"}}> Fitur untuk menentukan urutan pengantaran secara otomatis, sehingga jarak dan biaya pengiriman lebih efisien.</p>

# Konfirmasi Order 

Proses pengecekan sebelum sistem melakukan pembuatan invoice order. Dalam proses ini, customer juga dapat memasukkan kode promo jika ada.

serviceName: Nama layanan yang dipesan


orderNumber: Nomor order dari Superkul (unique)


datePick: Tanggal penjemputan


timePick: Jam penjemputan


vehicleType: Jenis kendaraan yang dipesan


additionalService: Layanan tambahan dari Superkul yang ditambahkan/dipilih oleh Customer.


customerFirstName: Nama depan customer Superkul yang membuat pesanan.


customerLastName: Nama belakang customer Superkul yang membuat pesanan.


customerPhone: Nomor hp customer Superkul yang ada pada profil customer.


customerEmail: Email customer Superkul yang ada pada profil customer


promoCode: Kode promo yang customer Superkul input, jika ada.


promoAmount: Nominal potongan dari kode promo yang di pakai customer Superkul.


paymentMethod: Merupakan pembayaran customer Superkul.

Metode pembayaran antara lain:

pre-paid: dimana customer 
harus membayar tagihan pemesanan sebelum pemesanan layanan diproses;

post-paid: dimana customer dapat membayar 
tagihan pemesanan dikemudian hari.


paymentStatus: merupakan status pembayaran dari customer Superkul. Payment Status terdiri dari paid & unpaid.


orderStatus: Merupakan status order dari customer Superkul. Order status terdiri dari waiting for payment,


Scheduled, done, dan cancel.


priceTrip: Merupakan biaya dari semua trip sebelum ditambahkan biaya dari layanan tambahan/additional service.


subTotal: Merupakan total biaya sebelum dipotong discount.


priceTotal: Merupakan total biaya setelah dipotong discount.

distanceTotal: merupakan estimasi total jarak perjalanan dari satu orderan, dalam satuan kilometer.


durationTotal: merupakan estimasi waktu perjalanan dari satu orderan, dalam satuan detik.


totalDestionation: total pengantaran atau drop dalam satu order.


created_at: waktu data order dibuat.


updated_at: waktu data order diupdate.


invoiceNumber: merupakan nomor untuk invoice order dari Superkul.


trip_planning: data perjalanan dari order yang telah dibuat oleh customer.


pick: merupakan semua data penjemputan dari order yang telah dibuat oleh customer.

drop: merupakan semua data pengantaran dari order yang telah dibuat oleh customer.

distance: merupakan jarak yang ditempuh dari satu trip, dalam satuan kilometer.


duration: merupakan waktu yang dibutuhkan untuk menyelesaikan trip tersebut, dalam satuan detik.


tripStatus: merupakan status dari masing-masing trip. Status trip antara lain Menunggu Pembayaran, Mencari 

Driver, Driver Ditemukan, Proses Penjemputan, Proses Pengiriman, Terkirim, Dibatalkan.


driverName: nama Driver Superkul yang menjalankan trip.


driverPhone: nomor hp Driver Superkul yang menjalankan trip.


driverVehicleName: Nama kendaraan (merek) yang dikendarai Driver Superkul yang menjalankan trip.


driverVehicleNumber: Nomor polisi kendaraan yang dikendarai Driver Superkul yang menjalankan trip.


