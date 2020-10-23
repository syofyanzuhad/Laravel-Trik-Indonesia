# Laravel Trik
Kumpulan trik berbahasa indonesia untuk menggunakan framework laravel.

_Berisi: **9** trik._

**Terakhir diupdate 20 Oktober 2020**

> Berikan pull request untuk memberikan manfaat lebih banyak !

# Daftar Isi :

- [DB Models dan Eloquent](#db-models-dan-eloquent) (2 trik).
- [Perintah `artisan`](#perintah-artisan) (1 trik).
- [Package](#package) (5 trik).
- [Templating](#templating) (1 trik).
- [Basis Data (Database)](#basis-data-database) (1 trik).
- [Middleware](#middleware)(1 trik).
- [Lain - lain](#lain-lain) (1 trik).

## DB Models dan Eloquent

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Perintah `artisan`)](#perintah-artisan)

- [Cara mengubah format output `created_at` dan `updated_at` lewat model](#cara-mengubah-format-output-created_at-dan-updated_at-lewat-model)

- [Cara Mengubah format text `created_at` dan `updated_at` menjadi `tgl_dibuat` dan `tgl_diupdate` lewat model](#cara-mengubah-format-text-created_at-dan-updated_at-menjadi-tgl_dibuat-dan-tgl_diupdate-lewat-model)

### **Cara mengubah format output `created_at` dan `updated_at` lewat model**

- **created_at**

Untuk mengubah format `created_at`, tambahkan method berikut di dalam model:

```
public function getCreatedAtFormattedAttribute()
{
   return $this->created_at->format('H:i d, M Y');
}
```
Method ini bisa digunakan dengan cara seperti ini : `$entry->created_at_formatted`.

Dan akan menampilkan hasil seperti ini: `04:19 23, Aug 2020`.

- **updated_at**

Untuk mengubah format `updated_at`, tambahkan method berikut di dalam model:

```
public function getUpdatedAtFormattedAttribute()
{
   return $this->updated_at->format('H:i d, M Y');
}
```
Method ini bisa digunakan dengan cara seperti ini : `$entry->updated_at_formatted`.

Dan akan menampilkan hasil seperti ini: `04:19 23, Aug 2020`.

### **Cara Mengubah format text created_at dan updated_at menjadi tgl_dibuat dan tgl_diupdate lewat model**

Caranya sangat mudah 

- **created_at**

Untuk created_at cukup menambahkan :

     const CREATED_AT = 'tgl_dibuat';

- **updated_at**

dan untuk  updated_at cukup menambahkan:

    const UPDATED_AT = 'tgl_diupdate';

## Perintah `artisan`

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Package)](#package)

- [Cara membuat model, controller, migration sekaligus](#cara-membuat-model-controller-migration-sekaligus)

### **Cara membuat model, controller, migration sekaligus**

Untuk membuat `model`, `controller`, dan `migration` sekaligus cukup jalankan perintah untuk membuat model dengan tambahan `-mc`, seperti berikut :

```
php artisan make:model User -mc
```

Jika kita ingin membuat `controller` dengan resource (default method dari laravel). Gunakan perintah ini (dengan tambahan huruf `r`):
```
php artisan make:model User -mcr
```
## Package

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Templating)](#templating)

- [Install Spatie Role Permission](#install-spatie-role-permission)
- [Cara Menggunakan Role](#cara-menggunakan-role)
- [Cara Menggunakan Permission](#cara-menggunakan-permission)
- [Cara Menggunakan Permission Via Role](#cara-menggunakan-permission-via-role)
- [Cara Menggunakan Spatie di Blade](#cara-menggunakan-spatie-di-blade)
---
### **Install Spatie Role Permission**

1. Install package

 `composer require spatie/laravel-permission`
 
2. edit app/config.php
```
'providers' => [
    // ...
    Spatie\Permission\PermissionServiceProvider::class,
];
```
3. publish migration di terminal

`php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"`

4. clear config & cache

 `php artisan optimize:clear`
 **or**
 `php artisan config:clear`
 
5. terakhir jalankan migration

 `php artisan migrate`

---

### **Cara menggunakan Role**
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

1. Menambahkan Permission
```php
// Adding permissions to a user
$user->givePermissionTo('edit articles');

// Adding permissions via a role
$user->assignRole('writer');

$role->givePermissionTo('edit articles');

// You can also give multiple permission at once
$user->givePermissionTo('edit articles', 'delete articles');

// You may also pass an array
$user->givePermissionTo(['edit articles', 'delete articles']);
```

2. Menghapus Permission
```php
// A permission can be revoked from a user
$user->revokePermissionTo('edit articles');

// Or revoke & add new permissions in one go:
$user->syncPermissions(['edit articles', 'delete articles']);
```

3. Mengecek Apakah User Mempunyai Permissioin
```php
$user->hasPermissionTo('edit articles');

// Or you may pass an integer representing the permission id
$user->hasPermissionTo('1');
$user->hasPermissionTo(Permission::find(1)->id);
$user->hasPermissionTo($somePermission->id);

// You can check if a user has Any of an array of permissions:
$user->hasAnyPermission(['edit articles', 'publish articles', 'unpublish articles']);

// ...or if a user has All of an array of permissions:
$user->hasAllPermissions(['edit articles', 'publish articles', 'unpublish articles']);

// You may also pass integers to lookup by permission id
$user->hasAnyPermission(['edit articles', 1, 5]);
```

---

### **Cara Menggunakan Permission Via Role**
1. Menerapkan Role ke User manapun
```php
$user->assignRole('writer');

// You can also assign multiple roles at once
$user->assignRole('writer', 'admin');
// or as an array
$user->assignRole(['writer', 'admin']);
```
2. Menghapus Role dari User
```php
$user->removeRole('writer');
```
3. Update Role dari User
```php
// All current roles will be removed from the user and replaced by the array given
$user->syncRoles(['writer', 'admin']);
```
4. Memeriksa User mempunyai Role, biasanya di gunakan untuk validasi
```php
// All current roles will be removed from the user and replaced by the array given
$user->syncRoles(['writer', 'admin']);

// You can also determine if a user has any of a given list of roles:
$user->hasAnyRole(['writer', 'reader']);
// or
$user->hasAnyRole('writer', 'reader');

// You can also determine if a user has all of a given list of roles:
$user->hasAllRoles(Role::all());
```
---
### **Cara Menggunakan Spatie di Blade**
1. Permission pada Blade
```php
@can('edit articles')
  //
@endcan
// or

@if(auth()->user()->can('edit articles') && $some_other_condition)
  //
@endif
// Bisa juga menggunakan @can, @cannot, @canany, dan @guest
```
2. Role pada Blade
```php
// Persiksa sebuah role
@role('writer')
    I am a writer!
@else
    I am not a writer...
@endrole
// bisa juga menggunakan ini
@hasrole('writer')
    I am a writer!
@else
    I am not a writer...
@endhasrole


// Cek beberapa Role 
@hasanyrole($collectionOfRoles)
    I have one or more of these roles!
@else
    I have none of these roles...
@endhasanyrole
// atau
@hasanyrole('writer|admin')
    I am either a writer or an admin or both!
@else
    I have none of these roles...
@endhasanyrole


// Cek Semua Role
@hasallroles($collectionOfRoles)
    I have all of these roles!
@else
    I do not have all of these roles...
@endhasallroles
// atau
@hasallroles('writer|admin')
    I am both a writer and an admin!
@else
    I do not have all of these roles...
@endhasallroles

// Alternatif lain, @unlessrole 
@unlessrole('does not have this role')
    I do not have the role
@else
    I do have the role
@endunlessrole
```

## Templating

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Basis Data / Database)](#basis-data-database)

- [Html To Pdf](#html-to-pdf)

### **Html To Pdf**
- Sebuah fungsi untuk mengubah string html menjadi string pdf menggunakan wkhtmltopdf. Fungsi ini tidak menggunakan file sementara apa pun dan tidak bergantung pada plugin. untuk info update silahkan lihat <a href="https://github.com/meertensm/HtmlToPdf">meertensm/HtmlToPdf</a>

```
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

[Ke Atas](#laravel-trik) ➡️ [Berikutnya (Middleware)](#middleware)

- [Koneksi Banyak Basis Data (Multiple-connection Database)](#koneksi-banyak-basis-data-multiple-connection-database))

### Koneksi Banyak Basis Data (Multiple-connection Database)

- biasa di gunakan untuk aplikasi menengah ke atas

- cara pemasangan :

1. Tambahkan baris kode ini, di dalam file `.env`.

```
DB_CONNECTION2=mysql
DB_HOST2=127.0.0.1
DB_PORT2=3306
DB_DATABASE2=database ke 2
DB_USERNAME2=root
DB_PASSWORD2=password kamu
```

2. Di dalam file `config/database.php` tambahkan baris kode berikut:


```
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

3. Untuk default databasenya adalah `firstdb`, jika ingin menggunakan database ke dua ubah connection yang ada di migration

```
  public function up()
    {
        Schema::connection(mysql2)->create('users', function (Blueprint $table) { // <= perhatikan connection nya
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

```
php artisan migrate --database=mysql
php artisan migrate --database=mysql2
```

5. selesai

## Middleware

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Lain -lain)](#lain-lain)
- [Validasi per menit menggunakan throttle](#Validasi-per-menit-menggunakan-throttle)

### **Validasi per menit menggunakan throttle**
1. Membuat class middleware menggunakan artisan


		php artisan make:middleware Report

	
2. Tambahkan Class middleware tadi ke dalam middlewareGroups yang ada di kernel.php

		protected $middlewareGroups = [

			'api' => [

				'report' => \App\Http\Middleware\Report::class,

			]

		];


3. Masuk Ke Web.php. dan Tambahkan Route middleware Group

		Route::middleware('report', 'throttle:1,1440')->group(function () {

			Route::post('laporan', "Dashboard\ReportController@store")->name('laporan');

		});

		//'report' -> nama middleware yg sudah terdaftar di kernel

		//'throttle' -> library untuk Rate Limit

		//'1,1440' -> 1 kali validasi dalam 24 jam/1440 menit



**Cara Merubah pesan error throttle**

Masuk ke  `Exceptions/Handler.php`, masukkan kondisi di dalam function render.

Contoh:

	if ($exception instanceof ThrottleRequestsException) {
	
	    return response()->json(abort(429, 'Upaya Hari Ini Sudah Habis'));
	    
	}else {
	
	    return parent::render($request, $exception);            
	    
	}


## Lain-lain
⬆️ [Ke Atas](#laravel-trik)

- [Penulisan singkat `if-else` dan `if-elseif-else` dengan ternary](#penulisan-singkat-if-else-dan-if-elseif-else-dengan-ternary)

### **Penulisan singkat if-else dan if-elseif-else dengan ternary**

- **if-else**

Penulisan singkat if-else yaitu: 

    $role = 0;
    echo $role == 0 ? 'Admin' : 'Pengunjung';

- **if-elseif-else**

**Hindari** penulisan seperti ini: 

> $role = 0;

> echo $role == 0 ? 'admin' : $role == 1 ? 'guru' : 'santri';
	
Jika mengikuti penulisan di atas maka akan muncul pesan error
**`Unparenthesized a ? b : c ? d : e is deprecated. Use either (a ? b : c) ? d : e or a ? b : (c ? d : e)`**

Yang benar adalah seperti ini:
    
    $role = 0;
    echo $role == 0 ? 'admin' : ($role == 1 ? 'guru' : 'santri'); 


