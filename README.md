# ระบบลงเวลาทำงานพนักงาน (Employee Timesheet App)

แอปพลิเคชันสำหรับจัดการระบบลงเวลาทำงานของพนักงาน พร้อมระบบคำนวณเงินเดือนอัตโนมัติ

## คุณสมบัติหลัก

### โหมดหน้าบ้าน (Public Mode)
- ✅ ตารางลงเวลา 31 วัน (วันที่ 16 เดือนปัจจุบัน ถึง วันที่ 15 เดือนถัดไป)
- ✅ เลือกเดือน/ปี ได้
- ✅ ค้นหาพนักงาน (ชื่อ, สกุล, รหัสพนักงาน)
- ✅ แสดงสถานะการเข้าทำงาน: N (สีเขียว) = มาทำงาน, F (สีแดง) = ไม่มาทำงาน
- ✅ ดูสรุปรายได้ของแต่ละพนักงาน

### โหมด Admin (รหัสผ่าน: admin)
- ✅ เพิ่ม/ลบพนักงาน
- ✅ แก้ไขข้อมูลพนักงาน (ชื่อ, นามสกุล, รหัสพนักงาน)
- ✅ เปลี่ยนสถานะการเข้าทำงาน (คลิกที่ตารางเวลา)
- ✅ จัดการเบี้ยเพิ่มพิเศษ (วันหยุดนักขัตฤกษ์, เบี้ยเลี้ยง, เบี้ยขยัน, ค่าจราจร)
- ✅ จัดการรายจ่าย (ประกันสังคม, ประกันชีวิต, เบิกล่วงหน้า, เบิกอุปกรณ์)

### ระบบคำนวณเงินเดือน
- ✅ ค่าแรงพื้นฐาน 600 บาท/วัน
- ✅ โบนัสพิเศษ: ทำงาน 7 วันติดกัน ได้เพิ่ม 1 วัน
- ✅ คำนวณเงินเดือนสุทธิ (เงินเดือนพื้นฐาน + เบี้ยเพิ่มพิเศษ - รายจ่าย)
- ✅ แสดงรายละเอียดในหน้า popup

## การติดตั้งและใช้งาน

### ขั้นตอนที่ 1: ติดตั้ง Dependencies
```bash
npm install
```

### ขั้นตอนที่ 2: รันแอปพลิเคชัน
```bash
npm start
```

แอปจะเปิดใน browser ที่ `http://localhost:3000`

### ขั้นตอนที่ 3: Build สำหรับ Production
```bash
npm run build
```

## การ Deploy

### Deploy ไป GitHub Pages
1. แก้ไข `homepage` ใน `package.json`:
```json
"homepage": "https://[ชื่อผู้ใช้].github.io/[ชื่อ-repository]"
```

2. ติดตั้ง gh-pages:
```bash
npm install --save-dev gh-pages
```

3. Deploy:
```bash
npm run deploy
```

### Deploy ไป Vercel
1. ไปที่ [vercel.com](https://vercel.com)
2. เชื่อมต่อ GitHub repository
3. กด Deploy

### Deploy ไป Netlify
1. ไปที่ [netlify.com](https://netlify.com)
2. Drag & drop โฟลเดอร์ `build` หรือเชื่อมต่อ GitHub

## การใช้งาน

### โหมดหน้าบ้าน
1. ดูตารางเวลาการทำงานของพนักงาน
2. เลือกเดือน/ปี ที่ต้องการดู
3. ค้นหาพนักงานด้วยชื่อ, นามสกุล หรือรหัส
4. คลิก "สรุปรายได้" เพื่อดูรายละเอียดเงินเดือน

### โหมด Admin
1. คลิกปุ่ม "Admin"
2. ใส่รหัสผ่าน: `admin`
3. คลิกที่ตารางเวลาเพื่อเปลี่ยนสถานะ N/F
4. ใช้ปุ่ม "เพิ่มพนักงาน" เพื่อเพิ่มพนักงานใหม่
5. คลิกไอคอนดินสอเพื่อแก้ไขข้อมูลพนักงาน
6. ตั้งค่าเบี้ยเพิ่มพิเศษและรายจ่าย

## โครงสร้างโปรเจกต์

```
employee-timesheet-app/
├── public/
│   └── index.html
├── src/
│   ├── App.js          # Component หลัก
│   ├── index.js        # Entry point
│   └── index.css       # CSS หลัก
├── package.json        # Dependencies และ scripts
└── README.md          # เอกสารนี้
```

## เทคโนโลยีที่ใช้

- **React 18** - JavaScript library สำหรับสร้าง UI
- **Lucide React** - Icon library
- **Tailwind CSS** - CSS framework สำหรับ styling
- **Create React App** - Tool สำหรับ setup React project

## การปรับแต่ง

### เปลี่ยนค่าแรงรายวัน
แก้ไขใน `calculateSalary` function:
```javascript
const baseSalary = (workDays + bonusDays) * 600; // เปลี่ยน 600 เป็นจำนวนที่ต้องการ
```

### เปลี่ยนเงื่อนไขโบนัส
แก้ไขใน `calculateSalary` function:
```javascript
if (currentStreak === 7) { // เปลี่ยน 7 เป็นจำนวนวันที่ต้องการ
```

### เปลี่ยนรหัสผ่าน Admin
แก้ไขใน `handleAdminLogin` function:
```javascript
if (adminPassword === 'admin') { // เปลี่ยน 'admin' เป็นรหัสผ่านใหม่
```

## License

MIT License - ใช้งานได้อย่างอิสระ

## ติดต่อ

หากมีปัญหาหรือข้อเสนอแนะ กรุณาติดต่อผู้พัฒนา