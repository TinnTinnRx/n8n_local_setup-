# 🐳 คู่มือการติดตั้ง Docker

## 💻 ความต้องการของระบบ

### Windows
| รายการ | ความต้องการขั้นต่ำ |
|--------|-------------------|
| OS | Windows 10 64-bit (Build 19041+) หรือ Windows 11 |
| RAM | 4 GB ขึ้นไป |
| CPU | รองรับ SLAT (Second Level Address Translation) |
| Feature | เปิดใช้งาน WSL 2 หรือ Hyper-V |

### macOS
| รายการ | ความต้องการขั้นต่ำ |
|--------|-------------------|
| OS | macOS 12 (Monterey) ขึ้นไป |
| RAM | 4 GB ขึ้นไป |
| CPU | Intel หรือ Apple Silicon (M1/M2/M3) |

### Linux
| รายการ | ความต้องการขั้นต่ำ |
|--------|-------------------|
| OS | Ubuntu 20.04+, Debian 11+, Fedora 38+, CentOS 7+ |
| RAM | 2 GB ขึ้นไป |
| Kernel | 3.10 ขึ้นไป |

---

##🪟 การติดตั้งบน Windows


**ขั้นตอนที่ 1: เปิดใช้งาน WSL 2**
เปิด **PowerShell** ในโหมด Administrator แล้วรันคำสั่ง:
```powershell
wsl --install

**ขั้นตอนที่ 2: ดาวน์โหลด Docker Desktop**
ไปที่เว็บไซต์ https://www.docker.com/products/docker-desktop
คลิก "Download for Windows"
รอการดาวน์โหลดให้เสร็จสิ้น

**ขั้นตอนที่ 3: ติดตั้ง Docker Desktop**
ดับเบิลคลิกที่ไฟล์ Docker Desktop Installer.exe
เลือก "Use WSL 2 instead of Hyper-V" (แนะนำ)
คลิก "Ok" และรอการติดตั้ง
คลิก "Close and restart" เมื่อติดตั้งเสร็จ

**ขั้นตอนที่ 4: ตั้งค่าหลังติดตั้ง**
เปิด Docker Desktop
ยอมรับ Terms of Service
เลือกแผนการใช้งาน (Personal ใช้ฟรีได้)
รอให้ Docker เริ่มทำงาน (ไอคอนกลายเป็นสีเขียว ✅)
