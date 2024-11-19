# regameshop-mobile

<details><summary><h2>Tugas 7</h2></summary>

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

<details><summary><h2>Tugas 8</h2></summary>

</details>

<details><summary><h2>Tugas 9</h2></summary>

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).

Jalankan perintah pip install django-cors-headers

ambahkan corsheaders ke INSTALLED_APPS pada main project settings.py aplikasi Django kamu.

Tambahkan corsheaders.middleware.CorsMiddleware ke MIDDLEWARE pada main project settings.py aplikasi Django kamu.

Tambahkan beberapa variabel berikut ini pada main project settings.py aplikasi Django kamu.

```CORS_ALLOW_ALL_ORIGINS = True
CORS_ALLOW_CREDENTIALS = True
CSRF_COOKIE_SECURE = True
SESSION_COOKIE_SECURE = True
CSRF_COOKIE_SAMESITE = 'None'
SESSION_COOKIE_SAMESITE = 'None'
```

Buatlah django-app bernama authentication pada project Django yang telah kamu buat sebelumnya.

Tambahkan authentication ke INSTALLED_APPS pada main project settings.py aplikasi Django kamu.

ubah authentication/views,py menjadi berikut

```py
from django.contrib.auth import authenticate, login as auth_login
from django.http import JsonResponse
from django.views.decorators.csrf import csrf_exempt
from django.contrib.auth.models import User
from django.contrib.auth import logout as auth_logout
import json

@csrf_exempt
def login(request):
    username = request.POST['username']
    password = request.POST['password']
    user = authenticate(username=username, password=password)
    if user is not None:
        if user.is_active:
            auth_login(request, user)
            # Status login sukses.
            return JsonResponse({
                "username": user.username,
                "status": True,
                "message": "Login sukses!"
                # Tambahkan data lainnya jika ingin mengirim data ke Flutter.
            }, status=200)
        else:
            return JsonResponse({
                "status": False,
                "message": "Login gagal, akun dinonaktifkan."
            }, status=401)

    else:
        return JsonResponse({
            "status": False,
            "message": "Login gagal, periksa kembali email atau kata sandi."
        }, status=401)

@csrf_exempt
def register(request):
    if request.method == 'POST':
        data = json.loads(request.body)
        username = data['username']
        password1 = data['password1']
        password2 = data['password2']

        # Check if the passwords match
        if password1 != password2:
            return JsonResponse({
                "status": False,
                "message": "Passwords do not match."
            }, status=400)
        
        # Check if the username is already taken
        if User.objects.filter(username=username).exists():
            return JsonResponse({
                "status": False,
                "message": "Username already exists."
            }, status=400)
        
        # Create the new user
        user = User.objects.create_user(username=username, password=password1)
        user.save()
        
        return JsonResponse({
            "username": user.username,
            "status": 'success',
            "message": "User created successfully!"
        }, status=200)
    
    else:
        return JsonResponse({
            "status": False,
            "message": "Invalid request method."
        }, status=400)

@csrf_exempt
def logout(request):
    username = request.user.username

    try:
        auth_logout(request)
        return JsonResponse({
            "username": username,
            "status": True,
            "message": "Logout berhasil!"
        }, status=200)
    except:
        return JsonResponse({
        "status": False,
        "message": "Logout gagal."
        }, status=401)
```
dan route dalam authentication/urls.py

ubah tambah view pada main/views.py
```py
@csrf_exempt
def create_product_flutter(request):
    if request.method == 'POST':

        data = json.loads(request.body)
        new_product = ProductEntry.objects.create(
            user=request.user,
            name=data["name"],
            description=data["description"],
            price=int(data["price"]),
            quantity=int(data["quantity"])
        )

        new_product.save()

        return JsonResponse({"status": "success"}, status=200)
    else:
        return JsonResponse({"status": "error"}, status=401)
```

