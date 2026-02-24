# 🐳 Laporan Praktikum Pertemuan 02
## Docker Fundamentals

---

## 👤 Identitas Mahasiswa

| Item | Keterangan |
|------|------------|
| **Nama** | DEVI NIRWANA |
| **NIM** | 105841121023 |
| **Kelas** | 5B |
| **Tanggal** | 2026-02-24 |

---

## 📚 Pemahaman Docker

### Apa itu Docker?

Docker itu adalah alat yang membantu kita menjalankan aplikasi dengan cara yang lebih rapi dan aman. Docker bekerja dengan membuat sebuah “wadah” kecil yang disebut container. Di dalam container itu sudah ada semua kebutuhan aplikasi, seperti sistem, library, dan pengaturan lainnya. Jadi aplikasi bisa berjalan dengan baik tanpa terganggu oleh aplikasi lain di komputer.
Dengan Docker, kita tidak perlu pusing soal perbedaan sistem atau konfigurasi. Aplikasi yang berjalan di satu komputer bisa berjalan sama persis di komputer lain. Jadi Docker itu seperti tempat khusus yang menjaga aplikasi supaya tetap stabil, konsisten, dan mudah dipindahkan.

### Komponen Utama Docker

1. Docker Images : Docker Image adalah “template” atau cetakan untuk membuat container.
Di dalam image sudah ada aplikasi, sistem operasi, library, dan semua konfigurasi yang dibutuhkan agar aplikasi bisa berjalan.
Image bersifat read-only (tidak berubah). Jadi kalau kita ingin menjalankan aplikasi, kita tidak langsung memakai image, tetapi membuat container dari image tersebut.
2. Docker Containers : Docker Container adalah hasil dari image yang dijalankan. Container merupakan lingkungan terisolasi tempat aplikasi benar-benar berjalan. Container bersifat ringan, cepat dibuat, dan dapat dijalankan, dihentikan, atau dihapus dengan mudah tanpa memengaruhi sistem utama.
3. Docker Registry : Docker Registry adalah tempat penyimpanan image Docker. Registry bisa bersifat publik maupun privat. Salah satu registry yang paling umum digunakan adalah Docker Hub, yang memungkinkan pengguna menyimpan, membagikan, serta mengunduh image sesuai kebutuhan.

### Perbedaan Docker vs Virtual Machine

Perbedaan utama antara Docker Container dan Virtual Machine (VM) terletak pada cara kerja dan penggunaan sumber daya sistem.
Docker Container berjalan langsung di atas sistem operasi host dengan bantuan Docker Engine. Container berbagi kernel sistem operasi yang sama, sehingga ukurannya lebih ringan, proses startup lebih cepat, dan penggunaan resource (RAM serta CPU) lebih efisien. Container hanya membawa aplikasi beserta dependensinya tanpa harus membawa sistem operasi lengkap.
Sedangkan Virtual Machine (VM) berjalan di atas hypervisor dan setiap VM memiliki sistem operasi sendiri (guest OS). Karena setiap VM membawa OS lengkap, ukurannya lebih besar dan membutuhkan resource yang lebih banyak. Proses menjalankannya juga lebih lambat dibanding container.
Contoh platform yang sering digunakan untuk menjalankan VM adalah Oracle VM VirtualBox dan VMware Workstation.
Jadi, secara sederhana:
Container lebih ringan dan cepat, sedangkan VM lebih berat tetapi memberikan isolasi sistem yang lebih penuh.

---

## 🔧 Praktik Docker Commands

### Output docker ps -a

