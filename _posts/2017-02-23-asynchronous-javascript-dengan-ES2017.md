---
title: Asynchronous Javascript dengan ES2017
---
## Konsep Asynchronous
Bagaimana kita melakukan pemrograman async di javascript (ES)? di post kali ini akan kita telaah secara mendalam dengan bahasa Indonesia. Yak, that's what unique about this post, using bahasa as explanation language instead of proper english.

Javascript itu bahasa yang single-threaded, artinya apa, berarti bahwa hanya satu bagian kode saja yang bisa berjalan dalam satu waktu. Tidak seperti bahasa seperti Java atau C++ yang mempunyai kemampuan multi-threading yaitu menjalankan beberapa bagian kode dalam satu waktu. Jadi jangan mengira dengan async di javascript kita dapat menjalankan beberapa bagian kode dalam satu waktu (secara paralel).

Asynchronous jika di definisikan dalam bahasa inggris begini:
> of or requiring a form of computer control timing protocol in which a specific operation begins upon receipt of an indication (signal) that the preceding operation has been completed.

Nah, kalo di tafsirkan, maksud dari async adalah melakukan panggilan untuk mengerjakan operasi yang lain sebelum operasi yang sedang berlangsung selesai.

## Analogi Asynchronous
Analoginya begini, Abdul punya aktivitas rutin sarapan lalu sekolah, lalu main, lalu mengerjakan PR. Abdul melakukan aktivitas ini secara runut atau sifatnya synchronous. Tapi pada suatu saat Abdul melakukan rutinitas berbeda di pagi hari. Pada saat dia sedang sarapan dia teringat bahwa hari ini ada pengumpulan PR Biologi, akhirnya sebelum sarapannya selesai, dia mengerjakan dahulu PR biologinya, lalu lanjut sarapan lagi dan meneruskan aktivitasnya seperti biasa. Apa yang dilakukan Abdul ini sifatnya asynchronous. Abdul melakukan aktivitas lain sebelum aktivitas yang sekarang dilakukannya selesai dan dilakukan satu-per-satu, tidak bersamaan (tidak paralel).

## Pemrograman Asynchronous di Javascript
Salah satu kelebihan Javascript dibanding bahasa pemrograman lainnya adalah javascript dapat melakukan pekerjaan secara asyncrhonous, seperti Abdul. Ada 4 teknik untuk melakukan pemrograman async di javascript, yaitu *Callback*, *Promises*, *Generator* dan *Async/await*.

### 1. Callback
Callback berarti kita menjalan sebuah fungsi (mis. fungsi A) yang mempunyai paramater fungsi baru (fungsi callback dari A) yang dijalankan hanya dan hanya jika fungsi A berjalan pada suatu waktu tertentu.

``` javascript

import fs from 'fs' // menginput module fs

const inputFile = 'input.txt'
const outputFile = 'output.txt'

fs.readFile(inputFile, 'utf8', (error, data) => {
    // nesting callback dari fungsi readFile
    if (error) throw error
    console.log(`Sudah selesai membaca file '${inputFile}'.`)

    fs.writeFile(outputFile, data, error => {
          // nesting callback dari fungsi writeFile
          if (error) throw error
          console.log(`Sudah selesai menulis ke file '${outputFile}'.`)
        })
    }
})

// untuk mencontohkan sifat Asynchronous
console.log('Log ini akan berjalan lebih dahulu.')

```
Jika dilihat dari konsol maka log yang akan ditampilkan akan seperti ini

```
Log ini akan berjalan lebih dahulu.
Sudah selesai membaca file 'input.txt'.
Sudah selesai menulis ke file 'output.txt'.

```
Dari log tersebut berarti fs melakukan eksekusi membaca dan menulis setelah melakukan log akhir. Namun kekurangan dari callback adalah jika callback sudah terlalu banyak maka kodingan kamu akan menjadi tidak rapih dan sangat sulit untuk di trace. Bayangkan jika kamu membuat fungsi callback nesting berlapis hingga 100 buah, sulit di trace bukan? jelek untuk dilihatkan? tidak elegan bukan? hal ini adalah apa yang dikenal dengan istilah 'neraka callback'.

### 2. Promise
Melakukan operasi asynchronous dengan callback merupakan cara yang tidak efisien. Oleh karena itu, para ahli javascript di TC-39 (comitee untuk membuat desain bahasa javascript) membuat sesuatu yang disebut Promises. Promises adalah object yang dimasukkan fungsi 'ekskutor' di dalamnya.
``` javascript

const waitUntil = ms => {
    // promise adalah objek yang mempunyai parameter resolve dan reject
    return new Promise((resolve, reject) => {
      if (ms){
        // buat delay sebesar miliseconds yang di inginkan
        setTimeout(() => { resolve('selesai.') }, ms)
      } else {
        // jika tidak ada ms maka reject
        reject('No time to live defined.')
      }
    })
}

waitUntil(1000).then(value => {
    console.log(value) // log value-nya
}).catch(err => {
    if (err) throw err // throw error
})

```
Dari contoh diatas kita dapat melihat bahwa fungsi 'waitUntil' me-return sebuah objek berupa Promise yang memiliki dua parameter fungsi, yaitu resolve dan reject. Resolve berarti operasi yang kita lakukan sudah berhasil, sedangkan reject berarti operasi yang kita lakukan gagal. Di dalam fungsi eksekutor objek Promise terdapat tiga buah keadaan, seperti layaknya janji, janji dapat 'tertunda' dalam konteks Promise hal ini berarti keadaan dimana fungsi resolve ataupun fungsi reject belum tereksekusi. Keadaan kedua adalah jika keadaan janji 'terpenuhi', kalau pada Promise yaitu keadaan saat fungsi resolve tereksekusi dan terakhir keadaan 'tertolak' dimana saat fungsi reject di eksekusi.

