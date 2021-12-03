# DOCKER-REGISTRY
### **disclaimer !** </br>
REPOSITORY ini merupakan murni didapatkan dari dokumentasi resmi dari [docker hub](docs.docker.com).
step:
1. Pastikan Anda masuk ke dalam repository docker-registry untuk dapat dieksekusi. Jika tidak ingin menggunakan autentikasi atau private ssl/certifate, dapat di comment(#) aja pada docker-compose di bagian Environment.
2. buat own certificate-mu sendiri dalam local laptopmu, link setting di bagian [Get My Own Certificate](https://docs.docker.com/registry/deploying/#run-an-externally-accessible-registry), </br> step ini merupakan syarat untuk dapat melakukan autentikasi menggunakan`htpasswd` 
3. Buat autentikasi dengan `htpasswd` di bagian [Basic Auth htpasswd](https://docs.docker.com/registry/deploying/#native-basic-auth) dengan  syntax: </br>
  `docker run --entrypoint htpasswd httpd:2 -Bbn "<username-cutomize>" "<password-customze>" > auth/htpasswd` </br>
   Hal tersebut secara otomatis akan ngebuat file `htpasswd` pada directory `auth/htpasswd`. ingat-ingat username sama passwordnya. 
4. Kalau sudah, baru jalankan `docker-compose up -d` untuk ngejalanin Container nya.  </br>
**Congrats !! Anda sudah berhasil ngejalanin docker registry Anda Sendiri !!!** </br> </br>

untuk cek coba kalian masuk ke terminal dan lakukan login:
1. `docker login "<nama-url/domain:port>"`
2. masukkan username dan password sesuai yang sudah digenerate di htpasswd sebelumnya.
3. selesai, Anda dapat nge-push, nge-pull pada private registry anda !

## NB
1. Anda juga dapat menggunakan docker-registry-ui, link [docker registry- ui](https://hub.docker.com/r/konradkleine/docker-registry-frontend), tinggal uncomment saja pada service docker-registry-ui di basefile docker-compose.yml.

## REFERENSI :
1. Deploying Private Docker Registry: https://docs.docker.com/registry/deploying/#run-an-externally-accessible-registry
2. How to deploy Registry Video: https://www.youtube.com/watch?v=8gEs_zefNYA
3. Docker image for docker registry-ui: https://hub.docker.com/r/konradkleine/docker-registry-frontend
4. Authencticating with Nginx: https://docs.docker.com/registry/recipes/nginx/
