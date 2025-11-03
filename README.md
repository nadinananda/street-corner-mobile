# Street Corner

## Tugas 7 
### 1. Jelaskan apa itu widget tree pada Flutter dan bagaimana hubungan parent-child (induk-anak) bekerja antar widget.
Widget tree pada flutter merupakan sebuah struktur hierarki suatu widget yang disusun untuk menentukan tata letak dan perilaku UI aplikasi. Setiap widget bisa menjadi induk (parent) yang memiliki satu atau beberapa anak (child). Hubungan parent-child bekerja dengan cara widget parent menyediakan kerangka seperti layout/padding untuk widget child lalu widget child akan mengambil kerangka tersebut untuk ditampilkan. Selanjutnya, parent akan memanggil fungsi build() dan menyusun anak-anaknya sebagai bagian dari widget tree. Widget tree bersifat *immutable* yang dimana setelah widget dibuat, widget tersebut tidak dapat diubah.  

Sumber = https://www.f22labs.com/blogs/what-is-flutter-widget-tree-a-comprehensive-guide/

### 2. Sebutkan semua widget yang kamu gunakan dalam proyek ini dan jelaskan fungsinya.
Pada pembuatan tugas 7 ini, widget yang digunakan adalah sebagai berikut: 
1. Class Widget 
- MyApp (lib/main.dart) = root widget yang akan membungkus MaterialApp dan titik awal aplikasi. 
- MyHomePage (lib/menu.dart) = widget yang mendefinisikan seluruh tata letak halaman utama, seperti AppBar dan body. 
- ItemCard (lib/menu.dart) = widget yang dapat menampilkan satu card berwarna di dalam GridView. Satu card berisi icon, text, dan dapat diklik melalui fungsi onTap().

2. Widget bawaan flutter 
- StatelessWidget = tipe widget parent yang menandakan bahwa widget tidak perlu menyimpan state atau datanya tidak berubah. 
- MaterialApp = widget utama yang membungkus aplikasi dengan gaya Material Design. 
- Scaffold = menyediakan kerangka untuk halaman, pada tugas ini kerangka meletakkan AppBar dan body. 
- Column = menyusun widget-widget child secara vertikal (dari atas ke bawah).
- GridView = menampilkan widget-widget dalam sebuah grid yang bisa di-scroll, contohnya di tugas ini menampilkan 3 itemCard dalam satu baris `crossAxisCount: 3`.
- Padding = memberi jarak di sekeliling atau di dalam widget lain.
- Center = memposisikan widget child di tengah-tengah area yang tersedia.
- Container = fungsinya sebagai wadah dan memberikan padding di dalam widget. 

3. Widget untuk UI aplikasi
- AppBar = membuat bar aplikasi di bagian atas layar. 
- Text = menampilkan teks atau tulisan.
- Icon = menampilkan icon yang dibutuhkan, contohnya `Icons.all_inbox_rounded`.
- Material = memberikan tampilakn pada widget, contohnya warna background `item.color` atau membuat lengkungan sudut `borderRadius`.

4. Widget untuk logika input atau fungsi pengguna 
- InkWell = membuat widget child, dalam tugas ini Material di ItemCard dapat diklik melalui onTap().
- ScaffoldMessenger = mengelola dan menampilkan SnackBar di aplikasi. 
- SnackBar = menampilkan pesan singkat sementara ketika button di klik. 

### 3. Apa fungsi dari widget MaterialApp? Jelaskan mengapa widget ini sering digunakan sebagai widget root.
Widget *MaterialApp* berfungsi sebagai wadah utama yang mengatur konfigurasi dasar aplikasi Flutter berbasis *Material Design*. Widget ini dapat membungkus seluruh hierarki widget tree agar bisa mengikuti UI dan fungsionalitas Material Design secara konsisten seperti Scaffold, AppBar, SnackBar, dan lainnya. Widget ini sering digunakan sebagai *widget root* karena widget ini pertama kali dibangun dalam widget tree dan mengatur konfigurasi yang memengaruhi seluruh aplikasi seperti *title*, *ThemeData* untuk pengaturan tema aplikasi, *home*, *routes*, *initialRoute*, serta *BuildContext* utama yang diwariskan ke seluruh widget anak.

Sumber = https://api.flutter.dev/flutter/material/MaterialApp-class.html, https://docs.flutter.dev/ui/widgets/material

