# Lab 3 – DHCP Server Configuration in a Network

## 🎯 الهدف
إعداد راوتر ليعمل كـ DHCP Server لتوزيع عناوين IP تلقائيًا على الأجهزة في الشبكة.

---

## 🖥️ الأجهزة المستخدمة
- Router 2911
- Switch 2960
- 3 PCs
- كابلات Straight Through

---

## 📡 خطوات الإعداد

### 1️⃣ تصميم الـ Topology
قم بتوصيل الأجهزة بالشكل التالي:

![Topology](topology.png)

---

### 2️⃣ إعداد DHCP على الراوتر
افتح CLI للراوتر واكتب الأوامر التالية:

```bash
Router> enable
Router# configure terminal
Router(config)# ip dhcp pool LAN
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.1.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
3️⃣ ضبط إعدادات الـ PCs
افتح أي PC → IP Configuration → اختر DHCP.

تحقق أن الجهاز حصل على IP أوتوماتيكي.


4️⃣ اختبار الاتصال
قم بإجراء Ping بين الأجهزة للتأكد من أن الاتصال يعمل:


📂 ملفات اللاب
Packet Tracer File – Lab3_DHCP_Network.pkt

topology Image

pc ip config Image

ping test Image

command line Image

✅ النتيجة:
تم تكوين DHCP بنجاح، والأجهزة حصلت على IP تلقائيًا من الراوتر.
