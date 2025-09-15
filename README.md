# Laravel Trik Indonesia

<p align='center'>
	<img src="https://img.shields.io/badge/hacktoberfest-2022-blueviolet" alt="Hacktober Badge"/>
  <img src="https://img.shields.io/static/v1?label=%F0%9F%8C%9F&message=If%20Useful&style=style=flat&color=BC4E99" alt="Star Badge"/>
 	<a href="https://github.com/keshavsingh4522" >
		<img src="https://img.shields.io/badge/Contributions-welcome-violet.svg?style=flat&logo=git" alt="Contributions" />
	</a>
</p>

<p align='center'>
  <a href='https://github.com/syofyanzuhad/Laravel-Trik-Indonesia'>
	  <img src='https://visitor-badge.glitch.me/badge?page_id=syofyanzuhad.laravel-trik-indonesia'>
	</a>
	
  <a href='https://github.com/syofyanzuhad/uptime-kita'>
    <img src="https://visitor-badge.laobi.icu/badge?page_id=syofyanzuhad.laravel-trik-indonesia" />
  </a>
	<a href="https://github.com/syofyanzuhad/Laravel-Trik-Indonesia/pulls">
		<img src="https://img.shields.io/github/issues-pr/syofyanzuhad/Laravel-Trik-Indonesia" alt="Pull Requests Badge"/>
	</a>
  <a href="https://github.com/syofyanzuhad/Laravel-Trik-Indonesia/graphs/contributors">
		<img alt="GitHub contributors" src="https://img.shields.io/github/contributors/syofyanzuhad/Laravel-Trik-Indonesia?color=2b9348">
	</a>
  <a href='https://github.com/syofyanzuhad/Laravel-Trik-Indonesia'>
		<img src='https://img.shields.io/github/forks/syofyanzuhad/Laravel-Trik-Indonesia'>
	</a>
  <a href='https://github.com/syofyanzuhad/Laravel-Trik-Indonesia'>
		<img src='https://img.shields.io/github/stars/syofyanzuhad/Laravel-Trik-Indonesia'>
	</a>
</p>

Kumpulan "_trik_" berbahasa indonesia untuk menggunakan framework laravel.
	
- <img src='https://img.shields.io/github/last-commit/syofyanzuhad/laravel-trik-indonesia/main'> 
- _Berisi: **22** trik._

### Kirimkan [`pull request`](https://github.com/syofyanzuhad/Laravel-Trik-Indonesia/contribute) untuk memberikan manfaat lebih banyak !

**Harap perhatikan juga cara untuk berkontribusi [DISINI](/CONTRIBUTING.md) !!**

