# Swap_Space_On_Ubuntu
### ตรวจสอบระบบสำหรับการติดตั้งก่อน
```
sudo swapon --show
```
### ตรวจสอบ Swap ที่ใช้งานอยู่
```
free -h
```
![1](https://user-images.githubusercontent.com/48780839/169758129-38a37732-7dae-4051-a79f-c57a3130b991.png)
### ตรวจสอบเนื้อที่ว่างที่มีอยู่บนพาร์ติชันฮาร์ดไดรฟ์
```
df -h
```
![2](https://user-images.githubusercontent.com/48780839/169758526-ec1861d2-a5d5-4910-8649-516a33cd6859.png)
### สร้างแฟ้ม Swap
```
sudo fallocate -l 4G /swapfile
```
### ตรวจสอบว่าสร้างพื้นที่ได้ถูกต้อง
```
ls -lh /swapfile
```
![3](https://user-images.githubusercontent.com/48780839/169758679-75d96d23-d011-4bac-8e06-63943d2aabbc.png)
### เปิดการใช้งาน
```
sudo chmod 600 /swapfile
```
### ตรวจสอบการเปลี่ยนแปลงสิทธิ์
```
ls -lh /swapfile
```
![4](https://user-images.githubusercontent.com/48780839/169759429-0d183996-13c3-4e90-aadd-3376fb171629.png)
### ทำเครื่องหมายไฟล์เป็นพื้นที่สลับ
```
sudo mkswap /swapfile
```
![5](https://user-images.githubusercontent.com/48780839/169759702-c9132f36-9347-4d0d-95d1-39639528795b.png)
### เปิดใช้งาน Swap
```
sudo swapon /swapfile
```
### ตรวจสอบความพร้อมใช้งานของ Swap
```
sudo swapon --show
```
![6](https://user-images.githubusercontent.com/48780839/169759893-081897d2-b3af-4860-ba4c-3d3df7fffe53.png)
### ตรวจสอบ Swap ที่ใช้งานอยู่
```
free -h
```
![7](https://user-images.githubusercontent.com/48780839/169760041-725b51c0-402a-4b45-88b8-e1f21fc2ca03.png)
### เนื่องจากการตั้งค่าด้านบน เมื่อ Reboot การตั้งค่าที่ทำไว้จะหาย การทำให้ Swap ถาวร
### สํารองไฟล์ในกรณีที่มีอะไรผิดพลาด :/etc/fstab
```
sudo cp /etc/fstab /etc/fstab.bak
```
### เพิ่มข้อมูลแฟ้ม Swap ส่วนท้ายของแฟ้ม :/etc/fstab
```
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```
