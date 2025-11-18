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

## Tugas 9
### 1. Jelaskan mengapa kita perlu membuat model Dart saat mengambil/mengirim data JSON? Apa konsekuensinya jika langsung memetakan `Map<String, dynamic>` tanpa model (terkait validasi tipe, null-safety, maintainability)?
Pentingnya pembuatan model Dart saat mengambil atau mengirim data JSON adalah untuk mengetahui *Type Safety*. Fungsi jsonDecode() sendiri secara default mengembalikan `Map<String, dynamic>`. Hal tersebut menyebabkan Dart tidak tahu apa tipe data dari model tersebut, contohnya price itu int, String, atau double. Melalui pembuatan model, kita segera mendefinisikan data ke tipe yang sudah didefinisikan dari awal. Apabila kita tidak sengaja mengisinya dengan tipe data lain, kompilator akan memberitahu error sebelum aplikasi dijalankan. Selain *Type Safety*, pembuatan model dapat mendefinisikan metode fromJson() untuk menyusun instance objek dari struktur map dan toJson() untuk mengubah instance kembali menjadi map. Hal tersebut membuat strukur kelas yang lebih terorganisir. 

Konsekuensi dari penggunaan langsung `Map<String, dynamic>` tanpa model adalah risiko null-safety dan runtime errors. Hal tersebut bisa terjadi ketika adanya kesalahan dalam mengetik akses data. Kondisi tersebut menyebabkan null saat dijalankan. Selain itu, konsekuensi dari penggunaan langsung adalah hilangnya validasi tipe atau *Type Validation Issues*. Kondisi ini terjadi ketika tipe data baru diketahui saat runtime. Compiler tidak bisa memperingatkan ketika terjadi kesalahan tipe. 

### 2. Apa fungsi package http dan CookieRequest dalam tugas ini? Jelaskan perbedaan peran http vs CookieRequest.
Melalui tugas 9 ini, package http berfungsi sebagai cara sederhana dalam melakukan request HTTP seperti (GET, POST, PUT, DELETE). Selain itu, package http digunakan untuk melakukan tugas jaringan stadnar seperti *fetch data*, mengirim data, atau memperbarui data melalui internet.  Secara default, package ini bersifat stateless. Package ini tidak menyimpan informasi keadaan (state) antar permintaan. Setiap kali memanggil http.get() atau http.post(), hal tersebut dianggap sebagai permintaan baru yang terisolasi tanpa ingatan tentang permintaan sebelumnya. Sedangkan, CookieRequest sendiri merupakan sebuah wrapper (pembungkus) di atas http yang didesain khusus untuk menangani manajemen sesi. Fungsi utamanya adalah untuk menyimpan cookies yang dikirim oleh server Django saat login (contohnya: Session ID). Ketika pengguna melakukan request seperti fetch product, CookieRequest secara otomatis menyertakan cookie sesi tersebut di header request. Tanpa adanya CookieRequest, Django tidak mengetahui siapa user yang sedang melakukan request (anonymous). 

### 3. Jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.
Instance CookieRequest perlu dibagikan ke semua komponen di aplikasi Flutter karena instance tersebut berfungsi sebagai *session manager* yang bersifat stateful. Selain itu, beberapa alasan instance Cookies perlu dibagikan adalah: 
1. State Persistence
Saat pengguna login, server memberikan sebuah session cookie unik yang berisi Session ID ke aplikasi flutter. Instance CookieRequest akan menyimpan session cookie ini secara internal. Aplikasi wajib menyertakan session cookie di dalam header agar server Django mengenali bahwa permintaan tersebut berasal dari pengguna yang sudah terautentikasi. 
2. Single Source of Truth 
Melalui pembagian satu instance CookieRequest menggunakan State Management seperti Provider atau InheritedWidget, dapat dipastikan bahwa semua komponen di aplikasi mengacu pada session state yang sama dan terbaru  
3. Menangani mekanisme LIFO Navigator 
CookieRequest memastikan status logged-in tetap terjaga saat navigasi push atau pop antar halaman.
Walaupun Navigator mengatur halaman dalam bentuk tumpukan (LIFO), session state pengguna harus tetap konsisten di seluruh halaman yang ada di tumpukan tersebut.

