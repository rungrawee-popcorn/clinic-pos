# AI_PROMPTS.md

เอกสารนี้สรุปการใช้ AI ช่วยพัฒนาในส่วนที่ทำเสร็จแล้วจริง

---

## 1. ตั้งค่า PostgreSQL ด้วย Docker

Prompt ที่ใช้:
"How do I run PostgreSQL using Docker for a .NET Web API project?"

ผลลัพธ์:
- ได้คำสั่ง docker run สำหรับสร้าง container
- ตั้งค่า POSTGRES_USER, POSTGRES_PASSWORD, POSTGRES_DB
- map port 5432

การตรวจสอบ:
- ใช้ docker ps ตรวจสอบว่า container รันอยู่
- ใช้ docker exec เข้า psql ได้จริง

---

## 2. ตั้งค่า connection string ใน .NET

Prompt ที่ใช้:
"How should I configure connection string for PostgreSQL in appsettings.json?"

ผลลัพธ์:
- ได้รูปแบบ connection string:
  Host=localhost;Port=5432;Database=clinicdb;Username=postgres;Password=postgres

การตรวจสอบ:
- รัน dotnet run แล้วเชื่อมต่อสำเร็จ
- EF Core สามารถสร้างตารางได้

---

## 3. สร้าง Patient API (POST)

Prompt ที่ใช้:
"Generate a basic ASP.NET Core Web API controller to create a Patient using EF Core."

ผลลัพธ์:
- ได้ Controller พร้อม POST endpoint
- ใช้ async SaveChanges()
- Return 201 Created พร้อมข้อมูลที่สร้าง

การตรวจสอบ:
- ทดสอบด้วย curl
- ได้ HTTP 201
- ตรวจสอบข้อมูลใน PostgreSQL ด้วยคำสั่ง \dt และ query

---

## 4. ทดสอบ API ด้วย curl

Prompt ที่ใช้:
"Give me a curl example to POST JSON to my local API."

ผลลัพธ์:
- ใช้ curl ยิง request ไปที่ http://localhost:5050/api/Patients
- ได้ response 201
- ข้อมูลถูกบันทึกในฐานข้อมูลจริง

---

## สรุป

AI ถูกใช้เพื่อ:
- ช่วยตั้งค่า environment
- ช่วย scaffold controller
- ช่วย debug การเชื่อมต่อฐานข้อมูล

ทุกขั้นตอนถูกตรวจสอบด้วยการ:
- รันระบบจริง
- ตรวจสอบฐานข้อมูลด้วย psql
- ทดสอบ HTTP response ด้วย curl