pada regameshoplite buatlah folder baru 'lib/models' dan tambahkan file product_entry.dart lalu isi dengan kode berikut
```
// To parse this JSON data, do
//
//     final productEntry = productEntryFromJson(jsonString);

import 'dart:convert';

List<ProductEntry> productEntryFromJson(String str) => List<ProductEntry>.from(json.decode(str).map((x) => ProductEntry.fromJson(x)));

String productEntryToJson(List<ProductEntry> data) => json.encode(List<dynamic>.from(data.map((x) => x.toJson())));

class ProductEntry {
    String model;
    String pk;
    Fields fields;

    ProductEntry({
        required this.model,
        required this.pk,
        required this.fields,
    });

    factory ProductEntry.fromJson(Map<String, dynamic> json) => ProductEntry(
        model: json["model"],
        pk: json["pk"],
        fields: Fields.fromJson(json["fields"]),
    );

    Map<String, dynamic> toJson() => {
        "model": model,
        "pk": pk,
        "fields": fields.toJson(),
    };
}

class Fields {
    int user;
    String name;
    String description;
    int price;
    int quantity;

    Fields({
        required this.user,
        required this.name,
        required this.description,
        required this.price,
        required this.quantity,
    });

    factory Fields.fromJson(Map<String, dynamic> json) => Fields(
        user: json["user"],
        name: json["name"],
        description: json["description"],
        price: json["price"],
        quantity: json["quantity"],
    );

    Map<String, dynamic> toJson() => {
        "user": user,
        "name": name,
        "description": description,
        "price": price,
        "quantity": quantity,
    };
}
```

pada screens tambahkan register.dart, login.dart, list_productentry.dart dan detail_productentry.dart dan pada widget tambahkan product_card.dart lalu isi dengan kode berikut
register.dart 
```
import 'dart:convert';
import 'package:flutter/material.dart';
import 'package:regameshoplite/screens/login.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';

class RegisterPage extends StatefulWidget {
  const RegisterPage({super.key});

  @override
  State<RegisterPage> createState() => _RegisterPageState();
}

class _RegisterPageState extends State<RegisterPage> {
  final _usernameController = TextEditingController();
  final _passwordController = TextEditingController();
  final _confirmPasswordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();
    return Scaffold(
      appBar: AppBar(
        title: const Text('Register'),
        leading: IconButton(
          icon: const Icon(Icons.arrow_back),
          onPressed: () {
            Navigator.pop(context);
          },
        ),
      ),
      body: Center(
        child: SingleChildScrollView(
          padding: const EdgeInsets.all(16.0),
          child: Card(
            elevation: 8,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(12.0),
            ),
            child: Padding(
              padding: const EdgeInsets.all(20.0),
              child: Column(
                mainAxisSize: MainAxisSize.min,
                children: <Widget>[
                  const Text(
                    'Register',
                    style: TextStyle(
                      fontSize: 24.0,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  const SizedBox(height: 30.0),
                  TextFormField(
                    controller: _usernameController,
                    decoration: const InputDecoration(
                      labelText: 'Username',
                      hintText: 'Enter your username',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    validator: (value) {
                      if (value == null || value.isEmpty) {
                        return 'Please enter your username';
                      }
                      return null;
                    },
                  ),
                  const SizedBox(height: 12.0),
                  TextFormField(
                    controller: _passwordController,
                    decoration: const InputDecoration(
                      labelText: 'Password',
                      hintText: 'Enter your password',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    obscureText: true,
                    validator: (value) {
                      if (value == null || value.isEmpty) {
                        return 'Please enter your password';
                      }
                      return null;
                    },
                  ),
                  const SizedBox(height: 12.0),
                  TextFormField(
                    controller: _confirmPasswordController,
                    decoration: const InputDecoration(
                      labelText: 'Confirm Password',
                      hintText: 'Confirm your password',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    obscureText: true,
                    validator: (value) {
                      if (value == null || value.isEmpty) {
                        return 'Please confirm your password';
                      }
                      return null;
                    },
                  ),
                  const SizedBox(height: 24.0),
                  ElevatedButton(
                    onPressed: () async {
                      String username = _usernameController.text;
                      String password1 = _passwordController.text;
                      String password2 = _confirmPasswordController.text;

                      // Cek kredensial
                      // TODO: Ganti URL dan jangan lupa tambahkan trailing slash (/) di akhir URL!
                      // Untuk menyambungkan Android emulator dengan Django pada localhost,
                      // gunakan URL http://10.0.2.2/
                      final response = await request.postJson(
                          "http://127.0.0.1:8000/auth/register/",
                          jsonEncode({
                            "username": username,
                            "password1": password1,
                            "password2": password2,
                          }));
                      if (context.mounted) {
                        if (response['status'] == 'success') {
                          ScaffoldMessenger.of(context).showSnackBar(
                            const SnackBar(
                              content: Text('Successfully registered!'),
                            ),
                          );
                          Navigator.pushReplacement(
                            context,
                            MaterialPageRoute(
                                builder: (context) => const LoginPage()),
                          );
                        } else {
                          ScaffoldMessenger.of(context).showSnackBar(
                            const SnackBar(
                              content: Text('Failed to register!'),
                            ),
                          );
                        }
                      }
                    },
                    style: ElevatedButton.styleFrom(
                      foregroundColor: Colors.white,
                      minimumSize: const Size(double.infinity, 50),
                      backgroundColor: Theme.of(context).colorScheme.primary,
                      padding: const EdgeInsets.symmetric(vertical: 16.0),
                    ),
                    child: const Text('Register'),
                  ),
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
}
```

