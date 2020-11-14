# Classic PHP

## Deskripsi
http://103.136.18.212:5706/

**Author:** bonceng

## Solusi
Diberikan sebuah link website. Saat dibuka, website menampilkan source code.

```
<?php

function sha256($data){
    return hash("sha256", $data);
}

if (isset($_GET['a']) && isset($_GET['b']) && isset($_GET['c'])) {
    if (!is_string($_GET['a']) && !is_string($_GET['a']) && !is_string($_GET['a']))
        die("No cheating cheating gan.");

    if ($_GET['a'] === $_GET['b'] || $_GET['a'] === $_GET['c'] || $_GET['b'] === $_GET['c'])
        die("Harus beda semua!!!");

    if (preg_match("/\d/i", $_GET['a']) > 0 && preg_match("/\d/i", $_GET['b']) > 0)
        die("Masih aja mau cheating, deh!");
    
    if (sha256($_GET['a']) != sha256($_GET['b']))
        die("Yok nyerah aja yok.");
    
    if (md5($_GET['c']) != $_GET['c'])
        die("Mending nyerah sih...");
    
    include('bendera.php');
    print $tujuh_belas_agustus_indonesia_merdeka;
    
} else 
    show_source(__FILE__);

?> 
```

Kemungkinan besar flag ada di variabel `$tujuh_belas_agustus_indonesia_merdeka` di dalam file `bendera.php`. Maka, agar website mengeluarkan flag, kita perlu melakukan setting parameter get 'a', 'b', dan 'c' dengan sebuah string yang berbeda. Kemudian, berdasarkan preg_match maka parameter 'a' dan 'b' haruslah tersusun atas non-numeric character. Lalu, kita perlu menyamakan hash sha256 dari parameter 'a' dan 'b', serta hash md5 dari parameter 'c' dengan value dari 'c'.

Apabila diperhatikan, saat menyamakan nilai hash, digunakan operator == yang mana bisa kita manfaatkan type juggling. Kita cari dua buah string berbeda yang hasil sha256nya dapat berubah ke double (karena akan terjadi precision error). Kemudian cari string yang hash md5nya dan valuenya dapat dianggap sebagai double oleh PHP. Kita dapat gunakan magic hash pada https://github.com/spaze/hashes/.

Gunakan payload `?a=TyNOQHUS&b=\}Fr@!-a&c=0e215962017` lalu didapatkan flagnya.

## Flag
NETSOS{Classic_PHP_Type_Juggling_y0ooW_ce7e1db5}
