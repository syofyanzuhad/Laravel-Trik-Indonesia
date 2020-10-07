# Laravel Trik
Kumpulan trik berbahasa indonesia untuk menggunakan framework laravel.

_Berisi: **3** trik._

**Terakhir diupdate 8 Oktober 2020**

> Berikan pull request untuk memberikan manfaat lebih banyak !

## Daftar Isi :

- [DB Models dan Eloquent](#db-models-dan-eloquent) (2 trik).
- [Lain - lain](#lain-lain) (1 trik).

## DB Models dan Eloquent

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Lain -lain)](#lain-lain)

- [Cara mengubah format output `created_at` dan `updated_at` lewat model](#cara-mengubah-format-output-created_at-dan-updated_at-lewat-model)

- [Cara Mengubah format text `created_at` dan `updated_at` menjadi `tgl_dibuat` dan `tgl_diupdate` lewat model](#cara-mengubah-format-text-created_at-dan-updated_at-menjadi-tgl_dibuat-dan-tgl_diupdate-lewat-model)

### Cara mengubah format output `created_at` dan `updated_at` lewat model

**created_at**

Untuk mengubah format `created_at`, tambahkan method berikut di dalam model:

```
public function getCreatedAtFormattedAttribute()
{
   return $this->created_at->format('H:i d, M Y');
}
```
Method ini bisa digunakan dengan cara seperti ini : `$entry->created_at_formatted`.

Dan akan menampilkan hasil seperti ini: `04:19 23, Aug 2020`.

**updated_at**

Untuk mengubah format `updated_at`, tambahkan method berikut di dalam model:

```
public function getUpdatedAtFormattedAttribute()
{
   return $this->updated_at->format('H:i d, M Y');
}
```
Method ini bisa digunakan dengan cara seperti ini : `$entry->updated_at_formatted`.

Dan akan menampilkan hasil seperti ini: `04:19 23, Aug 2020`.

### Cara Mengubah format text created_at dan updated_at menjadi tgl_dibuat dan tgl_diupdate lewat model

Caranya sangat mudah 

**created_at**
Untuk created_at cukup menambahkan :

     const CREATED_AT = 'tgl_dibuat';

**updated_at**

dan untuk  updated_at cukup menambahkan:

    const UPDATED_AT = 'tgl_diupdate';
 

## Lain-lain
⬆️ [Ke Atas](#laravel-trik)
- [Penulisan singkat `if dan else, if elseif dan else`](#penulisan-singkat-if-dan-else-if-elseif-dan-else)

## Penulisan singkat if dan else, if elseif dan else 

**if dan else**
Penulisan singkat if dan else yaitu: 

    $role = 0;
    echo $role == 0 ? 'Admin' : 'Pengunjung';
**if elseif dan else**
Penulisan singkat if elseif dan else yaitu: 
Hindari penulisan seperti ini: 

    $role = 0;
    echo $role == 0 ? 'admin' : $role == 1 ? 'guru' : 'santri';
    
	
Jika mengikuti penulisan di atas maka akan muncul pesan error
`**Unparenthesized `a ? b : c ? d : e` is deprecated. Use either `(a ? b : c) ? d : e` or `a ? b : (c ? d : e)`**`

Yang benar adalah seperti ini
    
    $role = 0;
    echo $role == 0 ? 'admin' : ($role == 1 ? 'guru' : 'santri'); 