login.dart
```
import 'package:regameshoplite/screens/menu.dart';
import 'package:flutter/material.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';
import 'package:regameshoplite/screens/register.dart';
// TODO: Import halaman RegisterPage jika sudah dibuat

void main() {
  runApp(const LoginApp());
}

class LoginApp extends StatelessWidget {
  const LoginApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Login',
      theme: ThemeData(
        useMaterial3: true,
        colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.deepPurple,
        ).copyWith(secondary: Colors.deepPurple[400]),
      ),
      home: const LoginPage(),
    );
  }
}

class LoginPage extends StatefulWidget {
  const LoginPage({super.key});

  @override
  State<LoginPage> createState() => _LoginPageState();
}

class _LoginPageState extends State<LoginPage> {
  final TextEditingController _usernameController = TextEditingController();
  final TextEditingController _passwordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();

    return Scaffold(
      appBar: AppBar(
        title: const Text('Login'),
      ),
      body: Center(
        child: SingleChildScrollView(
          padding: const EdgeInsets.all(16.0),
          child: Card(
            elevation: 8,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(12.0),
            ),
            child: Padding(
              padding: const EdgeInsets.all(20.0),
              child: Column(
                mainAxisSize: MainAxisSize.min,
                children: [
                  const Text(
                    'Login',
                    style: TextStyle(
                      fontSize: 24.0,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  const SizedBox(height: 30.0),
                  TextField(
                    controller: _usernameController,
                    decoration: const InputDecoration(
                      labelText: 'Username',
                      hintText: 'Enter your username',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                  ),
                  const SizedBox(height: 12.0),
                  TextField(
                    controller: _passwordController,
                    decoration: const InputDecoration(
                      labelText: 'Password',
                      hintText: 'Enter your password',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    obscureText: true,
                  ),
                  const SizedBox(height: 24.0),
                  ElevatedButton(
                    onPressed: () async {
                      String username = _usernameController.text;
                      String password = _passwordController.text;

                      // Cek kredensial
                      // TODO: Ganti URL dan jangan lupa tambahkan trailing slash (/) di akhir URL!
                      // Untuk menyambungkan Android emulator dengan Django pada localhost,
                      // gunakan URL http://10.0.2.2/
                      final response = await request
                          .login("http://127.0.0.1:8000/auth/login/", {
                        'username': username,
                        'password': password,
                      });

                      if (request.loggedIn) {
                        String message = response['message'];
                        String uname = response['username'];
                        if (context.mounted) {
                          Navigator.pushReplacement(
                            context,
                            MaterialPageRoute(
                                builder: (context) => MyHomePage()),
                          );
                          ScaffoldMessenger.of(context)
                            ..hideCurrentSnackBar()
                            ..showSnackBar(
                              SnackBar(
                                  content:
                                      Text("$message Selamat datang, $uname.")),
                            );
                        }
                      } else {
                        if (context.mounted) {
                          showDialog(
                            context: context,
                            builder: (context) => AlertDialog(
                              title: const Text('Login Gagal'),
                              content: Text(response['message']),
                              actions: [
                                TextButton(
                                  child: const Text('OK'),
                                  onPressed: () {
                                    Navigator.pop(context);
                                  },
                                ),
                              ],
                            ),
                          );
                        }
                      }
                    },
                    style: ElevatedButton.styleFrom(
                      foregroundColor: Colors.white,
                      minimumSize: const Size(double.infinity, 50),
                      backgroundColor: Theme.of(context).colorScheme.primary,
                      padding: const EdgeInsets.symmetric(vertical: 16.0),
                    ),
                    child: const Text('Login'),
                  ),
                  const SizedBox(height: 36.0),
                  GestureDetector(
                    onTap: () {
                      Navigator.push(
                        context,
                        MaterialPageRoute(
                            builder: (context) => const RegisterPage()),
                      );
                    },
                    child: Text(
                      'Don\'t have an account? Register',
                      style: TextStyle(
                        color: Theme.of(context).colorScheme.primary,
                        fontSize: 16.0,
                      ),
                    ),
                  ),
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
}
```