### 3. Generator
Generator adalah fungsi yang mampu 'mengiterasi' nilai hingga beberapa kali dengan menggunakan keyword 'yield'. Keyword yield berfungsi seolah-olah kita me-return sebuah value dari fungsi generator jika fungsi generator tersebut dipanggil dengan fungsi next(). Berikut ini merupakan contoh generator yang menghasilkan beberapa iterasi dari 'yield'.

``` javascript
function *genTelor() {
    yield 'telorA'
    yield 'telorB'
    yield 'telorC'
}

// kita mendefinisikan variable berupa fungsi generator
let hasil = genTelor()

// kita panggil satu-per-satu hasil dari yield genTelor
console.log(hasil.next())           // "{ value: 'telorA', done: false }"
console.log(hasil.next().value)     // "telorB"
console.log(hasil.next().done)      // true

```
Dari contoh kode diatas kita dapat membuat fungsi yang memiliki kemampuan sebagai generator dengan menambahkan asterisk atau bintang (*) di depan nama fungsi. Keyword yield digunakan untuk memberhentikan sementara eksekusi fungsi dan mengembalikan (return) value diberikan padanya. Saat kita mengeksekusi kembali generator dengan fungsi next() maka generator akan melanjutkan eksekusi fungsi ke 'yield' selanjutnya. Berikut adalah contoh bagaimana kita dapat memasukan parameter pada fungsi next().

``` javascript
function *genTelor() {
    let param1 = yield 'telorA'
    let param2 = yield param1 + 'telorB'
    yield param2 = 'telorC'
}

let hasil = genTelor()

console.log(hasil.next())                   // "{ value: 'telorA', done: false }"
console.log(hasil.next('suka ').value)      // "suka telorB"
console.log(hasil.next('makan '))           // "{ value: 'makan telorC', done: true }"

```
Pada kode diatas, selain memanggil value dari generator genTelor() kita juga memasukan parameter pada fungsi next() nya. Di dalam fungsi genTelor() kita harus membuat variabel param1 yang di pass ke yield berikutnya untuk menandakan bahwa kita ingin menggunakan parameter pada pemanggilan yield berikutnya. Jadi fungsi * generator tidak hanya dapat 'memanggil; dengan nilai dari yield, namun kita juga dapat 'memasukan' parameter pada keyword yield pula.

### 4. Async/await
Meskipun teknik asynchronous menggunakan generator sudah cukup robust, namun apa yang kita inginkan, yaitu mempunyai fungsi asinkronus sebenarnya belum tercapai. Di ES2017 dikenalkan sebuah dua keyword baru yaitu *async* untuk membuat sebuah fungsi asinkronus yang me-return Promise dan *await* yaitu keyword untuk memberhentikan fungsi async dan 'menunggu' sampai eksekusi fungsi yang di tunggu selesai. Proposal ini sudah mencapai tahap akhir yaitu finished dan sudah di rilis di ES2017. Proposal ini di ajukan oleh Brian Terlson dan sudah bisa kamu lihat di website TC39 [disini](https://tc39.github.io/ecmascript-asyncawait/).

``` javascript

const penumpangSiap = true

function penumpang() {
    return new Promise(resolve, reject){
        if (penumpangSiap){
            // menunggu dalam bus dalam waktu 2 detik
            setTimeout(() => {
                // me-resolve status penumpang
                resolve('siap.')
            }, 2000)
        } else {
            reject('belum siap.')
        }
    }
}

async function busKota(){
    let statusPenumpang = await penumpang()
    console.log(statusPenumpang)
}

```
Pada contoh diatas, kita menggunakan membuat sebuah Promise penumpang yang akan menyelesaikan dengan status kesiapan penumpang dalam bus. Lalu, di fungsi asynchronous busKota() kita menunggu status penumpang dengan keyword *await*, keyword *await* akan menunggu Promise penumpang sampai keadaan Promise tersebut terpenuhi atau tertolak. Jika Promise sudah ter-resolve maka *await* akan langsung me-return nilai dari Promise tersebut, di kode diatas statusPenumpang akan menangkap nilai dari Promise. Hal yang menarik di fungsi async ini, kita dapat melakukan pemrosesan 'seolah-olah' bekerja secara paralel dengan cara berikut

``` javascript

const penumpangSiap = true

const tungguPenumpang = (waktu) => {
    return new Promise(resolve, reject){
        if (penumpangSiap){
            setTimeout(() => {
                resolve('siap.')
            }, waktu)
        } else {
            reject('belum siap.')
        }
    }
}

// membuat dua fungsi yang mempunyai Promise yang sama
function penumpang1() return tungguPenumpang(2000)
function penumpang2() return tungguPenumpang(3000)

async function busKota() {
    const [statusPenumpang1, statusPenumpang2] = await Promise.all([
        penumpang1(),
        penumpang2(),
    ])

    console.log(statusPenumpang1, statusPenumpang2)
}

```
Pada kode diatas kita mempunyai dua fungsi yang akan me-return Promise dengan waktu yang berbeda. Selanjutnya, fungsi async akan menunggu kedua Promise sampai keduanya terpenuhi, pada kasus diatas berarti await akan menunggu sampai waktu tiga detik karena waktu dimana kedua Promise akan terpenuhi adalah tiga detik. Setelah awai sukses untuk me-resolve kedua Promise maka ia akan me-return valuenya dalam bentuk array. Karena hasil di return dalam array, kita dapat melakukan destruktur ke dua variabel yaitu vairabel statusPenumpang1 dan statusPenumpang2.