### 4. Jelaskan konfigurasi konektivitas yang diperlukan agar Flutter dapat berkomunikasi dengan Django. Mengapa kita perlu menambahkan 10.0.2.2 pada ALLOWED_HOSTS, mengaktifkan CORS dan pengaturan SameSite/cookie, dan menambahkan izin akses internet di Android? Apa yang akan terjadi jika konfigurasi tersebut tidak dilakukan dengan benar?
Konfigurasi konektivitas yang diperlukan adalah pengaturan 10.0.2.2 (Khusus Emulator Android), Aktivasi CORS (Cross-Origin Resource Sharing), pengaturan cookie (SameSite), dan Internet Permission (Android Manifest). Dimulai dari penambahan 10.0.2.2 pada list ALLOWED_HOSTS di file settings.py Django, localhost (127.0.0.1) di dalam emulator Android akan merujuk pada emulator itu sendiri, bukan ke laptop pengguna. Apabila konfigurasi tersebut tidak dijalankan dengan benar, Django secara default akan memblokir request seperti Error: 400 Bad Request: Invalid HTTP_HOST header yang tidak diketahui host-nya demi keamanan. Selanjutnya, terkait dengan aktivasi CORS (Cross-Origin Resource Sharing), konfigurasi yang dilakukan adalah menginstal django-cors-headers di Django, lalu menambahkan domain klien seperti http://localhost:8000 atau IP klien ke CORS_ALLOWED_ORIGINS. Ketika konfigurasi tersebut tidak dijalankan dengan benar, klien akan diblokir dan terjadi Error: Access-Control-Allow-Origin di browser/console Flutter Web atau request gagal secara diam-diam. Konfigurasi selanjutnya adalah pengaturan cookie (SameSite), konfigurasi ini dilakukan dengan cara mengatur parameter cookie di Django settings.py, seperti SESSION_COOKIE_SAMESITE = '...' atau None dan memastikan SESSION_COOKIE_SECURE diatur dengan benar. Apabila konfigurasi tidak berjalan dengan benar, login akan berhasil di Django, tetapi Flutter gagal menyimpan cookie. User dikembalikan ke halaman login saat mencoba mengakses halaman terautentikasi (seperti "My Products"), karena CookieRequest tidak membawa session. Konfigurasi terakhir adalah Internet Permission. Hal yang dilakukan adalah menambahkan tag `<uses-permission android:name="android.permission.INTERNET" />` ke file AndroidManifest.xml (khusus Android). Ketika konfigurasi tidak berjalan dengan benar, aplikasi tidak bisa melakukan request sama sekali dan terjadi Error: SocketException: Failed host lookup atau No address associated with hostname.

### 5. Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.
Mekanisme pengiriman data melibatkan proses synchronous dan asynchronous antara klien dan server.Langkah pertama, data dari input TextFormField divalidasi dan diserialisasi dari objek Dart menjadi JSON menggunakan metode toJson() sebelum dikirimkan secara asynchronous melalui request POST ke server Django. Selanjutnya, server Django menerima, memproses, menyimpan data ke database, dan mengirimkan respons sukses. Kemudian, klien dari sisi Flutter akan melakukan request GET asynchronous untuk mengambil data terbaru yang diterima sebagai JSON. Proses decode menggunakan jsonDecode() dan di-deserialisasi kembali menjadi objek Dart menggunakan metode fromJson() agar dapat ditampilkan di antarmuka pengguna. 

### 6. Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
Mekanisme autentikasi dalam aplikasi Flutter yang terintegrasi dengan Django melibatkan tiga proses utama yang bergantung pada komunikasi asynchronous dan session management. Saat registrasi, pengguna mengirimkan data melalui request POST ke endpoint Django. Server Django menerima, memvalidasi, dan menyimpan username serta password yang sudah di-hash ke database. Kemudian, server akan merespons dengan status sukses. Proses ini bersifat asynchronous agar aplikasi Flutter tidak berhenti saat menunggu respons dari server.

Pada proses login, pengguna mengirimkan username dan password melalui request POST. Server Django memverifikasi kredensial tersebut menggunakan fungsi authenticate() dan memanggil login(request) ketika verifikasi sukses. Django akan membuat Session ID unik dan mengirimkannya kembali ke Flutter sebagai session cookie dalam header respons HTTP. Instance CookieRequest di Flutter yang telah dibagikan secara global ke semua komponen, menangkap dan menyimpan cookie ini. Melalui adanya sesi ini, Flutter dapat menavigasi pengguna ke halaman Menu Utama menggunakan Navigator.pushReplacement() dan semua permintaan berikutnya dapat menyertakan session cookie untuk mengakses data yang terproteksi.