list_productentry.dart
```
import 'package:flutter/material.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';
import 'package:regameshoplite/models/product_entry.dart';
import 'package:regameshoplite/screens/detail_productentry.dart';
import 'package:regameshoplite/widgets/left_drawer.dart'; 

class ProductEntryPage extends StatefulWidget {
  const ProductEntryPage({super.key});

  @override
  State<ProductEntryPage> createState() => _ProductEntryPageState();
}

class _ProductEntryPageState extends State<ProductEntryPage> {
  Future<List<ProductEntry>> fetchProduct(CookieRequest request) async {
    final response = await request.get('http://127.0.0.1:8000/json/');
    var data = response;

    List<ProductEntry> listProduct = [];
    for (var d in data) {
      if (d != null) {
        listProduct.add(ProductEntry.fromJson(d));
      }
    }
    return listProduct;
  }

  @override
  Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();
    return Scaffold(
      appBar: AppBar(
        title: const Text('Product Entry List'),
      ),
      drawer: const LeftDrawer(),
      body: FutureBuilder(
        future: fetchProduct(request),
        builder: (context, AsyncSnapshot snapshot) {
          if (snapshot.data == null) {
            return const Center(child: CircularProgressIndicator());
          } else if (!snapshot.hasData) {
            return const Column(
              children: [
                Text(
                  'Belum ada data product pada mental health tracker.',
                  style: TextStyle(fontSize: 20, color: Color(0xff59A5D8)),
                ),
                SizedBox(height: 8),
              ],
            );
          } else {
            return ListView.builder(
              itemCount: snapshot.data!.length,
              itemBuilder: (_, index) {
                var product = snapshot.data![index];
                return GestureDetector(
                  onTap: () {
                    Navigator.push(
                      context,
                      MaterialPageRoute(
                        builder: (context) => ProductDetailPage(product: product),
                      ),
                    );
                  },
                  child: Container(
                    margin: const EdgeInsets.symmetric(horizontal: 16, vertical: 12),
                    padding: const EdgeInsets.all(20.0),
                    decoration: BoxDecoration(
                      border: Border.all(color: Colors.grey),
                      borderRadius: BorderRadius.circular(8.0),
                    ),
                    child: Column(
                      mainAxisAlignment: MainAxisAlignment.start,
                      crossAxisAlignment: CrossAxisAlignment.start,
                      children: [
                        Text(
                          product.fields.name,
                          style: const TextStyle(
                            fontSize: 18.0,
                            fontWeight: FontWeight.bold,
                          ),
                        ),
                        const SizedBox(height: 10),
                        Text(product.fields.description),
                      ],
                    ),
                  ),
                );
              },
            );
          }
        },
      ),
    );
  }
}
```

detail_productentry.dart
```
import 'package:flutter/material.dart';
import 'package:regameshoplite/models/product_entry.dart';

class ProductDetailPage extends StatelessWidget {
  final ProductEntry product;

  const ProductDetailPage({Key? key, required this.product}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(product.fields.name),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text(
              "Name: ${product.fields.name}",
              style: const TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 10),
            Text("Description: ${product.fields.description}"),
            const SizedBox(height: 10),
            Text("Price: \$${product.fields.price}"),
            const SizedBox(height: 10),
            Text("Quantity: ${product.fields.quantity}"),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: () {
                Navigator.pop(context); // Go back to the previous page
              },
              child: const Text('Back to List'),
            ),
          ],
        ),
      ),
    );
  }
}
```

product_card.dart
```
import 'package:flutter/material.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';
import 'package:regameshoplite/screens/list_productentry.dart';
import 'package:regameshoplite/screens/login.dart';
import 'package:regameshoplite/screens/productentry_form.dart';

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
    final request = context.watch<CookieRequest>();
    return Material(
      color: item.color,
      borderRadius: BorderRadius.circular(12),
      child: InkWell(
        onTap: () async {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("Kamu telah menekan tombol ${item.name}!"))
            );
          if (item.name == "Tambah Product") {
            Navigator.push(
              context,
              MaterialPageRoute(
                builder: (context) => const ProductEntryFormPage(),
              ),
            );
          }
          else if (item.name == "Lihat Product") {
            Navigator.push(context,
                MaterialPageRoute(
                    builder: (context) => const ProductEntryPage()
                ),
            );
          }
          else if (item.name == "Logout") {
            final response = await request.logout(
                // TODO: Ganti URL dan jangan lupa tambahkan trailing slash (/) di akhir URL!
                "http://127.0.0.1:8000/auth/logout/");
            String message = response["message"];
            if (context.mounted) {
                if (response['status']) {
                    String uname = response["username"];
                    ScaffoldMessenger.of(context).showSnackBar(SnackBar(
                        content: Text("$message Sampai jumpa, $uname."),
                    ));
                    Navigator.pushReplacement(
                        context,
                        MaterialPageRoute(builder: (context) => const LoginPage()),
                    );
                } else {
                    ScaffoldMessenger.of(context).showSnackBar(
                        SnackBar(
                            content: Text(message),
                        ),
                    );
                }
            }
          }
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

lalu ubah menu.dart, left_drawer.dart dan main.dart seperti berikut

menu.dart
```
import 'package:flutter/material.dart';
import 'package:regameshoplite/widgets/left_drawer.dart';
import 'package:regameshoplite/widgets/product_card.dart';