```
PS D:\ドキュメント\LAB-RPL 5\105841121023_Devi Nirwana_Pertemuan02\task2-dockerfile\praktikum-docker> docker ps -a
CONTAINER ID   IMAGE                               COMMAND                   CREATED          STATUS                     PORTS                                     NAMES
c7a48f1e5771   praktikum-docker:v1                 "/docker-entrypoint.…"    4 minutes ago    Created                                                              praktikum-web
cbec9a1062ed   nginx:alpine                        "/docker-entrypoint.…"    34 minutes ago   Up 34 minutes              0.0.0.0:8081->80/tcp, [::]:8081->80/tcp   web-praktikum
cc8665171568   hello-world                         "/hello"                  3 hours ago      Exited (0) 3 hours ago                                               sweet_lalande
d8577785680a   hello-world                         "/hello"                  3 hours ago      Exited (0) 3 hours ago                                               zen_solomon
0bc1f500921e   341bf0f3ce6c                        "/docker-entrypoint.…"    5 hours ago      Up 5 hours                                                           k8s_nginx_nginx-with-label_default_2227408b-fb43-47ee-8e5e-75fdb427fdef_4
b331c2be1c65   341bf0f3ce6c                        "/docker-entrypoint.…"    5 hours ago      Up 5 hours                                                           k8s_nginx_pod-name_default_5ff05f0e-454d-45e7-a8ad-e60af8bb7f56_5
96d5e0ee3a44   devina22/multi                      "/bin/sh -c /app/main"    6 weeks ago      Exited (2) 6 weeks ago                                               multi
be75f71019ef   devina22/entrypoint                 "go run /app/main.go"     6 weeks ago      Exited (2) 6 weeks ago                                               entrypoint
cc6d6725888d   devina22/health                     "sh -c 'go run app/m…"    6 weeks ago      Exited (2) 6 weeks ago                                               health
935e30f5a56c   devina22/user                       "/bin/sh -c 'go run …"    6 weeks ago      Exited (2) 6 weeks ago                                               user
6f2ece8bfef1   devina22/workdir                    "go run main.go"          6 weeks ago      Exited (2) 6 weeks ago                                               workdir
193db9cfc247   devina22/volume                     "/bin/sh -c 'go run …"    6 weeks ago      Exited (2) 6 weeks ago                                               volume
e26c9457c3aa   devina22/env                        "/bin/sh -c 'go run …"    6 weeks ago      Exited (2) 6 weeks ago                                               env
a5a55a943218   devina22/expose                     "/bin/sh -c 'go run …"    6 weeks ago      Exited (2) 6 weeks ago                                               expose
48f20a66b854   devina22/ignore                     "/bin/sh -c 'ls -l h…"    6 weeks ago      Exited (0) 6 weeks ago                                               ignore
b6a7bff923be   devina22/copy                       "/bin/sh -c 'cat \"he…"   6 weeks ago      Exited (0) 6 weeks ago                                               copy
1bbc42e10bac   74f706144a56                        "/bin/sh -c 'cat \"he…"   6 weeks ago      Exited (0) 6 weeks ago                                               add
d2bdf68931c6   devina22/command                    "cat hello/word.txt"      6 weeks ago      Exited (0) 6 weeks ago                                               command
6d0776bcdad5   43e5b5730ee8                        "/bin/sh"                 7 weeks ago      Exited (0) 6 weeks ago                                               sharp_ride
e8e2a1aee852   calendar-service-api-gateway        "docker-entrypoint.s…"    2 months ago     Exited (255) 6 weeks ago   0.0.0.0:3000->3000/tcp                    calendar-service-api-gateway-1
f49fa3757b8c   calendar-service-calendar-service   "docker-entrypoint.s…"    2 months ago     Exited (255) 6 weeks ago   0.0.0.0:3003->3003/tcp                    calendar-service-calendar-service-1
4cc77daa8b74   calendar-service-jadwal-service     "docker-entrypoint.s…"    2 months ago     Exited (255) 6 weeks ago   0.0.0.0:3002->3002/tcp                    calendar-service-jadwal-service-1
248b250e7d08   calendar-service-course-service     "docker-entrypoint.s…"    2 months ago     Exited (255) 6 weeks ago   0.0.0.0:3001->3001/tcp                    calendar-service-course-service-1
4738bbddb449   confluentinc/cp-kafka:7.6.1         "/etc/confluent/dock…"    2 months ago     Exited (1) 7 weeks ago                                               calendar-service-kafka-1   
80d7f718004d   mysql:8.0                           "docker-entrypoint.s…"    2 months ago     Exited (255) 6 weeks ago   33060/tcp, 0.0.0.0:33063->3306/tcp        calendar-service-mysql_calendar-1
e80d0b4d20c3   mysql:8.0                           "docker-entrypoint.s…"    2 months ago     Exited (255) 6 weeks ago   33060/tcp, 0.0.0.0:33062->3306/tcp        calendar-service-mysql_jadw0bc1f500921e   341bf0f3ce6c   "/docker-entrypoint.…"   5 hours ago      Up 5 hours                                                k8s_nginx_nginx-with-label_default_2227408b-fb43-47ee-8e5e-75fdb427fdef_4
b331c2be1c65   341bf0f3ce6c   "/docker-entrypoint.…"   5 hours ago      Up 5 hours                                                k8s_nginx_pod-name_default_5ff05f0e-454d-45e7-a8ad-e60af8bb7f56_5
```

