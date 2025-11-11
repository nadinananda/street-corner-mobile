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

## Tugas 8
### 1. Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement() pada Flutter. Dalam kasus apa sebaiknya masing-masing digunakan pada aplikasi Football Shop kamu?
Perbedaan antara Navigator.push() dan Navigator.pushReplacement() terletak pada apa yang dilakukan kepada route yang berada pada atas stack. Metode push() akan menambah route baru di atas route yang sudah ada pada stack. Sedangkan, pushReplacement() menggantikan route yang sudah ada pada atas stack dengan route baru tersebut. Pada aplikasi Street Corner, Navigator.push() digunakan ketika user ingin kembali ke halaman sebelumnya. Contohnya: User membuka drawer dan mengisi form tambah produk lalu kembali ke halaman utama melalui tombol back. Sedangkan, Navigator.pushReplacement() pada kasus ini digunakan ketika pengguna tidak kembali ke halaman sebelumnya, tetapi ganti ke tampilan halaman baru. Contohnya pada aplikasi Street Corner ini, ketika user membuka drawer lalu klik `Halaman Utama`, maka user akan otomatis direct ke tampilan utama. 

### 2. Bagaimana kamu memanfaatkan hierarchy widget seperti Scaffold, AppBar, dan Drawer untuk membangun struktur halaman yang konsisten di seluruh aplikasi?
Hierarchy widget dimulai dari Scaffold sebagai kerangka utama yang akan membungkus AppBar, Drawer, dan body. Kemudian, AppBar merupakan widget yang akan menjadi header seperti: title dan actions (untuk meletakkan icon). Sedangkan, drawer berfungsi sebagai navigasi terpusat, biasanya terletak di sisi kiri UI aplikasi. Pada contoh aplikasi Street Corner, drawer didefinisikan melalui satu file widgets yang bernama `left_drawer.dart`. Kemudian, widget `LeftDrawer()` diimport di setiap Scaffold yang ada di aplikasi. Contohnya terletak pada file `menu.dart` yaitu `drawer: LeftDrawer(),`.

### 3. Dalam konteks desain antarmuka, apa kelebihan menggunakan layout widget seperti Padding, SingleChildScrollView, dan ListView saat menampilkan elemen-elemen form? Berikan contoh penggunaannya dari aplikasi kamu.
Kelebihan utama dari masing-masing layout widget sebagai berikut: 
1. Padding (widget yang memberikan ruang kosong pada widget child)
Kelebihan: memberikan tampilan form UI yang rapih dan konsisten. Contohnya: pada file `productlist_form.dart`, padding diimplementasikan untuk `TextFormField` sehingga text tidak akan menempel ke tepi layar dan menempel satu sama lain. 
``` dart 
Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Nama Produk",
                    ...
                  )
                  ...
                )
                ...
)
```
2. SingleChildScrollView (widget yang membungkus child Column atau Row agar tampilan dapat di-scroll)
Kelebihan: menangani / menyederhanakan design konten form yang ukurannya panjang dan mencegah kesalahan overflow. 
Contoh implementasi pada aplikasi: 
Pada file `productlist_form.dart`, SingleChildScrollView diimplementasikan melalui body Form. 
``` dart
body: Form(
        key: _formKey,
        child: SingleChildScrollView(
          child: Column(
        ...
          )
        )
)
```
3. ListView (widget untuk menampilkan sejumlah besar item di layar satu per satu dengan membuat layar dapat di-scroll)
Kelebihan: menyederhanakan kode yang lebih ringkas menggunakan ListView dibanding menggunakan SingleChildScrollView() dan Column. 
Contoh: 
Pada file `left_drawer.dart`, ListView diimplementasikan melalui child LeftDrawer. 
```dart
return Drawer(
      child: ListView(
        children: [
          const DrawerHeader(
            decoration: BoxDecoration(
                ...
            )
          )
        ]
      )
)
```

### 4. Bagaimana kamu menyesuaikan warna tema agar aplikasi Football Shop memiliki identitas visual yang konsisten dengan brand toko?
Warna tema yang konsisten dari aplikasi Street Corner telah didefinisikan pada file `main.dart` melalui widget MaterialApp. 
``` dart
theme: ThemeData(
        colorScheme: ColorScheme.fromSwatch(primarySwatch: Colors.blueGrey).copyWith(secondary: Colors.blueGrey[100]),
      ),
```
Kemudian, implementasi widget lainnya seperti AppBar, ElevatedButton, TextFormField dan lainnya akan otomatis mengambil warna dari tema yang ada di file `main.dart` melalui `MaterialStateProperty`. Contohnya sebagai berikut: 
```dart
Align(
                alignment: Alignment.center,
                child: Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: ElevatedButton(
                    style: ButtonStyle(
                      backgroundColor: MaterialStateProperty.all(Colors.blueGrey),
                    ),
                  )
                )
)
```


