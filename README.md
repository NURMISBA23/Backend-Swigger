# Lab-Backend

<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master" target="_blank"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#9" alt="Coverage" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg" alt="Donate us"/></a>
    <a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow" alt="Follow us on Twitter"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

# Laporan Struktur Proyek NestJS Berdasarkan Gambar

Laporan ini menyajikan analisis terstruktur terhadap arsitektur proyek NestJS, didasarkan pada visualisasi struktur folder yang diberikan.  Fokus utama laporan adalah identifikasi dan lokalisasi komponen-komponen arsitektur NestJS yang krusial. Komponen-komponen yang dianalisis meliputi aspek instalasi framework NestJS, implementasi Controller dan Service, pengorganisasian Module, integrasi Prisma ORM, mekanisme autentikasi, penerapan middleware, guard, dan decorator, fungsionalitas file uploader dan getter, implementasi query search, dan integrasi WebSocket.  Laporan ini disusun dengan tujuan untuk menyediakan dokumentasi yang jelas dan informatif mengenai struktur proyek NestJS ini.
Berikut adalah direktori dan file utama dalam proyek ini:

*   **`dist`**: Direktori output hasil kompilasi kode TypeScript menjadi JavaScript. Direktori ini dihasilkan setelah proses build proyek.
*   **`node_modules`**: Direktori yang berisi semua dependensi proyek yang terinstal, termasuk library NestJS dan dependensi lainnya. Direktori ini tidak termasuk dalam repositori kode dan biasanya dibuat setelah menjalankan perintah `npm install` atau `yarn install`.
*   **`prisma`**: Direktori yang terkait dengan integrasi Prisma ORM. Direktori ini berisi skema database Prisma (`schema.prisma`) dan file-file terkait integrasi Prisma dengan NestJS.
*   **`src`**: Direktori utama yang berisi kode sumber aplikasi NestJS. Di dalam direktori `src`, kode diorganisasikan berdasarkan fitur dan jenis komponen (controller, service, module, dto, entity, dll.).
    *   **Direktori Fitur (contoh: `chat`, `profile`, `app`, `auth`)**: Direktori-direktori ini mengelompokkan komponen-komponen yang terkait dengan fitur-fitur spesifik aplikasi (misalnya, fitur chat, fitur profil pengguna, fitur otentikasi).
    *   **`dto`**: Direktori untuk Data Transfer Objects (DTOs). DTOs digunakan untuk mendefinisikan struktur data yang digunakan dalam permintaan dan respons API.
    *   **`entity`**: Direktori untuk definisi entitas database. Entitas merepresentasikan tabel atau koleksi dalam database.
    *   **`main.ts`**: File utama aplikasi NestJS, titik masuk aplikasi. File ini bertanggung jawab untuk bootstrapping aplikasi NestJS.
    *   **`prisma.ts`**: File yang kemungkinan berisi konfigurasi atau instance Prisma Client untuk interaksi dengan database.
    *   **`user.decorator.ts`**: File yang berisi custom decorator terkait pengguna, kemungkinan untuk mengambil informasi pengguna dari request.
*   **`test`**: Direktori untuk file-file pengujian (unit testing, integration testing, e2e testing).
*   **`uploads`**: Direktori yang kemungkinan digunakan untuk menyimpan file yang diunggah oleh pengguna aplikasi.
*   **File Konfigurasi dan Lainnya**:
    *   `.eslintrc.js`, `.gitignore`, `.prettierrc`, `nest-cli.json`, `package-lock.json`, `package.json`, `README.md`, `tsconfig.build.json`, `tsconfig.json`: File-file konfigurasi untuk linting, formatting kode, konfigurasi NestJS CLI, konfigurasi package manager (npm), dan konfigurasi TypeScript compiler.
## 1. Instalasi NestJS
```bash
npm install -g @nestjs/cli //install NestJs CLI secara Global
nest new labBackend //Buat Proyek NestJS baru
cd labBackend
npm run start:dev //jalankan aplikasi
```

Anda dapat mengakses aplikasi di browser pada alamat yang tertera
```https://localhost:3000```