### Output docker images

```
PS D:\ドキュメント\LAB-RPL 5\105841121023_Devi Nirwana_Pertemuan02\task2-dockerfile\praktikum-docker> docker images
                                                                                                                                               i Info →   U  In Use
IMAGE                                                                                                   ID             DISK USAGE   CONTENT SIZE   EXTRA
calendar-service-api-gateway:latest                                                                     6c813e13f6c1        217MB         50.5MB    U 
calendar-service-calendar-service:latest                                                                ba0733437ee2        200MB         48.3MB    U 
calendar-service-course-service:latest                                                                  895a4e205e62        200MB         48.3MB    U 
calendar-service-jadwal-service:latest                                                                  36ef831408c0        202MB         48.6MB    U 
confluentinc/cp-kafka:7.6.1                                                                             620734d9fc0b        1.3GB          453MB    U 
confluentinc/cp-zookeeper:7.6.1                                                                         4dc780642bfc        1.3GB          453MB    U 
devina22/add:latest                                                                                     36edba4607e9         13MB         3.86MB    U   
devina22/arg:latest                                                                                     a54633e86e5a        489MB          119MB
devina22/command:latest                                                                                 91dda0544854         13MB         3.86MB    U 
devina22/copy:latest                                                                                    0ccba7842cda         13MB         3.86MB    U 
devina22/entrypoint:latest                                                                              670698df6744        489MB          119MB    U 
devina22/env:latest                                                                                     4f1ea868bd35        489MB          119MB    U 
devina22/expose:latest                                                                                  f79e9c5376da        489MB          119MB    U 
devina22/from:latest                                                                                    888c5ece805c         13MB         3.86MB    U 
devina22/health:latest                                                                                  2c06d1671e66        492MB          120MB    U 
devina22/ignore:latest                                                                                  556129f65908         13MB         3.86MB    U 
devina22/label:latest                                                                                   2f4699c83a21         13MB         3.86MB
devina22/multi:latest                                                                                   9868530ed6b0       22.9MB         7.45MB    U 
devina22/run:latest                                                                                     6b825af840cc         13MB         3.86MB
devina22/user:latest                                                                                    33bfed4e37bc        489MB          119MB    U 
devina22/volume:latest                                                                                  bec2014bb98c        489MB          119MB    U 
devina22/workdir:latest                                                                                 09b82fd29b75        489MB          119MB    U 
docker/desktop-kubernetes:kubernetes-v1.34.1-cni-v1.7.1-critools-v1.33.0-cri-dockerd-v0.3.20-1-debian   12d6673564e0        592MB          185MB
docker/desktop-storage-provisioner:v2.0                                                                 115d77efe6e2       59.2MB         17.3MB    U 
docker/desktop-vpnkit-controller:dc331cb22850be0cdd97c84a9cfecaf44a1afb6e                               7ecf567ea070         47MB         10.8MB    U 
hello-world:latest                                                                                      ef54e839ef54       25.9kB         9.52kB    U 
mysql:8.0                                                                                               0275a35e79c6       1.08GB          247MB    U 
nginx:alpine                                                                                            1d13701a5f9f       93.4MB         26.9MB    U 
nginx:latest                                                                                            341bf0f3ce6c        240MB         65.8MB    U 
nginx:trixie-perl                                                                                       b60f25eb5acd        310MB         79.3MB
praktikum-docker:v1                                                                                     b90f0725d57e       92.5MB           26MB    U 
registry.k8s.io/coredns/coredns:v1.12.1                                                                 e8c262566636        101MB         22.4MB    U 
registry.k8s.io/etcd:3.6.4-0                                                                            e36c08168342        273MB         74.3MB    U 
registry.k8s.io/kube-apiserver:v1.34.1                                                                  b9d7c117f8ac        118MB         27.1MB    U 
registry.k8s.io/kube-controller-manager:v1.34.1                                                         2bf47c1b01f5        101MB         22.8MB    U 
registry.k8s.io/kube-proxy:v1.34.1                                                                      913cc83ca0b5        102MB           26MB    U 
registry.k8s.io/kube-scheduler:v1.34.1                                                                  6e9fbc4e25a5       73.5MB         17.4MB    U 
registry.k8s.io/pause:3.10                                                                              ee6521f290b2       1.06MB          318kB    U 
registry.k8s.io/pause:3.10.1                                                                          docker run -d -p 8080:80 --name praktikum-web praktikum-docker:v1
```