Terakhir, proses logout berjalan ketika Flutter mengirimkan request ke endpoint logout Django, CookieRequest secara otomatis menyertakan session cookie yang aktif. Server Django merespons dengan menghapus Session ID dari database yang membuat session cookie tidak valid. Setelah menerima respons sukses, Flutter membersihkan session cookie lokal pada instance CookieRequest dan melakukan navigasi pushReplacement kembali ke halaman Login. Dengan cookie yang sudah dihapus, status pengguna kembali menjadi anonymous (logged out) dan semua upaya akses berikutnya ke data terautentikasi akan ditolak oleh Django

### 7. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).
1. Persiapan Backend (Deployment & Model)
- Deployment Django dan Endpoint JSON
Memastikan proyek Django berjalan dengan baik di localhost atau di platform deployment. Menambahkan '10.0.2.2' ke ALLOWED_HOSTS di settings.py Django agar emulator Android dapat mengaksesnya. Membuat view di Django yang mengembalikan data semua item (/json/) dan satu view khusus yang mengembalikan data hanya milik pengguna yang sedang login (misalnya /json-by-user/), di mana view ini menggunakan filter(user=request.user). 
- Membuat Model Kustom (Django & Flutter)
Mendefinisikan model Product dengan field yang diperlukan: name, price, description, thumbnail, category, dan is_featured. Kemudian pada flutter membuat Model Dart (ProductEntry) menggunakan quickType dengan field yang sama. Model ini memiliki metode ProductEntry.fromJson() untuk mengonversi respons JSON Django menjadi objek Dart yang aman tipenya (type-safe).

2. Implementasi Autentikasi (Flutter & Django)
- Registrasi Akun dan Halaman Login (Flutter)
Membuat halaman register dan login dengan Form yang berisi TextFormField untuk username dan password. Saat submit, request POST akan berjalan asynchronous ke endpoint registrasi Django. 
- Integrasi Sistem Autentikasi
Menggunakan instance CookieRequest yang dibagikan secara global melalui Provider untuk menangani semua komunikasi setelah registrasi/login. Saat login berhasil, CookieRequest akan secara otomatis menyimpan session cookie yang dikirim oleh Django. Cookie akan secara otomatis disertakan dalam setiap request yang dilakukan oleh CookieRequest selanjutnya sehingga server Django dapat mengenali pengguna yang terautentikasi.

3. Implementasi Halaman Daftar Item dan Detail
- Halaman Daftar Semua Item (ProductEntryListPage)
Di dalam StatefulWidget, buat fungsi asynchronous (async) yang melakukan request GET ke endpoint semua item Django (/json/) menggunakan CookieRequest. Kemudian, deserialisasi respons JSON menjadi List<ProductEntry> menggunakan metode fromJson() yang telah dibuat di Model Dart. Pada tampilan pengguna, FutureBuilder digunakan untuk menangani status asynchronous (loading, error, data). Jika data tersedia, tampilan akan muncul menggunakan ListView.builder. Pada widget item, setiap item list dirender sebagai Card atau ListTile custom sesuai dengan atributnya. 
- Halaman Detail Item (ProductDetailPage)
Di ProductEntryCard, event handler onTap akan memanggil Navigator.push. Saat navigasi, objek ProductEntry yang sudah lengkap dikirim ke halaman detail sebagai constructor. Halaman detail menerima objek tersebut dan merender seluruh atribut pada body halaman. Menambahkan ElevatedButton yang memanggil Navigator.pop(context) untuk kembali ke halaman daftar item sehingga menghilangkan halaman detail dari stack navigasi.

4. Implementasi Filter Item (My Products)
Modifikasi fungsi fetchProduct di ProductEntryListPage agar menerima boolean showOnlyMine. Jika showOnlyMine == false, request dikirim ke endpoint semua item (/json/). Jika showOnlyMine == true, request dikirim ke endpoint item milik pengguna (/json-by-user/). Karena filter sudah dilakukan di view Django (menggunakan Product.objects.filter(user=request.user)), Flutter hanya mengambil data yang sudah difilter dan tidak perlu melakukan filtering tambahan di sisi klien. Pada navigasi, mambahkan ListTile baru di LeftDrawer yang mengarahkan ke ProductEntryListPage(showOnlyMine: true).