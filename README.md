# QEMU-KVM-Linux
untuk membangun sebuah SOC Lab, kita memerlukan beberapa komputer, entah itu sebagai server, client, maupun mesin pentest. sedangkan menggunakan hardware komputer asli memerlukan biaya yang tidak sedikit dan akan sangat ribet, oleh karena itu kita memerlukan mesin virtual sebagai pengganti mesin fisik/hardware.<br />
### KVM (Karnel-based Virtual Machine)
untuk menjawab kebutuhan virtualisasi maka dipilihlah `KVM (Karnel-based Virtual Machine)`, KVM diciptakan pada pertengahan 2006 oleh Avi Kivity di Qumranet company yaitu sebuah perusahaan yang menangani bab teknologi yang diakuisisi oleh Red Hat pada 2008, KVM muncul pada Oktober 2006 dan digabungkan ke dalam jalur utama kernel Linux di kernel versi 2.6. 20, yang dirilis pada 5 Februari 2007. KVM dikelola oleh Paolo Bonzini.
### Installasi
ditahap installasi saya menggunakan OS Linux Ubuntu 20.04 LTS (focal fossa), teman-teman juga bisa menggunakan versi OS linux lainnya, seperti Debian, Kali dan lain-lain. disini saya akan melakukan installasi dengan metode GUI. sebelum masuk ke tahap installasi silakan check `Hardware support virtualization` pada terminal, jangan lupa menggunakan mode super user `sudo su`.
```bash
# egrep -c '(vmx|svm)' /proc/cpuinfo
8
```
pada keterangan diatas, CPU saya mendukung virtualisasi tersedia diBIOS dengan maks virtualisasi 8 mesin. jika output pada perintah diatas adalah "0" pada sayang, CPU teman-teman tidak mendukung virtualsasi. saya anggap CPU teman-teman mendukung virtualisasi, jadi lanjut dengan perintah.
```bash
# kvm ok
INFO: /dev/kvm exist
KVM acceleration can be used
```
Sekarang kita akan menginstall KVM package, sebelumnya update repository kalian.
```bash
# apt-get update
```
lalu install beberapa package dibawah ;
```bash 
# apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils -y
```
jika diminta memasukan konfirmasi ketikan opsi "Y". <br />
<br />
sekarang tambahkan user dari group libvrt dan kvm, dengan perintah
```bash
# adduser 'username' libvirt
# adduser 'username' kvm
```
keterangan 'username' adalah account user yang ada pada /etc/passwd, dan user group pada /etc/group. jika sudah vertifikasi install dengan perintah
```bash 
# virsh list --all
 Id	Name	State
----------------------
```
atau dengan perintah `systemctl` untuk check status dari libvrtd ;
```bash
systemctl status libvrtd
```
next, install virt-manager, dengan perintah ;
```bash
apt-get install virt-manager -y
```
tunggu sampai proses selesai, dan setelahnya jalankan KVM dengan perintah `virt-manager`.


