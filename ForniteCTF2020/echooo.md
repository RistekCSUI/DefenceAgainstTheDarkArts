# Echooo

by prajnapras19

---

## Flag

```
NETSOS{cuma_echo_ehehe_379e1d}
```

## Description
Program ini akan melakukan command terminal echo pada setiap input yang kamu berikan, kecuali karakter alphanumeric.<br>
Flag ada di ./flag.txt.
`nc 103.136.18.212 1197`

## Tags
Misc, bashjail

## How to solve
Jika kita menonton [video ini](https://www.youtube.com/watch?v=6D1LnMj0Yt0), maka akan terlihat bahwa terdapat `/bin/cat` yang dapat dimanfaatkan untuk mengeluarkan isi flag.<br>
`/bin/cat` dapat dipanggil payload `/???/???` (walaupun bukan hanya `/bin/cat` yang cocok dengan command tersebut), dan `flag.txt` dapat dipanggil dengan cara `????.???`.<br>
Karena commandnya adalah `echo <input kita>`, maka kita perlu memasukkan payload untuk mem-bypass echo terlebih dahulu. Kita bisa manfaatkan semicolon (`;`), sehingga payload kita akan membentuk `echo;/bin/cat flag.txt`.
Sehingga payload akhirnya adalah `;/???/??? ????.???`