### Docker Run Command

```bash
 docker run -d -p 8080:80 --name praktikum-web praktikum-docker:v1
```

---

## 📄 Dockerfile

### Isi Dockerfile

```dockerfile
# Gunakan nginx alpine sebagai base image
FROM nginx:alpine

# Copy file HTML ke direktori nginx
COPY app/index.html /usr/share/nginx/html/index.html

# Expose port 80
EXPOSE 80

# Command default nginx
CMD ["nginx", "-g", "daemon off;"]
```

### Penjelasan Dockerfile

FROM nginx:alpine
Menentukan base image untuk container, yaitu Nginx versi Alpine Linux. Alpine adalah distribusi Linux yang sangat ringan, sehingga image yang dihasilkan kecil, cepat diunduh, dan minim risiko keamanan karena hanya menyertakan paket yang penting.

COPY app/index.html /usr/share/nginx/html/index.html
Menyalin file index.html dari folder lokal app ke direktori default Nginx di container, /usr/share/nginx/html/. Dengan begitu, ketika container dijalankan, Nginx akan menampilkan file HTML ini sebagai halaman utama web.

EXPOSE 80
Memberi tahu Docker bahwa container akan menggunakan port 80, yaitu port standar untuk HTTP. Meskipun tidak membuka port secara otomatis di host, ini berguna untuk dokumentasi dan mempermudah pemetaan port saat menjalankan container.

CMD ["nginx", "-g", "daemon off;"]
Menetapkan perintah default yang dijalankan saat container dijalankan. Perintah nginx -g "daemon off;" membuat Nginx berjalan di foreground, sehingga container tetap aktif. Tanpa ini, Nginx akan berjalan sebagai daemon dan container akan langsung berhenti karena proses utama selesai.

---

## 🐙 Docker Compose

### Isi docker-compose.yml

```yaml
version: '3.8'

services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./app:/usr/share/nginx/html:ro
    depends_on:
      - api
    networks:
      - praktikum-net

  api:
    image: httpd:alpine
    ports:
      - "8081:80"
    networks:
      - praktikum-net

  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_USER: praktikum
      POSTGRES_PASSWORD: devops123
      POSTGRES_DB: praktikum_db
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - praktikum-net

networks:
  praktikum-net:
    driver: bridge

volumes:
  db_data:
```

### Penjelasan Docker Compose

Di bagian services, terdapat tiga layanan: web, api, dan db. Layanan web menggunakan image nginx:alpine dan memetakan port 80 di container ke port 8080 di host, sehingga website dapat diakses melalui localhost:8080. Direktori lokal ./app di-mount ke /usr/share/nginx/html di container dengan mode ro (read-only), sehingga file HTML dapat dibaca oleh Nginx tetapi tidak bisa diubah dari container. Layanan web juga tergantung pada api (depends_on), sehingga Docker akan menjalankan api lebih dulu, dan kedua layanan ini berada di jaringan praktikum-net.

Layanan api menggunakan image httpd:alpine untuk menjalankan server Apache HTTP sederhana, dengan port 80 di container dipetakan ke port 8081 di host. api juga terhubung ke jaringan praktikum-net, sehingga dapat berkomunikasi dengan layanan lain di jaringan yang sama.