### 4. Jelaskan perbedaan antara StatelessWidget dan StatefulWidget. Kapan kamu memilih salah satunya?
*StatelesWidget* adalah widget yang tidak memiliki status dan sepenuhnya ditentukan oleh input yang diterima saat build() dijalankan. Stateless Widget tidak menyimpan atau mengubah state internal. Namun, tampilan dapat ikut berubah oleh peristiwa eksternal pada widget parent. Widget child akan menerima deskripsinya dari widget parent dan tidak akan mengubahnya sendiri.

Sedangkan, *StatefulWidget* merupakan widget yang memiliki state dan mengelola state selama siklusnya. Tampilan widget dapat berubah melalui perubahan state internal melalui setState(). StatefulWidget memiliki 2 kelas yaitu StatefulWidget dan State, siklus hidupnya adalah initState(), build(), setState(), dan dispose().

Pemilihan kedua widget tersebut ditentukan berdasarkan tampilan (UI) aplikasi yang harus berubah atau tidak. *StatelessWidget* cocok digunakan ketika tampilan hanya bergantung pada data yang tidak berubah selama perubahan siklus. Contohnya: halaman yang menampilkan teks, ikon, atau static image. Sedangkan, *StatefulWidget* cocok digunakan ketika tampilan (UI) perlu diperbarui karena adanya perubahan state internal. Contohnya: form input, animasi, counter, dan data yang diperbarui API. 

Sumber = https://api.flutter.dev/flutter/widgets/StatelessWidget-class.html, https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html

### 5. Apa itu BuildContext dan mengapa penting di Flutter? Bagaimana penggunaannya di metode build?
*BuildContext* merupakan objek yang merepresentasikan posisi atau lokasi suatu widget di dalam widget tree. BuildContext sangat penting pada flutter karena widget dapat mengakses informasi yang diwariskan dari widget atasnya, contohnya adalah `Theme.of(context)` untuk tema aplikasi. Penggunaan BuildContext melalui metode build adalah dengan menerima context di build() lalu context tersebut digunakan untuk berinteraksi dengan widget parent di dalam tree, contoh interaksi antar widget tersebut adalah mengambil data dari InheritedWidget, melakukan navigasi menggunakan `Navigator.of(context)`, dan menampilkan komponen UI seperti SnackBar (ScaffoldMessenger.of(context)).

Sumber= https://api.flutter.dev/flutter/widgets/BuildContext-class.html

### 6. Jelaskan konsep "hot reload" di Flutter dan bagaimana bedanya dengan "hot restart".
Konsep *hot reload* adalah memuat perubahan kode ke dalam Virtual Machine (VM) dan membangun ulang widget tree. Konsep tersebut *mempertahankan status aplikasi* dan tidak menjalankan ulang main() atau initState(). Contoh: (⌘\ di Intellij dan Android Studio, ⌃F5 di VSCode)

Sedangkan, konsep *hot restart* adalah memuat perubahan kode ke dalam VM dan memulai ulang aplikasi Flutter. Namun, konsep ini *membuat status aplikasi hilang*. Contoh: (⇧⌘\ di IntelliJ dan Android Studio, ⇧⌘F5 di VSCode)

Sumber = https://docs.flutter.dev/tools/hot-reload, https://docs.flutter.dev/tools/hot-reload#how-it-works

### 7. Jelaskan bagaimana kamu menambahkan navigasi untuk berpindah antar layar di aplikasi Flutter.
Cara menambahkan navigasi untuk berpindah antar layar adalah menggunakan konsep `Navigator`. Konsep navigator digunakan seperti tumpukan (stack) pada layar. Hal pertama yang dilakukan adalah menambahkan `Navigator.push()` di dalam event onPressed/onTap pada sebuah tombol. Fungsi dari `Navigator.push()` adalah untuk menambahkan layar baru. Kemudian layar yang baru ditambahkan akan dibungkus oleh `MaterialPageRoute`. `builder: (context)` akan membangun atau membuat widget dari layar baru. Contoh implementasinya sebagai berikut: 

onTap: () {
    if (item.name == "All Products") {
    Navigator.push(
        context,
        MaterialPageRoute(builder: (context) => AllProductsScreen()),
    );
}}

Selanjutnya, pembuatan layar back atau kembali ke layar sebelumnya menggunakan `Navigator.pop(context)`. `Navigator.pop(context)` akan ditambahkan di dalam fungsi onPressed/onTap. 


