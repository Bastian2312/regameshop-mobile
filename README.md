# regameshop-mobile

<details><summary><h2>Tugas 2</h2></summary>

### Membuat sebuah program Flutter baru dengan tema E-Commerce yang sesuai dengan tugas-tugas sebelumnya.
Generate proyek Flutter baru pada terminal dengan nama RegameshopLite
```flutter create RegameshopLite```

Pada RegameshopLite ubah main.dart menjadi berikut

```dart
import 'package:flutter/material.dart';
import 'package:regameshoplite/menu.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        // This is the theme of your application.
        //
        // TRY THIS: Try running your application with "flutter run". You'll see
        // the application has a purple toolbar. Then, without quitting the app,
        // try changing the seedColor in the colorScheme below to Colors.green
        // and then invoke "hot reload" (save your changes or press the "hot
        // reload" button in a Flutter-supported IDE, or press "r" if you used
        // the command line to start the app).
        //
        // Notice that the counter didn't reset back to zero; the application
        // state is not lost during the reload. To reset the state, use hot
        // restart instead.
        //
        // This works for code too, not just values: Most code changes can be
        // tested with just a hot reload.
        colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.deepPurple,
        ).copyWith(secondary: Colors.deepPurple[400]),
        useMaterial3: true,
      ),
      home: MyHomePage(),
    );
  }
}

```

Lalu buatlah file baru bernama menu.dart dan isi dengan kode berikut

```dart
import 'package:flutter/material.dart';

class MyHomePage extends StatelessWidget {
  final String npm = '2306245005'; // NPM
  final String name = 'Bastian Adiputra Siregar'; // Nama
  final String className = 'PBP D'; // Kelas
  MyHomePage({super.key});

  final List<ItemHomepage> items = [
    ItemHomepage("Lihat Produk", Icons.shopping_cart, Colors.red),
    ItemHomepage("Tambah Produk", Icons.add, Colors.green),
    ItemHomepage("Logout", Icons.logout, Colors.blue),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text(
          'RegameshopLite',
          style: TextStyle(
            color: Colors.white,
            fontWeight: FontWeight.bold,
          ),
        ),
        backgroundColor: Theme.of(context).colorScheme.primary,
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                InfoCard(title: 'NPM', content: npm),
                InfoCard(title: 'Name', content: name),
                InfoCard(title: 'Class', content: className),
              ],
            ),
            const SizedBox(height: 16.0),
            Center(
              child: Column(
                children: [
                  const Padding(
                    padding: EdgeInsets.only(top: 16.0),
                    child: Text(
                      'Welcome to RegameshopLite',
                      style: TextStyle(
                        fontWeight: FontWeight.bold,
                        fontSize: 18.0,
                      ),
                    ),
                  ),
                  GridView.count(
                    primary: true,
                    padding: const EdgeInsets.all(20),
                    crossAxisSpacing: 10,
                    mainAxisSpacing: 10,
                    crossAxisCount: 3,
                    shrinkWrap: true,
                    children: items.map((ItemHomepage item) {
                      return ItemCard(item);
                    }).toList(),
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}

class InfoCard extends StatelessWidget {
  final String title;
  final String content;

  const InfoCard({super.key, required this.title, required this.content});

  @override
  Widget build(BuildContext context) {
    return Card(
      elevation: 2.0,
      child: Container(
        width: MediaQuery.of(context).size.width / 3.5,
        padding: const EdgeInsets.all(16.0),
        child: Column(
          children: [
            Text(
              title,
              style: const TextStyle(fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 8.0),
            Text(content),
          ],
        ),
      ),
    );
  }
}

class ItemHomepage {
  final String name;
  final IconData icon;
  final Color color;

  ItemHomepage(this.name, this.icon, this.color);
}

class ItemCard extends StatelessWidget {
  final ItemHomepage item;

  const ItemCard(this.item, {super.key});

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      borderRadius: BorderRadius.circular(12),
      child: InkWell(
        onTap: () {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))
            );
        },
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```

Unutk menjalankan flutter dilokal chrome tulislah code berikut dalam terminal
```
flutter run -d chrome
```

Lalukakn git init dan git remote add origin