*   **`integrasi Swagger (OpenApi) untuk Dokumentasi API`**: Swagger (OpenAPI) adalah kerangka kerja populer untuk mendeskripsikan dan mendokumentasikan API REST. NestJS memiliki modul khusus untuk integrasi Swagger, yang memungkinkan Anda menghasilkan dokumentasi API secara otomatis berdasarkan kode Anda.

    [Image of node_modules folder in file explorer]
```Bash
npm install @nestjs/swagger swagger-ui-express  //install paket Swagger

    Konfigurasi SwaggerModule di main.ts
```src/main.ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import { SwaggerModule, DocumentBuilder } from '@nestjs/swagger';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  const config = new DocumentBuilder()
    .setTitle('Belajar NestJS API')
    .setDescription('Dokumentasi API untuk aplikasi Belajar NestJS')
    .setVersion('1.0')
    .addTag('belajar-nestjs')
    .build();
  const document = SwaggerModule.createDocument(app, config);
  SwaggerModule.setup('misba', app, document); // path untuk akses Swagger UI

  await app.listen(3000);
}
bootstrap();
```


## 2. Controller dan Service

Dalam arsitektur NestJS, Controller bertanggung jawab untuk menangani permintaan HTTP dan Service bertanggung jawab untuk logika bisnis.

*   **Controller**: Biasanya memiliki akhiran `*.controller.ts` dan terletak di dalam direktori fitur (seperti `profile`, `auth`, `chat`, `app`).

    [Image of controller files in file explorer]

    Cuplikan gambar di atas menunjukkan beberapa file controller seperti `profile.controller.ts`, `app.controller.ts`, `auth.controller.ts`, `chat.gateway.ts`, dan `sprofile.controller.ts`. Controller ini bertugas untuk menerima permintaan dari klien dan meneruskannya ke service.

*   **Service**: Biasanya memiliki akhiran `*.service.ts` dan terletak di direktori yang sama dengan controller atau dalam direktori `services` di dalam fitur.

    [Image of service files in file explorer]

    Cuplikan gambar di atas menunjukkan file service seperti `prisma.service.ts`, `chat.service.ts`, `sprofile.service.ts`, `app.service.ts`, `auth.service.ts`, dan `profileservicespe.ts` (kemungkinan typo, seharusnya `profile.service.spec.ts` atau `profile.service.ts`). Service ini berisi logika bisnis aplikasi dan dipanggil oleh controller.

## 3. Module

Module dalam NestJS digunakan untuk mengorganisir komponen-komponen aplikasi. Biasanya memiliki akhiran `*.module.ts`.

*   **Module**: Terlihat beberapa file module seperti `prisma.module.ts`, `chat.module.ts`, `profile.module.ts`, `auth.module.ts`, `app.module.ts`, `sprofile.module.ts`, dan `sapp.module.ts`. `app.module.ts` adalah module utama aplikasi.

    [Image of module files in file explorer]

    Cuplikan gambar di atas menunjukkan berbagai file module. Module ini berfungsi sebagai wadah untuk mengelompokkan controller, service, dan komponen lain yang terkait. `app.module.ts` adalah module akar aplikasi NestJS.

    

## 4. Prisma JS

Prisma adalah ORM (Object-Relational Mapper) yang populer digunakan dengan NestJS.

*   **Prisma**: Direktori `prisma` dan file terkait seperti `schema.prisma`, `prisma.service.ts`, `prisma.module.ts`, dan `prisma.ts`. `schema.prisma` berisi definisi skema database Prisma. `prisma.service.ts` dan `prisma.module.ts` kemungkinan menyediakan integrasi Prisma ke dalam NestJS. `prisma.ts` kemungkinan berisi konfigurasi atau instance Prisma Client.

    [Image of prisma folder and related files in file explorer]

    Direktori dan file-file yang terkait dengan Prisma ini menunjukkan penggunaan Prisma sebagai ORM dalam proyek. `schema.prisma` mendefinisikan struktur database, dan file lainnya mengintegrasikan Prisma dengan aplikasi NestJS.

## 5. Authentication

Authentication (Otentikasi) adalah proses verifikasi identitas pengguna.

*   **Auth**: Direktori `auth` dan file-file seperti `auth.controller.ts`, `auth.guard.ts`, `auth.module.ts`, dan `authservicets` (kemungkinan typo, seharusnya `auth.service.ts`). Ini menunjukkan implementasi otentikasi di dalam proyek. `auth.guard.ts` mengindikasikan penggunaan Guard untuk otorisasi.

    [Image of auth folder and related files in file explorer]

    Direktori dan file-file `auth` menunjukkan implementasi fitur otentikasi dalam aplikasi. `auth.guard.ts` kemungkinan berisi implementasi Guard untuk melindungi rute yang memerlukan otentikasi.


## 6. Middleware, Guard, dan Decorator

Komponen-komponen ini digunakan untuk menangani permintaan dan respons secara global atau spesifik.

*   **Guard**: `auth.guard.ts` (seperti dijelaskan di atas) adalah contoh Guard. Guard digunakan untuk otorisasi dan dijalankan setelah middleware tetapi sebelum interceptor atau pipe.

    [Image of auth.guard.ts in file explorer]

    `auth.guard.ts` adalah contoh Guard yang kemungkinan digunakan untuk mengamankan rute aplikasi dan memastikan hanya pengguna yang terotentikasi yang dapat mengaksesnya.

*   **Decorator**: `user.decorator.ts`. Decorator digunakan untuk menambahkan metadata ke class, method, atau properti. `user.decorator.ts` kemungkinan berisi decorator khusus yang terkait dengan pengguna (misalnya untuk mengambil informasi pengguna dari request).

    [Image of user.decorator.ts in file explorer]

    `user.decorator.ts` kemungkinan berisi decorator custom yang berhubungan dengan entitas User, misalnya untuk mengambil data user dari token otentikasi.

*   **Middleware**: Tidak terlihat file middleware secara eksplisit dalam struktur folder berdasarkan nama file. Middleware biasanya diterapkan secara global di `app.module.ts` atau module tertentu. Middleware digunakan untuk memproses request sebelum mencapai handler rute (controller).

    Meskipun tidak ada file middleware yang terlihat secara eksplisit, middleware bisa saja diimplementasikan dalam service atau controller atau di-register dalam module (`app.module.ts` atau module fitur).

## 7. File Uploader dan File Getter

Untuk menangani unggah dan pengambilan file.

*   **Uploads**: Direktori `uploads`. Direktori ini kemungkinan digunakan untuk menyimpan file yang diunggah oleh pengguna.

    [Image of uploads folder in file explorer]

    Direktori `uploads` kemungkinan besar digunakan sebagai tempat penyimpanan file-file yang diunggah oleh pengguna aplikasi.

*   **File Uploader/Getter Logic**: Tidak terlihat file khusus yang secara eksplisit bernama file uploader atau file getter berdasarkan nama file. Logika untuk upload dan get file kemungkinan diimplementasikan dalam service atau controller, mungkin di dalam module `profile` atau `app`.

    Implementasi logika untuk upload dan get file kemungkinan berada di dalam controller atau service yang terkait, dan tidak terlihat file terpisah dengan nama yang jelas untuk fitur ini berdasarkan struktur folder yang diberikan.

## 8. Query Search

Untuk implementasi pencarian data.

*   **Query Search**: Tidak terlihat implementasi query search secara eksplisit sebagai folder atau file terpisah berdasarkan nama file. Fitur pencarian kemungkinan diimplementasikan dalam service atau controller, dan parameter query ditangani langsung dalam method handler atau service.

    Implementasi query search kemungkinan besar diimplementasikan di dalam service atau controller yang relevan, tanpa folder atau file khusus yang dinamakan "query search" secara eksplisit. Logika pencarian akan ditangani dalam method service atau controller.

## 9. Web Socket

Untuk komunikasi real-time menggunakan Web Socket.

*   **Web Socket**: Direktori `chat` dan file-file seperti `chat.gateway.spec.ts`, `chat.gateway.ts`, `chat.module.ts`, dan `chat.service.ts`. `chat.gateway.ts` adalah indikator kuat implementasi Web Socket menggunakan NestJS Gateway.

    [Image of chat folder and related files in file explorer]

    Direktori dan file-file `chat` menunjukkan implementasi fitur Web Socket. `chat.gateway.ts` adalah komponen utama dalam NestJS untuk menangani koneksi dan pesan Web Socket.

    
