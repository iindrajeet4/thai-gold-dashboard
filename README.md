# Thai Gold Dashboard 🪙

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE) [![Live Demo](https://img.shields.io/badge/demo-live-blue.svg)](https://iindrajeet4.github.io/thai-gold-dashboard/) [![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen.svg)](#)

ราคาทองคำแท่ง–ทองรูปพรรณแบบสด อ้างอิง**สมาคมค้าทองคำ (Gold Traders Association)** พร้อมเครื่องคำนวณราคาขายเครื่องประดับ (เนื้อทอง + ค่ากำเหน็จ) และประเมินราคารับซื้อคืน — ทั้งหมดใน **ไฟล์ HTML เดียว ไม่ต้อง build ไม่ต้องมี server ไม่มี dependency ภายนอก**

Live Thai gold price dashboard (gold bar & ornament, buy/sell) with a jewelry price calculator and buy-back estimator — single-file, zero-dependency, client-side only.

**[🔗 Live Demo / ลองใช้เลย](https://iindrajeet4.github.io/thai-gold-dashboard/)**

## ✨ Features

- **ราคาสด 4 ค่า** — ทองแท่ง/รูปพรรณ × ขายออก/รับซื้อ พร้อมเวลาอัปเดตและสถานะแหล่งข้อมูล (LIVE / แคช / ป้อนเอง)
- **คำนวณราคาขายเครื่องประดับ** — น้ำหนัก (บาททอง / สลึง / กรัม) × ราคารูปพรรณขายออก + ค่ากำเหน็จ × จำนวนชิ้น พร้อมตัวเลขคั่นหลักพัน
- **ประเมินราคารับซื้อคืน** — ทองเก่าแบบแท่งหรือรูปพรรณ แปลงหน่วยน้ำหนักอัตโนมัติ (แท่ง 15.244 g/บาททอง, รูปพรรณ 15.16 g/บาททอง)
- **กราฟราคาสะสม** — บันทึกราคาทองแท่งขายออกลง localStorage ทุกครั้งที่เปิด (วันละ 1 จุด สูงสุด 60 จุด) วาด sparkline ในเครื่องคุณเอง
- **ทนต่อความล้มเหลว** — API หลักล่มสลับไปตัวสำรอง, ออฟไลน์แสดงราคาแคชล่าสุดพร้อมแจ้งเตือนชัดเจน, กรอกราคาเองได้เสมอ และดึงราคาใหม่อัตโนมัติเมื่อกลับมาออนไลน์
- Dark / Light theme, responsive mobile-first, ภาษาไทยทั้งระบบ

## 📊 Data sources (สามชั้นเพื่อความเสถียร)

1. **Primary:** [Hua Seng Heng](https://www.huasengheng.com) public price API — ใช้ค่า `REF` (ราคาอ้างอิงสมาคมค้าทองคำ) และ `JEWEL` (ทองรูปพรรณ)
2. **Fallback:** [thai-gold-api](https://github.com/pnx/thai-gold-api) (`api.chnwt.dev`) ซึ่ง sync จาก [goldtraders.or.th](https://www.goldtraders.or.th) เว็บทางการของสมาคมค้าทองคำ
3. **Last resort:** ราคาล่าสุดที่แคชไว้ในเครื่อง หรือกรอกราคาเองจากหน้าเว็บสมาคมฯ

> ⚠️ **Disclaimer:** เพื่อการอ้างอิงเท่านั้น ราคาซื้อขายจริงขึ้นอยู่กับแต่ละร้านค้า โปรเจกต์นี้ไม่ใช่คำแนะนำการลงทุน

## 🚀 Usage

1. ใช้งานได้ทันทีที่ **https://iindrajeet4.github.io/thai-gold-dashboard/** — หรือดาวน์โหลด/clone repo นี้
2. เปิด `index.html` ในเบราว์เซอร์ได้เลย — หรือ deploy ขึ้น GitHub Pages / static host ใดก็ได้
3. กด **⟳ อัปเดตราคา** เพื่อดึงราคาล่าสุด (ต้องต่ออินเทอร์เน็ต; ถ้าไม่ได้จะใช้ราคาแคชหรือกรอกเอง)

ข้อมูลทั้งหมด (ธีม, ราคาแคช, ประวัติกราฟ) เก็บใน localStorage ของเบราว์เซอร์คุณเท่านั้น — ไม่มีการส่งข้อมูลใดออกไปนอกจากการเรียกดึงราคา

## 🧮 สูตรคำนวณ

```
ราคาขายต่อชิ้น  = (ราคารูปพรรณขายออก × น้ำหนักเป็นบาททอง) + ค่ากำเหน็จ
ราคารับซื้อคืน   = ราคารับซื้อ (แท่ง/รูปพรรณ) × น้ำหนักเป็นบาททอง

1 บาททอง (แท่ง)    = 15.244 กรัม
1 บาททอง (รูปพรรณ) = 15.16 กรัม
1 สลึง             = ¼ บาททอง
```

## 📄 License

MIT — see [LICENSE](LICENSE)

## 🙏 Credits

- Price data: Gold Traders Association via Hua Seng Heng API and [thai-gold-api](https://github.com/pnx/thai-gold-api)
- UI direction inspired by [Tremor](https://github.com/tremorlabs/tremor) dashboard aesthetics (independent vanilla-JS implementation, no code reused)
