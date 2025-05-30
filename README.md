# Advprog Module 11 Tutorial - Deployment on Kubernetes
Hadyan Fachri\
2306245030\
Advprog A

## Reflection on Hello Minikube
**1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?**

![Before exposing as service](./before_expose.png)
Gambar berikut adalah situasi dimana setelah saya menjalankan `kubectl logs` yang mana digunakan untuk melihat log suatu aplikasi sebagai suatu service namun belum terexpose karena belum menjalankan `kubectl expose deployment` ke aplikasi yang ingin di expose.

![Expose as service](./expose.png)
Disini saya menjalankan `kubectl expose deployment` untuk mengekspose aplikasi yang ingin di expose.

![After exposing as service](./after_expose.png)
Gambar berikut aadalah situasi dimana setelah saya menjalankan `minikube service` secara dua kali, terlihat disini bahwa ada 4 baris logs baru yang sebelumnya tidak ada, yaitu logs GET/ yang menandakan aplikasi berhasil dikunjungi dengan menampilkan GET request.

![After exposing as service more](./after_expose_more.png)
Disini saya mencoba menjalankan lagi `minikube service` dan mengunjungi aplikasi sebanyak 2 kali. Yang terjadi adalah logs bertambah sebanyak 4 baris baru. Jadi setiap mengunjungi aplikasi yang sudah diexpose akan menampilkan 2 baris logs GET/ setiap 1 kali kunjungan.

**2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. 13The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created?**

Opsi `-n` pada perintah `kubectl get` digunakan untuk menentukan namespace spesifik tempat objek Kubernetes (seperti Pod atau Service) akan dicari. Namespace dalam Kubernetes bisa diibaratkan seperti direktori atau folder terpisah yang menyimpan sumber daya tertentu. Dengan menyertakan `-n <nama-namespace>`, kita memberitahu `kubectl` untuk hanya menampilkan objek dari namespace tersebut. Jika opsi -n tidak disebutkan, maka `kubectl` akan secara otomatis menggunakan namespace `default`. Itulah sebabnya objek yang dibuat dalam namespace default tidak muncul saat kita menjalankan perintah dengan `-n kube-system`, karena keduanya berada di namespace yang berbeda.