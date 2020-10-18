# Laravel Trik
Kumpulan trik berbahasa indonesia untuk menggunakan framework laravel.

_Berisi: **8** trik._

**Terakhir diupdate 18 Oktober 2020**

> Berikan pull request untuk memberikan manfaat lebih banyak !

# Daftar Isi :

- [DB Models dan Eloquent](#db-models-dan-eloquent) (2 trik).
- [Perintah `artisan`](#perintah-artisan) (1 trik).
- [Package](#package) (2 trik).
- [Templating](#templating) (1 trik).
- [Basis Data](#basis-data) (1 trik).
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

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Lain -lain)](#templating)

- [Install Spatie Role Permission](#install-spatie-role-permission)
- [Cara Menggunakan Role](#cara-menggunakan-role)

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

### Cara menggunakan Role
1. membuat role 
```
use Spatie\Permission\Models\Role;

$role = Role::create(['name' => 'writer']);
```

2. Menambahkan role kepada user
```
$user->assignRole($role);
```
3. Menghapus role pada user
```
$user->revokeRoleTo($role); //$role = nama rolenya apa
```

## Templating

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Basis Data)](#basis-data)

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

### **Basis Data**

[Ke Atas](#laravel-trik) ➡️ [Berikutnya (Lain -lain)](#lain-lain)

- [Banyak Basis Data](#banyak-basis-data)

## Banyak Basis Data atau Multiple Database
- biasa di gunakan untuk aplikasi menengah ke atas
- cara pemasangan

1 di dalam file env tambahkan ini

```
DB_CONNECTION2=mysql
DB_HOST2=127.0.0.1
DB_PORT2=3306
DB_DATABASE2=database ke 2
DB_USERNAME2=root
DB_PASSWORD2=password kamu
```

2 didalam config/database.php tambahkan


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

3 untuk default databasenya adalah firstdb, jika ingin menggunakan database ke dua ubah table di migration

```
  public function up()
    {
        Schema::connection(mysql2)->create('users', function (Blueprint $table) { // <= perhatikan 
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

4 jalankan migration satu satu

```
php artisan migrate --database=mysql
php artisan migrate --database=mysql2
```

5 selesai


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


