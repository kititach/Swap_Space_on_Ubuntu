# Swap_Space_on_Ubuntu
### ตรวจสอบระบบสำหรับการติดตั้งก่อน
```
sudo swapon --show
```
### ตรวจสอบ Swap ที่ใช้งานอยู่
```
free -h
```
### ตรวจสอบเนื้อที่ว่างที่มีอยู่บนพาร์ติชันฮาร์ดไดรฟ์
```
df -h
```
### สร้างแฟ้ม Swap
```
sudo fallocate -l 4G /swapfile
ls -lh /swapfile
```
### ตรวจสอบว่าสร้างพื้นที่ได้ถูกต้อง
```
ls -lh /swapfile
```
### เปิดการใช้งาน
```
sudo chmod 600 /swapfile
```
### ตรวจสอบการเปลี่ยนแปลงสิทธิ์
```
ls -lh /swapfile
```
### ทำเครื่องหมายไฟล์เป็นพื้นที่สลับ
```
sudo mkswap /swapfile
```
### เปิดใช้งาน Swap
```
sudo swapon /swapfile
```
### ตรวจสอบความพร้อมใช้งานของ Swap
```
sudo swapon /swapfile
```
### ทำให้ Swap ถาวร
```
sudo cp /etc/fstab /etc/fstab.bak
```
### เพิ่มข้อมูลแฟ้ม Swap
```
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```