class MyHomePage extends StatelessWidget {
  final String npm = '2306245005'; // NPM
  final String name = 'Bastian Adiputra Siregar'; // Nama
  final String className = 'PBP D'; // Kelas
  MyHomePage({super.key});

  final List<ItemHomepage> items = [
    ItemHomepage("Lihat Product", Icons.shopping_cart, Colors.red),
    ItemHomepage("Tambah Product", Icons.add, Colors.green),
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
        iconTheme: const IconThemeData(color: Colors.white),
      ),
      drawer: const LeftDrawer(),
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
```

left_drawer.dart
```
import 'package:flutter/material.dart';
import 'package:regameshoplite/screens/list_productentry.dart';
import 'package:regameshoplite/screens/menu.dart';
import 'package:regameshoplite/screens/productentry_form.dart';

class LeftDrawer extends StatelessWidget {
  const LeftDrawer({super.key});

  @override
  Widget build(BuildContext context) {
    return Drawer(
      child: ListView(
        children: [
          DrawerHeader(
            decoration: BoxDecoration(
              color: Theme.of(context).colorScheme.primary,
            ),
            child: const Column(
              children: [
                Text(
                  'Mental Health Tracker',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 24,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                  ),
                ),
                Padding(padding: EdgeInsets.all(8)),
                Text(
                  "Ayo jaga kesehatan mentalmu setiap hari disini!",
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 15,
                    fontWeight: FontWeight.normal,
                    color: Colors.white,
                  ),
                ),
              ],
            ),
          ),
          ListTile(
            leading: const Icon(Icons.home_outlined),
            title: const Text('Halaman Utama'),
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => MyHomePage(),
                  ));
            },
          ),
          ListTile(
            leading: const Icon(Icons.videogame_asset),
            title: const Text('Tambah Product'),
            onTap: () {
              Navigator.pushReplacement(
                context,
                MaterialPageRoute(
                  builder: (context) => const ProductEntryFormPage(),
                ),
              );
            },
          ),
          ListTile(
            leading: const Icon(Icons.add_reaction_rounded),
            title: const Text('Daftar Product'),
            onTap: () {
                // Route menu ke halaman product
                Navigator.push(
                    context,
                    MaterialPageRoute(builder: (context) => const ProductEntryPage()),
                );
            },
          ),
        ],
      ),
    );
  }
}
```

main.dart
```
import 'package:flutter/material.dart';
import 'package:regameshoplite/screens/login.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return Provider(
      create: (_) {
        CookieRequest request = CookieRequest();
        return request;
      },
      child: MaterialApp(
        title: 'Mental Health Tracker',
        theme: ThemeData(
          useMaterial3: true,
          colorScheme: ColorScheme.fromSwatch(
            primarySwatch: Colors.deepPurple,
          ).copyWith(secondary: Colors.deepPurple[400]),
        ),
        home: const LoginPage(),
      ),
    );
  }
}
```

lalu akhiri dengan menjalankan command berikut pada terminal

```
flutter pub add provider
flutter pub add pbp_django_auth
flutter pub add http
```

### Jelaskan mengapa kita perlu membuat model untuk melakukan pengambilan ataupun pengiriman data JSON? Apakah akan terjadi error jika kita tidak membuat model terlebih dahulu?

Model diperlukan untuk merepresentasikan struktur data JSON secara terorganisir dalam aplikasi. Dengan model, kita dapat mengonversi data JSON ke dalam objek Dart sehingga memudahkan manipulasi data, validasi, dan akses atribut secara langsung melalui properti objek.

Jika model tidak dibuat, pengolahan data akan menjadi lebih kompleks karena data harus diakses melalui map atau decoding manual setiap saat. Ini meningkatkan risiko kesalahan, terutama ketika bekerja dengan data JSON yang besar atau kompleks.

Error mungkin tidak terjadi secara langsung, tetapi akan ada kemungkinan besar kesalahan dalam penanganan atribut yang tidak sesuai dengan struktur JSON.

### Jelaskan fungsi dari library http yang sudah kamu implementasikan pada tugas ini

Library http digunakan untuk memfasilitasi komunikasi antara aplikasi Flutter dan server backend. Beberapa fungsi utamanya adalah:

GET: Mengambil data dari server dalam format JSON atau lainnya.
POST: Mengirimkan data ke server, misalnya untuk autentikasi atau pengisian formulir.
Error Handling: Menangani kesalahan seperti koneksi gagal atau respons server tidak valid.
Dalam tugas ini, http digunakan untuk mengambil daftar produk dari server Django dan menampilkannya di aplikasi Flutter.

### Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.

CookieRequest adalah bagian dari library pbp_django_auth yang digunakan untuk melakukan autentikasi berbasis sesi. Fungsi utama CookieRequest:

Menyimpan sesi pengguna secara otomatis menggunakan cookie.
Mempermudah pengiriman permintaan autentikasi seperti login dan logout.
Mengelola status autentikasi sehingga pengguna tidak perlu login ulang selama sesi masih berlaku.
Instance CookieRequest perlu dibagikan ke semua komponen Flutter agar:

Semua widget memiliki akses ke status sesi pengguna.
Data pengguna tetap konsisten di seluruh aplikasi.
Memastikan setiap permintaan ke server menyertakan cookie autentikasi.

### Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.

Berikut adalah mekanisme pengiriman data dari input hingga ditampilkan di Flutter:

Input Data: Data dimasukkan oleh pengguna melalui antarmuka Flutter.
Request ke Server: Flutter menggunakan http atau CookieRequest untuk mengirim data ke Django.
Pengolahan Data di Backend:
Django memproses data input, melakukan validasi, dan menyimpannya di database.
Django mengirimkan respons berupa data JSON kembali ke Flutter.
Dekode Data JSON: Aplikasi Flutter mendekode data JSON dan memetakan data tersebut ke dalam model Dart.
Tampilkan Data: Flutter menampilkan data tersebut melalui widget UI seperti ListView.

### Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.

Pada proses login, pengguna akan memasukkan data seperti email dan password melalui antarmuka Flutter. Data tersebut kemudian dikirimkan ke server Django menggunakan metode HTTP POST. Django akan memvalidasi data dengan mencocokkan email yang dimasukkan dengan akun di database, lalu memeriksa apakah password yang diberikan sesuai dengan hash yang disimpan. Jika validasi berhasil, Django akan mengembalikan respons sukses yang menyertakan cookie sesi untuk menandai pengguna sebagai terautentikasi. Cookie ini disimpan oleh CookieRequest di aplikasi Flutter, memungkinkan pengguna mengakses fitur-fitur tertentu tanpa perlu login ulang. Setelah login berhasil, Flutter akan memperbarui antarmuka pengguna untuk menampilkan opsi logout dan menghilangkan menu login.

Proses registrasi serupa dengan login, tetapi dilakukan untuk membuat akun baru. Pengguna akan memasukkan data pendaftaran seperti nama, email, dan password, yang kemudian dikirimkan ke Django menggunakan metode HTTP POST. Django akan memproses data tersebut dengan melakukan validasi, seperti memastikan email belum terdaftar dan password memenuhi kriteria keamanan tertentu. Jika semua validasi terpenuhi, Django akan membuat akun baru di database dan mengembalikan respons sukses ke Flutter. Setelah registrasi berhasil, aplikasi Flutter akan memberikan pesan keberhasilan kepada pengguna, namun pengguna biasanya diminta untuk login secara terpisah setelah registrasi.

Pada proses logout, pengguna dapat menekan tombol logout yang tersedia di aplikasi. Flutter akan mengirimkan permintaan POST ke server Django untuk menghapus cookie sesi yang terkait dengan pengguna tersebut. Django akan memproses permintaan ini dengan membatalkan sesi pengguna di server, memastikan bahwa cookie yang disimpan tidak lagi valid. Setelah logout berhasil, antarmuka Flutter diperbarui untuk menampilkan kembali menu login dan menyembunyikan fitur-fitur yang hanya dapat diakses oleh pengguna yang telah login.
 </details>
