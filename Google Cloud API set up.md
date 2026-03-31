# ☁️ คู่มือการตั้งค่า Google Cloud API และการขอ Client ID / Client Secret

## 📋 ข้อกำหนดเบื้องต้น (Prerequisites)
1. มีบัญชี Google (Gmail หรือ Google Workspace)
2. มีสิทธิ์ในการเข้าถึง [Google Cloud Console](https://console.cloud.google.com/)

---

## ขั้นตอนที่ 1: สร้าง Project ใหม่ (หรือเลือกโปรเจกต์ที่มีอยู่)
1. ไปที่ [Google Cloud Console](https://console.cloud.google.com/)
2. ที่แถบเมนูด้านบน (ข้างโลโก้ Google Cloud) ให้คลิกที่ **Dropdown รายชื่อโปรเจกต์** หรือ สร้างโปรเจกต์
3. คลิกปุ่ม **New Project** (สร้างโปรเจกต์) มุมขวาบนของหน้าต่างป๊อปอัป
4. ตั้งชื่อโปรเจกต์ (Project name) แล้วคลิก **Create** (สร้าง)
5. รอสักครู่ เมื่อสร้างเสร็จให้เลือกโปรเจกต์ที่คุณเพิ่งสร้าง

---

## ขั้นตอนที่ 2: การเปิดใช้งาน API (Enable APIs)
คุณต้องเปิดใช้งาน API ของบริการที่คุณต้องการใช้เสียก่อน (เช่น Google Drive API, YouTube Data API, Cloud Storage เป็นต้น)

1. เปิด **Navigation menu** (ไอคอน ☰ มุมซ้ายบน)
2. ไปที่ **APIs & Services** > **Library**
3. ในช่องค้นหา ให้พิมพ์ชื่อ API ที่โปรเจกต์นี้ต้องการใช้งาน ตัวอย่างเช่น: `<ชื่อ API ที่ต้องการ>`
4. คลิกที่ชื่อ API ในผลการค้นหา
5. คลิกปุ่ม **Enable** (เปิดใช้งาน) สีฟ้า และรอจนกว่าระบบจะดำเนินการเสร็จสิ้น

---

## ขั้นตอนที่ 3: ตั้งค่าหน้าจอขอความยินยอม (OAuth Consent Screen)
*หมายเหตุ: หากคุณยังไม่เคยตั้งค่า Consent Screen ในโปรเจกต์นี้ ระบบจะบังคับให้ทำก่อนสร้าง Client ID*

1. ไปที่เมนู **APIs & Services** > **OAuth consent screen**
2. เลือก **User Type**:
   - เลือก **External** (สำหรับผู้ใช้ทั่วไป มีบัญชี Google ใดๆ ก็ทดสอบได้)
3. คลิก **Create**
4. กรอกข้อมูลที่จำเป็น (ช่องที่มีเครื่องหมาย *):
   - **App name**: ชื่อแอปพลิเคชันของคุณ
   - **User support email**: อีเมลของคุณ
   - **Developer contact information**: อีเมลของคุณ (ด้านล่างสุด)
5. คลิก **Save and Continue** ในหน้า Scopes (ยังไม่ต้องกำหนดก็สได้สำหรับช่วงทดสอบ)
6. ในหน้า **Test users** ให้คลิก **+ ADD USERS** และใส่อีเมล Google ของคุณ (และทีม) ที่จะใช้เพื่อทดสอบล็อกอิน > คลิก **Save and Continue**
7. ตรวจสอบข้อมูลแบบร่างแล้วคลิก **Back to Dashboard**

---

## ขั้นตอนที่ 4: การสร้าง Credentials (ขอ Client ID และ Client Secret)
1. ไปที่เมนู **APIs & Services** > **Credentials**
2. คลิก **+ CREATE CREDENTIALS** (ด้านบน) แล้วเลือก **OAuth client ID**
3. ในช่อง **Application type** ให้เลือกประเภทแอปพลิเคชันของคุณ:
   - *ตัวอย่าง: หากเป็นแอปพลิเคชันบนเว็บไซต์ เลือก **Web application***
   - *ตัวอย่าง: หากเป็นเซิร์ฟเวอร์รันสคริปต์/แอปบนคอมตัวเอง เลือก **Desktop app***
4. ตั้งชื่อ Client ID (เช่น `My Project Web Client`)
5. **(เฉพาะ Web application)** ตั้งค่า URL:
   - **Authorized JavaScript origins**: เช่น `http://localhost:3000` (สำหรับการรันแบบ Local)
   - **Authorized redirect URIs**: เช่น `http://localhost:3000/oauth2callback` (ใส่ตามที่โปรเจกต์คุณกำหนดไว้)
6. คลิก **Create** (สร้าง)

---

## ขั้นตอนที่ 5: การนำ Client ID และ Client Secret ไปใช้งาน
1. เมื่อคลิก Create ระบบจะแสดงหน้าต่าง Popup ที่ประกอบด้วย:
   - **Your Client ID** (รหัสไคลเอ็นต์)
   - **Your Client Secret** (รหัสลับไคลเอ็นต์)
2. คุณสามารถคลิก **DOWNLOAD JSON** เพื่อดาวน์โหลดไฟล์รวมค่าทั้งหมด (มักจะได้ชื่อไฟล์ยาวๆ เช่น `client_secret_xxxx.json`)



