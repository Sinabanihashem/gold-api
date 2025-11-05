# 👑 SinaGoldAPI version : 2.1.1

وب‌سرویس **SinaGoldAPI** یک سرویس سریع و سبک برای دریافت قیمت‌ لحظه‌ای **طلا و سکه** از معتبرترین منبع اعلام نرخ‌هاست 🇮🇷💰  
فقط با یک درخواست GET می‌تونی نرخ‌های لحظه‌ای رو بگیری — **بدون نیاز به API Key** 🚀


---

## 🌐 آدرس وب‌سرویس

https://gold.api-sina-free.workers.dev/gold

---

## 🔹 خروجی‌ها

| پارامتر | نوع | توضیح |
|--------|------|--------|
| gold_18_ayar | number | قیمت هر گرم طلای ۱۸ عیار |
| gold_24_ayar | number | قیمت هر گرم طلای ۲۴ عیار |
| gold_second_hand | number | قیمت طلای دست دوم |
| mesghal_tala | number | قیمت هر مثقال طلا |
| abshode_naghd | number | قیمت آبشده نقدی |
| abshode_moamelati | number | قیمت آبشده معاملاتی |
| sekke_emami | number | سکه امامی |
| sekke_bahar_azadi | number | سکه بهار آزادی |
| nim_sekke | number | نیم‌سکه |
| rob_sekke | number | ربع‌سکه |
| sekke_gerami | number | سکه گرمی |
| habab_* | number | حباب سکه‌ها |
| updated_at | string | زمان به‌روزرسانی |
| source | string | منبع دریافت قیمت |

---

## 🧪 نمونه درخواست

GET https://gold.api-sina-free.workers.dev/gold

---

## 🧾 نمونه خروجی

```
{
  "gold_18_ayar": 104686000,
  "gold_24_ayar": 139580000,
  "gold_second_hand": 103290300,
  "mesghal_tala": 453590000,
  "abshode_naghd": 453750000,
  "abshode_moamelati": 453450000,
  "sekke_emami": 1109950000,
  "sekke_bahar_azadi": 1040100000,
  "nim_sekke": 579500000,
  "rob_sekke": 333000000,
  "sekke_gerami": 164000000,
  "habab_emami": 99440000,
  "updated_at": "2025-11-05T20:24:12.793Z",
  "source": "tgju.org"
}
```

---

## 💻 نمونه استفاده در Python

```
import requests

res = requests.get("https://gold.api-sina-free.workers.dev/gold")
data = res.json()

print("💰 طلای 18 عیار:", data["gold_18_ayar"])
print("🥇 سکه امامی:", data["sekke_emami"])
print("⏱ آخرین بروزرسانی:", data["updated_at"])
```

---

## 🤖 استفاده در ربات روبیکا / بات‌ها

```
from rubpy import Client, filters
import requests

bot = Client(name="sina_gold")

@bot.on_message_updates(filters.text)
async def handler(message):
    if message.text == "قیمت طلا":
        data = requests.get("https://gold.api-sina-free.workers.dev/gold").json()
        await message.reply(
            f"💰 قیمت لحظه‌ای طلا:\n\n"
            f"طلای ۱۸ عیار: {data['gold_18_ayar']:,} تومان\n"
            f"سکه امامی: {data['sekke_emami']:,} تومان\n"
            f"نیم‌سکه: {data['nim_sekke']:,} تومان\n"
            f"\n⏱ بروزرسانی: {data['updated_at']}"
        )

bot.run()
```

---

## 👤 Developer

@Sinabanis

📍 Hosted on: Cloudflare Workers          
🗳 Rubika: https://rubika.ir/Sinabani_api          
🔗 Endpoint: https://gold.api-sina-free.workers.dev/gold          
