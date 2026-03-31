**Step 1: สร้าง Tunnel บนเว็บ Cloudflare**
1.เข้าไปที่ Cloudflare Zero Trust Dashboard (https://one.dash.cloudflare.com/)
2. ที่เมนูด้านซ้าย ไปที่ Networks -> Connectors -> Cloudflare Tunnels
3. คลิกปุ่ม Create a tunnel
4. เลือก Cloudflared แล้วคลิก Next
5. ตั้งชื่อ Tunnel ของคุณ (เช่น my-docker-tunnel) แล้วคลิก Save tunnel
6. จะได้ Tunnel ID
7. จากนั้นให้ใช้คำส่ั่ง $cloudflared.exe service install "Your Tunnel ID" ใน Terminal หรือ Window Powershell
8. ใช้คำสั่ง docker run cloudflare/cloudflared:latest tunnel --no-autoupdate run --token "Your Tunnel ID"

**Step 2: สร้างไฟล์ docker-compose.yml**
cloudflared:
    image: cloudflare/cloudflared:latest
    container_name: cloudflared-tunnel
    restart: unless-stopped
    command: tunnel run
    environment:
      # เอา Token ยาวๆ ที่ได้จาก Step 1 มาวางหลังเครื่องหมาย = ด้านล่างนี้ (ไม่ต้องใส่ฟันหนู)
      - TUNNEL_TOKEN=eyJhbGciOiJSUz...ใส่Tokenของคุณที่นี่...

**Step 3: สตาร์ทระบบ (Run Docker)**
docker-compose up -d

**Step 4: ผูกโดเมนเนม (Public Hostname)**
ขั้นตอนนี้คือการบอก Cloudflare ว่า ถ้าคนพิมพ์โดเมนหน้าเว็บ ให้วิ่งเข้ามาที่ Container ไหนในเครื่องเรา
ในหน้าตั้งค่า Tunnel บน Cloudflare (แท็บ Public Hostname) ให้กรอกข้อมูลดังนี้:
  Subdomain: พิมพ์ชื่อข้างหน้า (เช่น portal หรือ app)
  Domain: เลือกโดเมนเนมของคุณ (เช่น yourdomain.com) ตรงนี้จะเป็น Dropdown ให้เลือก
  (รวมกันจะได้ URL เป็น app.yourdomain.com)
  Service Type: เลือก HTTP
  URL: กรอก my-web:80 
  กด Save hostname