Layanan db menggunakan image postgres:15-alpine untuk menjalankan database PostgreSQL. Variabel lingkungan seperti POSTGRES_USER, POSTGRES_PASSWORD, dan POSTGRES_DB digunakan untuk mengatur kredensial awal dan nama database. Data disimpan secara persisten melalui volume db_data, yang di-mount ke /var/lib/postgresql/data di container, sehingga data tidak hilang saat container dihentikan.

Bagian networks mendefinisikan jaringan bernama praktikum-net dengan driver bridge, memungkinkan semua layanan saling terhubung dalam jaringan internal yang sama. Bagian volumes mendefinisikan volume db_data untuk penyimpanan data PostgreSQL secara persisten di host.

### Output Docker Compose Up

```
Belum diisi
```

---

## 📸 Screenshots

| No | Screenshot | Keterangan |
|----|------------|------------|
| 1 | ![Container Running](screenshots/01-container-running.png) | Container yang sedang berjalan |
| 2 | ![Docker Images](screenshots/02-docker-images.png) | Daftar Docker images |
| 3 | ![Dockerfile](screenshots/03-dockerfile-content.png) | Isi file Dockerfile |
| 4 | ![Docker Build](screenshots/04-docker-build.png) | Proses docker build |
| 5 | ![App Browser](screenshots/05-app-browser.png) | Aplikasi berjalan di browser |
| 6 | ![Compose Up](screenshots/06-compose-up.png) | Docker Compose up |

---

## 💭 Refleksi & Kesimpulan

### Yang Dipelajari

Dari praktikum ini, saya belajar cara menjalankan beberapa layanan sekaligus menggunakan Docker Compose, seperti web, API, dan database, serta bagaimana mereka saling terhubung lewat jaringan internal dan menyimpan data secara permanen.

Saya juga memahami pentingnya mapping port agar layanan bisa diakses dari host, penggunaan volume untuk menghubungkan file lokal ke container, dan membedakan antara warning yang bisa diabaikan dengan error yang kritis.
Praktikum ini memberi pengalaman langsung tentang containerization, bagaimana layanan berjalan terisolasi tapi tetap bisa saling berkomunikasi, serta memudahkan pengaturan lingkungan development dibanding instalasi manual. Secara keseluruhan, ini sangat berguna untuk proyek nyata di masa depan.

### Manfaat Docker

Docker membantu pengembangan software dengan cara membuat setiap aplikasi berjalan di dalam container yang terisolasi, sehingga lingkungan setiap proyek tidak saling bertabrakan. Hal ini membuat aplikasi bisa dijalankan konsisten di komputer manapun, cepat, dan lebih ringan dibanding mesin virtual. Dengan Docker, banyak layanan seperti web, API, dan database bisa dijalankan sekaligus, mudah diatur, dan siap dipindahkan dari development ke production tanpa konfigurasi ulang. Secara keseluruhan, Docker mempermudah pengembangan, pengujian, dan penyebaran software secara efisien.

### Tantangan dan Solusi

Beberapa tantangan yang sering dihadapi saat menggunakan Docker antara lain memahami konsep container dan cara kerjanya, mengatur jaringan antar container agar layanan bisa saling terhubung, serta mengelola penyimpanan data agar tidak hilang saat container dihentikan. Selain itu, kadang muncul error atau warning yang membingungkan, seperti Apache yang tidak mengenali nama server. Solusinya adalah mempelajari dokumentasi Docker secara bertahap, menggunakan Docker Compose untuk mengatur beberapa layanan sekaligus, memanfaatkan volume untuk menyimpan data secara persisten, serta belajar membedakan mana error yang kritis dan warning yang bisa diabaikan. Dengan pendekatan ini, tantangan dapat diatasi dan penggunaan Docker menjadi lebih lancar.

---

## ✅ Checklist

- [x] Berhasil membuat Dockerfile yang valid
- [x] Berhasil build Docker image
- [x] Container berjalan dan aplikasi bisa diakses
- [x] Docker Compose berhasil dijalankan
- [x] Semua screenshot lengkap dan jelas
- [x] Penjelasan ditulis dengan bahasa sendiri

---

*Laporan ini dibuat pada Rabu, 25 Februari 2026*