### Jelaskan apa yang dimaksud dengan stateless widget dan stateful widget, dan jelaskan perbedaan dari keduanya.

## Stateful Widget
Stateful Widget adalah widget yang memiliki state atau keadaan yang dapat berubah-ubah seiring waktu. Stateful Widget cocok untuk menampilkan elemen UI yang dinamis, yang mungkin berubah berdasarkan interaksi pengguna atau kejadian tertentu dalam aplikasi.

## Stateless Widget
Stateless Widget adalah widget yang tidak memiliki state (keadaan) yang dapat berubah setelah widget tersebut pertama kali dibuat. Stateless Widget bersifat immutable—artinya, setelah widget ini dibuat, nilai dan tampilannya tidak akan berubah.

Secara singkat, gunakan Stateless Widget untuk UI yang tidak berubah, dan Stateful Widget untuk UI yang perlu merespons interaksi atau perubahan data.

### Sebutkan widget apa saja yang kamu gunakan pada proyek ini dan jelaskan fungsinya.

* Scaffold: Menyediakan struktur utama halaman aplikasi, termasuk bar atas, konten body, dan tombol aksi.
* AppBar: Menampilkan bar judul di bagian atas halaman, di sini menampilkan "RegameshopLite."
* Padding: Memberikan ruang di sekitar widget untuk tata letak yang lebih nyaman.
* Column: Menata widget secara vertikal dalam sebuah kolom.
* Row: Menata widget secara horizontal dalam satu baris.
* InfoCard (Widget Kustom): Menampilkan informasi seperti NPM, Nama, dan Kelas dalam sebuah kartu yang diatur.
* Card: Membuat kartu dengan efek bayangan untuk tampilan yang lebih rapi.
* Text: Menampilkan teks seperti judul, nama, atau deskripsi.
* GridView.count: Menyusun widget dalam bentuk grid dengan jumlah kolom yang ditentukan.
* ItemCard (Widget Kustom): Menampilkan ikon dan nama item dalam kartu di grid.
* Material: Memberikan efek desain material pada elemen, seperti warna latar dan efek sentuhan.
* InkWell: Menambahkan efek sentuhan (ripple effect) ketika widget ditekan.
* Icon: Menampilkan ikon dari pustaka ikon Flutter.
* SnackBar: Menampilkan pesan sementara di bagian bawah layar sebagai notifikasi.
* ScaffoldMessenger: Digunakan untuk menampilkan SnackBar atau pesan dalam konteks Scaffold.

### Apa fungsi dari setState()? Jelaskan variabel apa saja yang dapat terdampak dengan fungsi tersebut.

Fungsi setState() digunakan pada widget yang stateful untuk memperbarui tampilan saat ada perubahan data. Ketika setState() dipanggil, Flutter akan menandai bagian tertentu dari widget tree yang perlu dirender ulang, kemudian memperbarui UI sesuai dengan nilai terbaru.

Hanya variabel yang terkait dengan data dinamis dalam sebuah stateful widget yang akan terdampak ketika setState() dipanggil. Variabel ini biasanya dideklarasikan dalam State dari widget tersebut

### Jelaskan perbedaan antara const dengan final.

## fonst
* const digunakan untuk nilai yang tetap konstan pada waktu kompilasi. Ini berarti nilai tersebut harus sudah diketahui dan tetap saat aplikasi dikompilasi.
* const tidak dapat berubah, dan biasanya digunakan untuk objek yang tidak akan pernah berubah.
* Dengan const, Flutter bisa mengoptimalkan kinerja dengan menghindari alokasi ulang objek dalam UI, karena objek-objek ini tidak akan berubah sepanjang waktu.

## final
* final digunakan untuk variabel yang nilainya hanya dapat ditetapkan satu kali, tetapi nilainya mungkin hanya diketahui pada waktu runtime, bukan kompilasi.
* final bisa digunakan untuk objek atau variabel yang nilainya belum tentu diketahui sebelum aplikasi berjalan.
* Meskipun nilainya tidak dapat diubah setelah ditetapkan, final tidak memerlukan nilai yang sudah diketahui pada waktu kompilasi.

</details>
