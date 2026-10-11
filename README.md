# ตู้เก็บกลิ่น (แอป Android)

แอปเก็บน้ำหอม แนะนำขวดที่เหมาะกับโอกาสและอากาศ มีคะแนนจาก Fragrantica
ห่อด้วย Capacitor โค้ดหน้าแอปอยู่ที่ `www/index.html`

## วิธีที่ 1: ให้ GitHub สร้าง APK ให้ (ไม่ต้องติดตั้งอะไรในเครื่อง)

1. สร้าง repository ใหม่บน GitHub แล้วอัปโหลดไฟล์ทั้งโฟลเดอร์นี้ (รวมโฟลเดอร์ `.github`)
2. เปิดแท็บ Actions เลือก "Build APK" แล้วกด Run workflow
3. รอประมาณ 5-10 นาที เปิดงานที่เสร็จแล้ว ดาวน์โหลดไฟล์ `scent-cabinet-apk`
4. แตก zip จะได้ `app-debug.apk` ส่งเข้าโทรศัพท์แล้วเปิดติดตั้ง
   (Android จะถามให้อนุญาตติดตั้งจากแหล่งที่ไม่รู้จักหนึ่งครั้ง)

## วิธีที่ 2: สร้างเองด้วย Android Studio

ต้องมี Node.js 20 ขึ้นไป, JDK 21 และ Android Studio

```
npm install
npx cap add android
npx cap sync android
npx cap open android
```

ใน Android Studio กด Run ไปที่โทรศัพท์หรือ emulator
หรือสั่งสร้างไฟล์ติดตั้งด้วย `cd android && ./gradlew assembleDebug`
ไฟล์อยู่ที่ `android/app/build/outputs/apk/debug/app-debug.apk`

## หมายเหตุ

- ข้อมูลน้ำหอมเก็บในเครื่อง (localStorage ของแอป) ถ้าลบแอปหรือล้างข้อมูลแอป ข้อมูลจะหาย
- อากาศดึงสดจาก Open-Meteo ตอนเปิดแอป เลือกเมืองได้ที่แผงอากาศ (ต้องต่ออินเทอร์เน็ต)
- ฟอนต์โหลดจาก Google Fonts ถ้าออฟไลน์จะใช้ฟอนต์ของเครื่องแทน
- ไฟล์ debug เหมาะสำหรับติดตั้งใช้เอง ถ้าจะขึ้น Google Play ต้องเซ็นไฟล์ release และเปลี่ยน `appId` ใน `capacitor.config.json`
- ก่อนสร้างจริงให้เปลี่ยน `com.scentcabinet.app` เป็นรหัสของคุณเองถ้าต้องการ