> _inspired by: [LaravelDaily](https://github.com/LaravelDaily/laravel-tips)_

## Star History

<a href="https://www.star-history.com/#syofyanzuhad/Laravel-Trik-Indonesia&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=syofyanzuhad/Laravel-Trik-Indonesia&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=syofyanzuhad/Laravel-Trik-Indonesia&type=Date" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=syofyanzuhad/Laravel-Trik-Indonesia&type=Date" />
 </picture>
</a>

# Daftar Isi :

- [DB Models dan Eloquent](#db-models-dan-eloquent) (8 trik).
- [Perintah `artisan`](#perintah-artisan) (1 trik).
- [Package](#package) (6 trik).
- [Templating](#templating) (1 trik).
- [Basis Data (Database)](#basis-data-database) (1 trik).
- [Middleware](#middleware)(1 trik).
- [Routing](#routing) (2 trik).
- [Tampilan (View)](#tampilan-view) (1 trik).
- [Lain - lain](#lain-lain) (1 trik).

## DB Models dan Eloquent

⬆️ [Ke Atas](#laravel-trik-indonesia) ➡️ [Berikutnya (Perintah `artisan`)](#perintah-artisan)

- [Cara mengubah format output `created_at` dan `updated_at` lewat model](#cara-mengubah-format-output-created_at-dan-updated_at-lewat-model)

- [Cara Mengubah format text `created_at` dan `updated_at` menjadi `tgl_dibuat` dan `tgl_diupdate` lewat model](#cara-mengubah-format-text-created_at-dan-updated_at-menjadi-tgl_dibuat-dan-tgl_diupdate-lewat-model)

- [Penulisan `where` dengan `whereKolom`](#penulisan-where-dengan-wherekolom)

- [Penulisan `whereIn` dan `whereNotIn`](#penulisan-whereIn-dan-whereNotIn)

- [Cara otomatis mengisi kolom created_at dan updated_at pada tabel pivot](#cara-otomatis-mengisi-kolom-created_at-dan-updated_at-pada-tabel-pivot)

- [Menuliskan query where menggunakan 'LocalQueryScope'](#menuliskan-query-where-menggunakan-localqueryscope)

- [Cara membuat `fillable` di seluruh fieldnya pada model dengan mudah](#cara-membuat-fillable-di-seluruh-fieldnya-pada-model-dengan-mudah)

- [Cara menerapkan select kolom pada table di Eloquent](#cara-menerapkan-select-kolom-pada-table-di-eloquent)


---

### **Cara mengubah format output `created_at` dan `updated_at` lewat model**

_Ditulis oleh: [syofyanzuhad](https://github.com/syofyanzuhad)_

- **created_at**

Untuk mengubah format `created_at`, tambahkan method berikut di dalam model:

```php
public function getCreatedAtFormattedAttribute()
{
    return $this->created_at->format('H:i d, M Y');
}
```
Method ini bisa digunakan dengan cara seperti ini : `$entry->created_at_formatted`.

Dan akan menampilkan hasil seperti ini: `04:19 23, Aug 2020`.

- **updated_at**

Untuk mengubah format `updated_at`, tambahkan method berikut di dalam model:

```php
public function getUpdatedAtFormattedAttribute()
{
    return $this->updated_at->format('H:i d, M Y');
}
```
Method ini bisa digunakan dengan cara seperti ini : `$entry->updated_at_formatted`.

Dan akan menampilkan hasil seperti ini: `04:19 23, Aug 2020`.

### **Cara Mengubah format text created_at dan updated_at menjadi tgl_dibuat dan tgl_diupdate lewat model**

_Ditulis oleh: [aldyrifaldi](https://github.com/aldyrifaldi)_

Caranya sangat mudah 

- **created_at**

Untuk created_at cukup menambahkan :
```php
const CREATED_AT = 'tgl_dibuat';
```
- **updated_at**

dan untuk  updated_at cukup menambahkan:
```php
const UPDATED_AT = 'tgl_diupdate';
```
### **Penulisan where dengan whereKolom**

_Ditulis oleh: [syofyanzuhad](https://github.com/syofyanzuhad)_

- **where**

Misalnya kita punya table `users` dengan kolom `id`, `nama` dan kita mau menampilkan data `users` yang `id`nya 1, biasanya kita menuliskannya seperti ini:
```php
$users = User::where('id', 1)->get();
```
atau kita mau menampilkan data berdasarkan `nama`:
```php
$users = User::where('nama', 'namauser')->get();
```
dan kita juga bisa menampilkan data berdasarkan `id` dan `nama`:
```php
$users = User::where(['id'=> 1, 'nama' => 'namauser'])->get();
```
- **whereKolom**

Sebenarnya kita juga bisa menuliskannya seperti ini:
```php
$users = User::whereId(1)->get();
```
atau:
```php
$users = User::whereNama('namauser')->get();
```
dan:
```php
$users = User::whereIdAndNama(1, 'namauser')->get();
```
### **Penulisan whereIn dan whereNotIn**

_Ditulis oleh: [zulmarij](https://github.com/zulmarij)_

- **whereIn**

Sintaks `whereIn` :
```php
whereIn(Coulumn_name, Array);
```
Contoh Penggunaan `whereIn`
```php
User::whereIn('id', [1, 2, 3])->get();
```
permintaan di atas mencari `id` yang valuenya `1`,`2`,dan `3`.

- **whereNotIn**

Sintaks `whereNotIn` :
```php
whereNotIn(Coulumn_name, Array);
```

Contoh Penggunaan `whereNotIn`
```php
User::whereNotIn('id', [1, 2, 3])->get();
```
permintaan di atas mencari `id` yang valuenya bukan `1`,`2`,dan `3`.

### **Cara otomatis mengisi kolom created_at dan updated_at pada tabel pivot**

_Ditulis oleh: [syofyanzuhad](https://github.com/syofyanzuhad)_

Sebelumnya, jika kita ingin mengisi tabel pivot. Kita bisa menggunakan method `sync()` seperti contoh dibawah ini:
```php
public function store() {
    ...
    $user->roles()->sync([1, 2, 3]);
    ...
}
```
dengan cara diatas, hanya akan mengisi kolom `user_id` dan `role_id` pada tabel `role_user`. Jika kita ingin menggunakan `created_at` dan `updated_at` pada tabel pivotnya yaitu `role_user`, maka kita perlu menambahkan method `->withTimestamps()` pada relasi model `User.php` seperti di bawah ini:
```php
public function role()
{
    return $this->belongsToMany(Role::class)->withTimestamps();
}
```

### **Menuliskan query where menggunakan `LocalQueryScope`**

_Ditulis oleh: [Lucky7Tb](https://github.com/Lucky7Tb)_

Misal anda mempunyai model `User` lalu anda ingin mengambil data user dengan role 'admin' atau 'member'. Kita bisa saja menulis seperti ini

```php
User::where('role', 'admin')->get();

User::where('role', 'member')->get();
```

Dengan QueryScope, penulisan where diatas akan lebih mudah dibaca oleh kita sebagai developer.

Pada model User, tambahkan fungsi seperti ini:

```php
public function scopeIsAdmin($query) {
    return $query->where('role', 'admin');
}

public function scopeIsMember($query) {
    return $query->where('role', 'member');
}
```

Kita membuat fungsi diatas harus dengan prefix (awalan) "scope" lalu sisanya kita beri nama fungsi bebas dengan format sisanya 'PascalCase'

Lalu kita tinggal panggil seperti ini

```php
User::isAdmin()->get();

User::isMember()->get();
```

Perlu diingat untuk pemanggilan fungsinya menggunaka format 'camelCase'.

Atau lebih kerennya kita bisa membuat queryscopenya dinamis.

```php
public function scopeRole($query, $role) {
    return $query->where('role', $role);
}

// Pemanggilan
User::role('admin')->get();

// Atau
User::role('member')->get();
```

### **Cara membuat fillable di seluruh fieldnya pada model dengan mudah**

_Ditulis oleh: [aprian1337](https://github.com/aprian1337)_

Seperti kita tau, jika kita ingin menambahkan data baru menggunakan `create` di eloquent, kita harus mendeklarasikan terlebih dahulu field apa saja yang dapat diisi data pada array `$fillable` di modelnya. Jika kita ingin menambahkan property `fillable` ke model, kita dapat menambahkan field dari table kita ke dalam array fillable di modelnya, seperti berikut:
```php
protected $fillable = [
    'nama', 'email', 'password', 'alamat', 'hobi'
];
```
Sebenarnya tidak ada masalah terhadap kode di atas, namun jika field dari tabelnya banyak dan kita memiliki kebutuhan untuk fieldnya dapat diisi semua, maka kita harus memasukkan seluruh fieldnya ke dalam array `$fillable` dan itu membuat kode menjadi banyak dan tentunya tidak efektif, karena apa? Jika kita menambahkan field baru, kita harus menambahkan field baru tersebut ke dalam array `$fillable` lagi.

Jadi untuk memangkas kode tersebut, kita dapat memanfaatkan fitur `$guarded` pada model. Singkatnya `$guarded` ini memiliki fungsi kebalikan dari `$fillable`, jika `$fillable` adalah list dari field yang dapat diisi data, `$guarded` ini adalah list field yang tidak boleh diisi data. Jadi simplenya kita tinggal menggunakan fitur dari `$guarded` ini lalu mengisinya dengan array kosong, yang artinya kita memberikan akses untuk seluruh masukan data ke dalam field dari model. 
Untuk kodenya seperti di bawah ini :

```php
protected $guarded = [];
```

### **Cara menerapkan select kolom pada table di Eloquent**

_Ditulis oleh: [Muh-Sidik](https://github.com/Muh-Sidik)_

Oke bagaimana cara select dengan eloquent?
Misalnya, kita mempunyai 30 column pada pada 1 table lalu yang kita ingin tampilkan hanya 5 column saja.
Nah, pemborosan sekali jika kita hanya ingin menampilkan 5 column tapi 30 column nya ter-select, maka ini membuat performa database tidak baik malah jenderung membebani, apalagi jika datanya sudah banyak.
Ada caranya nih kalo di Eloquent, contohnya kita hanya ingin memampilkan 2 column dari Model `User`:

Yaitu jika menggunakan fungsi `get()`:
```php
User::get(['name', 'email']);
```
Bisa juga menggunakan fungsi `select()`:
```php
User::select(['name', 'email'])->get();
```

Maka, dua cara diatas hanya akan menampilkan 2 column dari table/model user yaitu colum `name` dan `email`.
Oh ya, cara dengan fungsi `get()` bisa juga diterapkan pada fungsi `all()`
```php
User::all(['name', 'email']);
```

---
## Perintah `artisan`

⬆️ [Ke Atas](#laravel-trik-indonesia) ➡️ [Berikutnya (Package)](#package)

- [Cara membuat model, controller, migration, factory, seeder sekaligus](#cara-membuat-model-controller-migration-factory-seeder-sekaligus)
---

### **Cara membuat model, controller, migration, factory, seeder sekaligus**

_Ditulis oleh: [syofyanzuhad](https://github.com/syofyanzuhad)_

Untuk membuat `model`, `controller`,`migration`, `factory`, dan `seeder` sekaligus cukup jalankan perintah untuk membuat model dengan tambahan `-mcfs`, seperti berikut :

```bash
php artisan make:model User -mcfs
```

Jika kita ingin membuat `controller` dengan resource (default method dari laravel). Gunakan perintah ini (dengan tambahan huruf `r`):
```bash
php artisan make:model User -mcrfs
```

Atau di laravel versi 8 kita bisa menyingkatnya dengan flag `-a` (yang berarti all). Maka kita akan membuat semuanya (`model`, `controller`,`migration`, `factory`, dan `seeder`) sekaligus, dengan perintah yang sangat singkat, seperti di bawah ini :

```bash
php artisan make:model User -a
```

## Package

⬆️ [Ke Atas](#laravel-trik-indonesia) ➡️ [Berikutnya (Templating)](#templating)

- [Install Spatie Role Permission](#install-spatie-role-permission)
- [Cara Menggunakan Role](#cara-menggunakan-role)
- [Cara Menggunakan Permission](#cara-menggunakan-permission)
- [Cara Menggunakan Permission Via Role](#cara-menggunakan-permission-via-role)
- [Cara Menggunakan Spatie di Blade](#cara-menggunakan-spatie-di-blade)
- [Cara Menggunakan Spatie di Middleware](#cara-menggunakan-spatie-di-middleware)
---
### **Install Spatie Role Permission**

_Ditulis oleh: [arifwardan](https://github.com/arifwardan)_

1. Install package

```
composer require spatie/laravel-permission
```
 
2. edit app/config.php
```php
'providers' => [
    // ...
    Spatie\Permission\PermissionServiceProvider::class,
];
```
3. publish migration di terminal

```
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
```

4. clear config & cache

```
php artisan optimize:clear
```
**or**
```
php artisan config:clear
```

5. terakhir jalankan migration

```
php artisan migrate
```

---

### **Cara menggunakan Role**

_Ditulis oleh: [Ridwanhasanah](https://github.com/Ridwanhasanah)_

1. membuat role 
```php
use Spatie\Permission\Models\Role;

$role = Role::create(['name' => 'writer']);
```

2. Menambahkan role kepada user
```php
$user->assignRole($role);
```
3. Menghapus role pada user
```php
$user->revokeRoleTo($role); //$role = nama rolenya apa
```
---

### **Cara Menggunakan Permission**

_Ditulis oleh: [Ridwanhasanah](https://github.com/Ridwanhasanah)_

1. Menambahkan Permission
```php
// Tambah permission ke user
$user->givePermissionTo('edit articles');

// Tambah permission melalui role
$user->assignRole('writer');

$role->givePermissionTo('edit articles');

// Tambahkan role sekaligus
$user->givePermissionTo('edit articles', 'delete articles');

// Tambahkan role sekaligus menggunakan array
$user->givePermissionTo(['edit articles', 'delete articles']);
```

2. Menghapus Permission
```php
// Hapus permissioin dari user
$user->revokePermissionTo('edit articles');

// Hapus dan tamabah sekaligus (update)
$user->syncPermissions(['edit articles', 'delete articles']);
```

3. Mengecek Apakah User Mempunyai Permissioin
```php
$user->hasPermissionTo('edit articles');

// Cek use mengguakan id
$user->hasPermissionTo('1');
$user->hasPermissionTo(Permission::find(1)->id);
$user->hasPermissionTo($somePermission->id);

// Periksa user yang mempunya beberapa permission
$user->hasAnyPermission(['edit articles', 'publish articles', 'unpublish articles']);

// alterntif lain
$user->hasAllPermissions(['edit articles', 'publish articles', 'unpublish articles']);

// Periksa user yang mempunya beberapa permission menggunakan integer
$user->hasAnyPermission(['edit articles', 1, 5]);
```

---

### **Cara Menggunakan Permission Via Role**

_Ditulis oleh: [Ridwanhasanah](https://github.com/Ridwanhasanah)_

1. Menerapkan Role ke User manapun
```php
$user->assignRole('writer');

// Memberikan role lebih dari satu
$user->assignRole('writer', 'admin');
// alternatif lain menggunakan array
$user->assignRole(['writer', 'admin']);
```
2. Menghapus Role dari User
```php
$user->removeRole('writer');
```
3. Update Role dari User
```php
// Semua role saat ini akan di hapus dari use dan di gantikan dari array yang di berikan
$user->syncRoles(['writer', 'admin']);
```
4. Memeriksa User mempunyai Role, biasanya di gunakan untuk validasi
```php
// Semua role saat ini akan di hapus dari use dan di gantikan dari array yang di berikan
$user->syncRoles(['writer', 'admin']);

// Memeriksa user yang mempunyai beberapa role
$user->hasAnyRole(['writer', 'reader']);
// atau
$user->hasAnyRole('writer', 'reader');

// Cek jika user punya semua role
$user->hasAllRoles(Role::all());
```
---
### **Cara Menggunakan Spatie di Blade**

_Ditulis oleh: [Ridwanhasanah](https://github.com/Ridwanhasanah)_

1. Permission pada Blade
```php
@can('edit articles')
    //
@endcan
// atau

@if(auth()->user()->can('edit articles') && $some_other_condition)
    //
@endif
// Bisa juga menggunakan @can, @cannot, @canany, dan @guest
```
2. Role pada Blade
```php
// Persiksa sebuah role
@role('writer')
    Saya seorang penulis!
@else
    Saya bukan penulis
@endrole
// bisa juga menggunakan ini
@hasrole('writer')
    Saya seorang penulis!
@else
    Saya bukan penulis
@endhasrole


// Cek beberapa Role 
@hasanyrole($collectionOfRoles)
    Saya punya satu atau lebih dari satu role
@else
    Saya tidak punya role...
@endhasanyrole
// atau
@hasanyrole('writer|admin')
    Saya penulis atau admin atau keudannya!
@else
    Saya tidak punya role...
@endhasanyrole


// Cek Semua Role
@hasallroles($collectionOfRoles)
    Saya punya semua role!!
@else
    Saya tidak memiliki semua role...
@endhasallroles
// atau
@hasallroles('writer|admin')
    Saya penulis dan juga admin!!
@else
    Saya tidak memiliki semua role...
@endhasallroles

// Alternatif lain, @unlessrole 
@unlessrole('does not have this role')
    Saya tidak punya role
@else
    Saya punya role
@endunlessrole
```

---

### **Cara Menggunakan Spatie di Middleware**

_Ditulis oleh: [Ridwanhasanah](https://github.com/Ridwanhasanah)_


1. Tambahkan Kodingan di bawah ini pada **app/Http/Kernel.php**
```php
protected $routeMiddleware = [
    // ...
    'role' => \Spatie\Permission\Middlewares\RoleMiddleware::class,
    'permission' => \Spatie\Permission\Middlewares\PermissionMiddleware::class,
    'role_or_permission' => \Spatie\Permission\Middlewares\RoleOrPermissionMiddleware::class,
];
```

2. Cara memvalidasi Route
```php
Route::group(['middleware' => ['role:super-admin']], function () {
    //
});

Route::group(['middleware' => ['permission:publish articles']], function () {
    //
});

Route::group(['middleware' => ['role:super-admin','permission:publish articles']], function () {
    //
});

Route::group(['middleware' => ['role_or_permission:super-admin|edit articles']], function () {
    //
});

Route::group(['middleware' => ['role_or_permission:publish articles']], function () {
    //
});
```

3. Memvalidasi Route lebih dari satu **role** atau **permission** menggunakan **| (pipa) karakter**
```php
Route::group(['middleware' => ['role:super-admin|writer']], function () {
    //
});

Route::group(['middleware' => ['permission:publish articles|edit articles']], function () {
    //
});

Route::group(['middleware' => ['role_or_permission:super-admin|edit articles']], function () {
    //
});
```

4. Memvalidasi Middleware di Controller

```php
public function __construct()
{
    $this->middleware(['role:super-admin','permission:publish articles|edit articles']);
}
public function __construct()
{
    $this->middleware(['role_or_permission:super-admin|edit articles']);
}
```
---

## Templating

⬆️ [Ke Atas](#laravel-trik-indonesia) ➡️ [Berikutnya (Basis Data / Database)](#basis-data-database)

- [Html To Pdf](#html-to-pdf)
---

### **Html To Pdf**

_Ditulis oleh: [arifwardan](https://github.com/arifwardan)_

- Sebuah fungsi untuk mengubah string html menjadi string pdf menggunakan wkhtmltopdf. Fungsi ini tidak menggunakan file sementara apa pun dan tidak bergantung pada plugin. untuk info update silahkan lihat <a href="https://github.com/meertensm/HtmlToPdf">meertensm/HtmlToPdf</a>

```php
function toPdf($html, $landscape = false)
{
    $wkhtmltopdf = '/usr/local/bin/wkhtmltopdf';

    // manfaatkan variables laravel's environment 
    // $wkhtmltopdf = env('WKHTMLTOPDF');

    $descriptorspec = [
        0 => ['pipe', 'r'], // stdin
        1 => ['pipe', 'w'], // stdout
        2 => ['pipe', 'w']  // stderr
    ];
    
    //Hapus DYLD_LIBRARY_PAth sebagai solusi errors ketika bekerja di system operasi MAC menggunakan MAMP
    $process = proc_open('unset DYLD_LIBRARY_PATH ;' . $wkhtmltopdf . ' ' . ( $landscape ? '-O landscape' : '' ) . ' -q - -', $descriptorspec, $pipes);

    // kirim HTML di stdin
    fwrite($pipes[0], $html);
    fclose($pipes[0]);

    // Baca hasilnya
    $pdf = stream_get_contents($pipes[1]);
    $errors = stream_get_contents($pipes[2]);

    // Tutup Prosesnya
    fclose($pipes[1]);
    $return_value = proc_close($process);

    if ($errors){
        dd($errors);
    }else{
        header('Content-Type: application/pdf');
        echo $pdf;
    }
}
```

## **Basis Data (Database)**

[Ke Atas](#laravel-trik-indonesia) ➡️ [Berikutnya (Middleware)](#middleware)

- [Koneksi Banyak Basis Data (Multiple-connection Database)](#koneksi-banyak-basis-data-multiple-connection-database)
---

### **Koneksi Banyak Basis Data (Multiple-connection Database)**

_Ditulis oleh: [arifwardan](https://github.com/arifwardan)_

- biasa di gunakan untuk aplikasi menengah ke atas

- cara pemasangan :

1. Tambahkan baris kode ini, di dalam file `.env`.

```env
DB_CONNECTION2=mysql2
DB_HOST2=127.0.0.1
DB_PORT2=3306
DB_DATABASE2=database ke 2
DB_USERNAME2=root
DB_PASSWORD2=password kamu
```

2. Di dalam file `config/database.php` tambahkan baris kode berikut:


```php
'mysql2' => [
    'driver' => 'mysql',
    'url' => env('DATABASE_URL'),
    'host' => env('DB_HOST2', '127.0.0.1'),
    'port' => env('DB_PORT2', '3306'),
    'database' => env('DB_DATABASE2', 'forge'),
    'username' => env('DB_USERNAME2', 'forge'),
    'password' => env('DB_PASSWORD2', ''),
    'unix_socket' => env('DB_SOCKET2', ''),
    'charset' => 'utf8mb4',
    'collation' => 'utf8mb4_unicode_ci',
    'prefix' => '',
    'prefix_indexes' => true,
    'strict' => true,
    'engine' => null,
    'options' => extension_loaded('pdo_mysql') ? array_filter([
        PDO::MYSQL_ATTR_SSL_CA => env('MYSQL_ATTR_SSL_CA'),
    ]) : [],
],
```

3. Untuk default databasenya adalah `firstdb`, jika ingin menggunakan database ke dua ubah connection yang ada di migration, sesuai dengan nama connection di `config/database.php`

```php
public function up()
{
    Schema::connection('mysql2')->create('users', function (Blueprint $table) { // <= perhatikan connection nya
        $table->id();
        $table->string('name');
        $table->string('email')->unique();
        $table->timestamp('email_verified_at')->nullable();
        $table->string('password');
        $table->rememberToken();
        $table->timestamps();
    });
}
```

4. Jalankan migration satu persatu

```bash
php artisan migrate --database=mysql
php artisan migrate --database=mysql2
```

5. selesai

## Middleware

⬆️ [Ke Atas](#laravel-trik-indonesia) ➡️ [Berikutnya (Routing)](#routing)
- [Validasi per menit menggunakan throttle](#validasi-per-menit-menggunakan-throttle)
---

### **Validasi per menit menggunakan throttle**

_Ditulis oleh: [Andihamsah](https://github.com/Andihamsah)_

1. Membuat class middleware menggunakan artisan

```bash
php artisan make:middleware Report
```
	
2. Tambahkan Class middleware tadi ke dalam middlewareGroups yang ada di kernel.php
```php
protected $middlewareGroups = [
    'api' => [
        'report' => \App\Http\Middleware\Report::class,
    ]
];
```

3. Masuk Ke Web.php. dan Tambahkan Route middleware Group
```php
Route::middleware('report', 'throttle:1,1440')->group(function () {
  Route::post('laporan', "Dashboard\ReportController@store")->name('laporan');
});
//'report' -> nama middleware yg sudah terdaftar di kernel
//'throttle' -> library untuk Rate Limit
//'1,1440' -> 1 kali validasi dalam 24 jam/1440 menit
```


**Cara Merubah pesan error throttle**

Masuk ke  `Exceptions/Handler.php`, masukkan kondisi di dalam function render.

Contoh:
```php
if ($exception instanceof ThrottleRequestsException) {

    return response()->json(abort(429, 'Upaya Hari Ini Sudah Habis'));
}else {

    return parent::render($request, $exception);            
}
```

## Routing

⬆️ [Ke Atas](#laravel-trik-indonesia) ➡️ [Berikutnya (Tampilan / view)](#tampilan-view)
- [Route model binding](#route-model-binding)
- [Mengelompokkan route berdasarkan controller yang sama](#mengelompokkan-route-berdasarkan-controller-yang-sama)
---

### **Route Model Binding**

_Ditulis oleh: [hanifazzuhdi](https://github.com/hanifazzuhdi)_

Untuk mencari data berdasarkan id / kolom lain pada suatu table kita bisa menggunakan route model binding yang disediakan laravel. Misalnya : 

```php
//Route
Route::get('book/{book}', 'BookController@show');

//Controller
class BookController {
    public function show (Book $book){
        return $book;
    }
}
```

Kode diatas akan menampilkan data buku sesuai dengan id yang dituliskan sebagai parameternya.

Kita juga bisa mencari data berdasarkan kolom yang lain misalnya kolom slug dengan mengubah route menjadi : 

```php
// Route => tambahkan {:nama_kolom} setelah nama model book
Route::get('book/{book:slug}', 'BookController@show');

// Controller => akan menampilkan data berdasarkan slugnya tanpa query where
class BookController {
    public function show (Book $book){
        return $book;
    }
}
```

Cara ini akan mempersingkat kode dibandingkan harus melakukan query where terlebih dahulu sebelum menampilkan data.

---

### **Mengelompokkan route berdasarkan controller yang sama**

_Ditulis oleh: [mbaharuddinyusuf](https://github.com/ByeByu07)_

untuk mengelompokkan route berdasarkan controller yang sama.

Biasanya kita menulis :

```php
Route::get('/index',[AdminController,'index']);
Route::get('/show',[AdminController,'show']);
Route::get('/edit',[AdminController,'edit']);
```
Akan lebih rapi dan cepat, jika :

```php
Route::controller(AdminController::class)->group(function(){
	Route::get('/index','index');
	Route::get('/show','show');
	Route::get('/edit','edit');
}
```
---

## Tampilan (View)

⬆️ [Ke Atas](#laravel-trik-indonesia) ➡️ [Berikutnya (Lain -lain)](#lain-lain)

- [Cara mengembalikan view dengan variabel](#cara-mengembalikan-view-dengan-variabel)

---

### **Cara mengembalikan view dengan variabel**

_Ditulis oleh: [Muh-Sidik](https://github.com/Muh-Sidik)_

Ada beberapa cara untuk mengolah variabel ke view yang akan kita render untuk `front-end`, yaitu:
1. Menggunakan fungsi `with()`:
```php
return view('view.index')->with('users', $users)->with('posts', $posts);
```

2. Dengan array dan langsung include ke parameter kedua di fungsi `view()`:
```php
return view('view.index', ['users' => $users, 'posts' => $posts]);
```

3. Atau dengan variabel dengan tipe array:
```php
$data = [
    'users' => $users, 
    'posts' => $posts
];

return view('view.index', $data);
```

4. Terakhir dengan cara yang paling banyak di pakai yaitu dengan fungsi `compact()`:
```php
$users = User::get();
$posts = Post::get();

return view('view.index', compact('users', 'posts'))
```
Note: untuk fungsi `compact()` dapat dipelajari <a href='https://www.php.net/manual/en/function.compact.php'>disini</a>

---


## Lain-lain
⬆️ [Ke Atas](#laravel-trik-indonesia)

- [Penulisan singkat `if-else` dan `if-elseif-else` dengan ternary](#penulisan-singkat-if-else-dan-if-elseif-else-dengan-ternary)
---

### **Penulisan singkat if-else dan if-elseif-else dengan ternary**

_Ditulis oleh: [aldyrifaldi](https://github.com/aldyrifaldi)_

- **if-else**
```php
// ternary operators (?:) atau istilah lainnya shorthand if/else.
// bisa digambarkan if = ?, dan else = :
// contoh:

$nilaiUjian = 9;

// menggunakan if-else 

if ($nilaiUjian > 6) {
    echo 'Baik'
} else {
    echo 'Kurang'
}

// menggunakan ternary
echo $nilaiUjian > 6 ? 'Baik' : 'Kurang';  // Baik


// Contoh lain penulisan singkat if-else: 

$role = 0;
echo $role == 0 ? 'Admin' : 'Pengunjung';
```

- **if-elseif-else**

**Hindari** penulisan seperti ini:

```php
$role = 0;
echo $role == 0 ? 'admin' : $role == 1 ? 'guru' : 'santri';
```

Jika mengikuti penulisan di atas maka akan muncul pesan error
**`Unparenthesized a ? b : c ? d : e is deprecated. Use either (a ? b : c) ? d : e or a ? b : (c ? d : e)`**

Yang benar adalah seperti ini:
```php
$role = 0;
echo $role == 0 ? 'admin' : ($role == 1 ? 'guru' : 'santri'); 
```
