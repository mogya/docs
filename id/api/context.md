---
title: 'API: Konteks (Context)'
description: Konteks (`context`) menyediakan objek/parameter tambahan dari Nuxt yang
  tidak tersedia secara tradisional untuk komponen Vue. Konteks (`context`) tersedia
  dalam area siklus (lifecycle) spesial nuxt  seperti `asyncData`, `plugins`, `middlewares`,
  `modules`, dan `store/nuxtServerInit`.
---

## Konteks (Context)

Daftar semua kunci yang tersedia di dalam konteks `context`:

Kunci | Tipe | Tersedia | Deskripsi
--- | --- | --- | ---
`app` | Root Vue Instance | Klien & Server | Akar dari instansi Vue yang mencakup semua plugin. Misalnya, ketika menggunakan `axios`, Anda dapat mengakses `$axios` melalui `context.app.$axios`.
`isClient` | `Boolean` | Klien & Server | Boolean yang memberitahu bahwa render dilakukan di sisi-klien.
`isServer` | `Boolean` | Klien & Server | Boolean yang memberitahu bahwa render dilakukan di sisi-server.
`isStatic` | `Boolean` | Klien & Server | Boolean yang memberitahu bahwa Anda sedang di dalam aplikasi yang dihasilkan (generated app) (melalui `nuxt generate`).
`isDev` | `Boolean` | Klien & Server | Boolean yang memberitahu bahwa Anda sedang berada di dalam mode pengembangan (dev), dapat berguna untuk menyimpan (cache) beberapa data pada mode produksi.
`isHMR` | `Boolean` | Klien & Server | Boolean yang memberitahu bahwa metode/middleware dipanggil dari "webpack hot module replacement" (*hanya pada sisi-klien dalam mode pengembangan (dev)*).
`route` | [Rute Vue Router](https://router.vuejs.org/en/api/route-object.html) | Klien & Server | Instansi rute Vue Router.
`store` | [Vuex Store](https://vuex.vuejs.org/en/api.html#vuexstore-instance-properties) | Klien & Server | Instansi Vuex Store. **Tersedia hanya jika [vuex store](/guide/vuex-store) telah diatur**.
`env` | `Object` | Klien & Server | Environment variables yang diatur di `nuxt.config.js`, lihat [env api](/api/configuration-env).
`params` | `Object` | Klien & Server | Alias dari `route.params`.
`query` | `Object` | Klien & Server | Alias dari `route.query`.
`req` | [`http.Request`](https://nodejs.org/api/http.html#http_class_http_incomingmessage) | Server | Permintaan (request) dari server Node.js. Jika Nuxt digunakan sebagai middleware, objek req mungkin berbeda tergantung dari framework yang Anda gunakan. <br>**Tidak tersedia melalui `nuxt generate`**.
`res` | [`http.Response`](https://nodejs.org/api/http.html#http_class_http_serverresponse) | Server | Respon (response) dari server Node.js. Jika Nuxt digunakan sebagai middleware, objek res mungkin berbeda tergantung dari framework yang Anda gunakan.<br>**Tidak tersedia melalui `nuxt generate`**.
`redirect` | `Function` | Klien & Server | Gunakan metode ini untuk mengalihkan (redirect) pengguna ke rute lain, kode status (status code) digunakan di sisi-server, secara default `302`. `redirect([status,] path [, query])`.
`error` | `Function` | Klien & Server | Gunakan metode ini untuk menampilkan halaman error: `error(parameter)`. `Parameter`-nya harus memiliki properti `statusCode` dan `message`.
`nuxtState` | `Object` | Klien | Status Nuxt, berguna untuk plugin yang menggunakan `beforeNuxtRender` untuk mendapatkan status nuxt pada sisi klien sebelum hidrasi. **Hanya tersedia dalam mode `universal`**.
`beforeNuxtRender(fn)` | `Function` | Server | Gunakan metode ini untuk memperbarui (update) variabel `__NUXT__` yang di-render di sisi-klien, `fn` (dapat berupa asynchronous) dipanggil dengan `{ Components, nuxtState }`, lihat [contoh](https://github.com/nuxt/nuxt.js/blob/cf6b0df45f678c5ac35535d49710c606ab34787d/test/fixtures/basic/pages/special-state.vue).
