# Thai Gold Dashboard 🪙

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE) [![Live Demo](https://img.shields.io/badge/demo-live-blue.svg)](https://iindrajeet4.github.io/thai-gold-dashboard/) [![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen.svg)](#)

ราคาทองคำแท่ง–ทองรูปพรรณแบบสด อ้างอิง**สมาคมค้าทองคำ (Gold Traders Association)** พร้อมกราฟราคาย้อนหลังอัตโนมัติ เครื่องคำนวณราคาขายเครื่องประดับ (เนื้อทอง + ค่ากำเหน็จ) ประเมินราคารับซื้อคืน และ**คู่มือเพชร 4Cs + ตัวประเมินราคาเพชร** — ทั้งหมดใน **ไฟล์ HTML เดียว ไม่ต้อง build ไม่ต้องมี server ไม่มี dependency ภายนอก**

Live Thai gold price dashboard (gold bar & ornament, buy/sell) with an automatic historical price chart, jewelry price calculator, buy-back estimator, and a diamond 4Cs guide + price estimator — single-file, zero-dependency, client-side only.

**[🔗 Live Demo / ลองใช้เลย](https://iindrajeet4.github.io/thai-gold-dashboard/)**

## ✨ Features

- **ราคาสด 4 ค่า** — ทองแท่ง/รูปพรรณ × ขายออก/รับซื้อ พร้อมเวลาอัปเดตและสถานะแหล่งข้อมูล (LIVE / แคช / ป้อนเอง)
- **คำนวณราคาขายเครื่องประดับ** — น้ำหนัก (บาททอง / สลึง / กรัม) × ราคารูปพรรณขายออก + ค่ากำเหน็จ × จำนวนชิ้น พร้อมตัวเลขคั่นหลักพัน
- **ประเมินราคารับซื้อคืน** — ทองเก่าแบบแท่งหรือรูปพรรณ แปลงหน่วยน้ำหนักอัตโนมัติ (แท่ง 15.244 g/บาททอง, รูปพรรณ 15.16 g/บาททอง)
- **กราฟราคาย้อนหลังอัตโนมัติ (30 วัน / 90 วัน / 1 ปี)** — ดึงราคาทองตลาดโลกย้อนหลังจาก CoinGecko (โทเคน PAX Gold) มาแสดงทันทีที่เปิดหน้า ไม่ต้องรอสะสมเอง พร้อมเส้นซ้อน (สีเขียว) จากราคาสมาคมฯ ที่เครื่องคุณบันทึกไว้แต่ละวัน · แคชผลไว้ 1 ชั่วโมงใน localStorage · ถ้าดึงไม่ได้จะแสดงเฉพาะเส้นราคาที่บันทึกในเครื่องพร้อมข้อความแจ้ง
- **💎 แท็บเพชร** — คู่มือ 4Cs ภาษาไทย (Carat / Cut / Color D–Z / Clarity FL–I3), ตัวประเมินช่วงราคาเพชรธรรมชาติตามกะรัต–รูปทรง (10 ทรง)–น้ำ–ความสะอาด–เหลี่ยม, ราคาฐานต่อกะรัตแก้ได้เพื่อปรับเทียบตลาด/Rapaport (จำค่าไว้ในเครื่อง), ตารางเทียบ มม. ↔ กะรัต และหมายเหตุใบเซอร์ GIA/HRD/IGI
- **ทนต่อความล้มเหลว** — API หลักล่มสลับไปตัวสำรอง, ออฟไลน์แสดงราคาแคชล่าสุดพร้อมแจ้งเตือนชัดเจน, กรอกราคาเองได้เสมอ และดึงราคาใหม่อัตโนมัติเมื่อกลับมาออนไลน์
- Dark / Light theme, responsive mobile-first, ภาษาไทยทั้งระบบ

## 📊 Data sources (สามชั้นเพื่อความเสถียร)

1. **Primary:** [Hua Seng Heng](https://www.huasengheng.com) public price API — ใช้ค่า `REF` (ราคาอ้างอิงสมาคมค้าทองคำ) และ `JEWEL` (ทองรูปพรรณ)
2. **Fallback:** [thai-gold-api](https://github.com/pnx/thai-gold-api) (`api.chnwt.dev`) ซึ่ง sync จาก [goldtraders.or.th](https://www.goldtraders.or.th) เว็บทางการของสมาคมค้าทองคำ
3. **Last resort:** ราคาล่าสุดที่แคชไว้ในเครื่อง หรือกรอกราคาเองจากหน้าเว็บสมาคมฯ

**กราฟราคาย้อนหลัง:** [CoinGecko](https://www.coingecko.com) `pax-gold` market_chart (ฟรี ไม่ต้องใช้ key) — [PAX Gold (PAXG)](https://paxos.com/paxg/) คือโทเคนที่อ้างอิงทองคำจริง 99.99% จำนวน 1 troy oz แปลงเป็น ฿/บาททอง ด้วย × 15.244/31.1035
> ⚠️ **ข้อจำกัดของกราฟ:** เส้น PAXG เป็น "ราคาอ้างอิงตลาดโลก" โดยประมาณ ไม่ใช่ราคาประกาศของสมาคมค้าทองคำ — อาจต่างกันเล็กน้อยจากค่าพรีเมียม/ส่วนลดของโทเคน อัตราแลกเปลี่ยน จังหวะเวลาประกาศ และความบริสุทธิ์ (99.99% vs 96.5%) จึงใช้ดู "แนวโน้ม" เป็นหลัก (Historical chart uses PAXG/THB from CoinGecko as a world-market proxy converted to baht-gold; it approximates but does not equal the Thai association quoted price.)

> ⚠️ **Disclaimer:** เพื่อการอ้างอิงเท่านั้น ราคาซื้อขายจริงขึ้นอยู่กับแต่ละร้านค้า โปรเจกต์นี้ไม่ใช่คำแนะนำการลงทุน

## 💎 Diamond estimator / ตัวประเมินราคาเพชร

ไม่มี API ราคาเพชรเรียลไทม์ที่เปิดฟรี (ราคากลาง Rapaport เป็นบริการเสียเงิน) แท็บเพชรจึงเป็น**เครื่องมืออ้างอิงฝั่ง client ล้วน**: ราคาฐานเริ่มต้น ≈ 230,000 ฿/กะรัต สำหรับเพชรกลมธรรมชาติ 1.00 ct น้ำ G, VS1, Cut Excellent (อิงช่วงตลาดค้าปลีก 2025–26 ราว US$5,500–8,500/ct จากแหล่งรีวิวตลาดเพชร เช่น diamonds.pro / StoneAlgo) แล้วปรับด้วยตัวคูณขนาด รูปทรง น้ำ ความสะอาด และเหลี่ยม แสดงเป็นช่วง ±15%

> ⚠️ **Disclaimer:** ตัวเลขเป็นแนวทางคร่าวๆ สำหรับเพชรธรรมชาติพร้อมใบเซอร์เท่านั้น ราคาจริงต่อรองเป็นรายเม็ด · เพชรแล็บราคาต่ำกว่ามาก · ร้านค้าควรแก้ "ราคาฐานต่อกะรัต" ให้ตรงตลาดปัจจุบันก่อนใช้อ้างอิง (No free realtime diamond price API exists; the estimator uses an embedded, user-editable baseline matrix — an approximate guide, not a quote.)

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
- Historical chart: PAX Gold (PAXG) prices via the free [CoinGecko API](https://www.coingecko.com/en/api)
- Diamond baseline ranges: compiled from public 2025–26 retail market guides (e.g. diamonds.pro, StoneAlgo) — approximate, user-calibratable
- UI direction inspired by [Tremor](https://github.com/tremorlabs/tremor) dashboard aesthetics (independent vanilla-JS implementation, no code reused)

---

## 💼 Services & custom work

I take on freelance and contract work around this project — custom implementation,
new features, and integration with your stack.

**Contact:** [GitHub @iindrajeet4](https://github.com/iindrajeet4) (opening an issue on this repo works too) · [DubeGames](https://dubegames.indrajeetdubeyy.workers.dev/)
