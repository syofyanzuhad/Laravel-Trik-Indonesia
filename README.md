# Laravel Trik
Kumpulan trik berbahasa indonesia untuk menggunakan framework laravel.

_Berisi: **1** trik._

**Terakhir diupdate 6 Oktober 2020**

## Daftar Isi :

- [DB Models dan Eloquent](#db-models-dan-eloquent) (1 trik).
- [Lain - lain](#lain-lain) (0 trik).

## DB Models dan Eloquent

⬆️ [Ke Atas](#laravel-trik) ➡️ [Berikutnya (Lain -lain)](#lain-lain)

- [Cara mengubah format `created_at` dan `updated_at` lewat model](#cara-mengubah-format-created_at-dan-updated_at-lewat-model)

### Cara mengubah format `created_at` dan `updated_at` lewat model

**created_at**

Untuk mengubah format `created_at`, tambahkan method berikut di dalam model:

```
public function getCreatedAtFormattedAtAttribute()
{
   return $this->created_at->format('H:i d, M Y');
}
```
Method ini bisa digunakan dengan cara seperti ini : `$entry->created_at_formatted`.

Dan akan menampilkan hasil seperti ini: `04:19 23, Aug 2020`.

**updated_at**

Untuk mengubah format `updated_at`, tambahkan method berikut di dalam model:

```
public function getUpdatedAtFormattedAtAttribute()
{
   return $this->updated_at->format('H:i d, M Y');
}
```
Method ini bisa digunakan dengan cara seperti ini : `$entry->updated_at_formatted`.

Dan akan menampilkan hasil seperti ini: `04:19 23, Aug 2020`.

## Lain-lain
