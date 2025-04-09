
# ساختار خروجی کاوه
خروجی پروژه کاوه در قالب چهار فایل در مسیر اصلی این مخزن قابل استفاده است.

|نام فایل|کاربرد|
|--|--|
|full.json|نسخه کامل|
|mini.json|نسخه کم حجم (پیشنهادی)|
|micro.json|نسخه بسیار کم حجم|
|VERSION|کد نسخه فعلی|

در ادامه به توضیح هر یک از این فایل ها خواهیم پرداخت.

## نسخه کامل (full.json)
این فایل کامل ترین نسخه از خروجی کاوه را به شکل indent شده ارائه می دهد. ساختار فایل به شکل زیر است:
```json
{
  "version": VERSION,
  "docs": {
    MALWARE_CLASS_1: MALWARE_CLASS_1_URL,
    MALWARE_CLASS_2: MALWARE_CLASS_2_URL,
    MALWARE_CLASS_3: MALWARE_CLASS_3_URL,
    ...
  },
  "malware": [
    {
      "sha256_hash": FILE1_SHA256_HASH,
      "sha1_hash": FILE1_SHA1_HASH,
      "md5_hash": FILE1_MD5_HASH,
      "detection": [
        MALWARE_CLASS_1,
        MALWARE_CLASS_2,
        ...
      ]
    },
    {
      "sha256_hash": FILE2_SHA256_HASH,
      "sha1_hash": FILE2_SHA1_HASH,
      "md5_hash": FILE2_MD5_HASH,
      "detection": [
        MALWARE_CLASS_3,
        ...
      ]
    },
    ...
  ]
}
```

### تعریف بخش اصلی

|نام|نوع|تعریف|
|--|--|--|
|`version`|string|نسخه|
|`docs`|object|لینک مستندات دسته های بدافزار|
|`malware`|array|آرایه شامل بدافزار ها|

### تعریف بخش docs
|نام|نوع|تعریف|
|--|--|--|
|MALWARE_CLASS_N|string|نام دسته بدافزار|
|MALWARE_CLASS_N_URL|string|آدرس URL مستندات دسته بدافزار|

### تعریف بخش malware
|نام|نوع|تعریف|
|--|--|--|
|`sha256_hash`|string|هش SHA256 بدافزار|
|`sha1_hash`|string|هش SHA1 بدافزار|
|`md5_hash`|string|هش MD5 بدافزار|
|`detection`|array|آرایه شامل نام دسته های بدافزار تشخیص داده شده|
|MALWARE_CLASS_N|string|نام دسته بدافزار|

> **نکته**:
تضمین می شود که به ازای هر دسته بدافزار قابل تشخیص، یک لینک با همان نام در آبجکت docs موجود است.

## نسخه کم حجم (mini.json)
این فایل دارای تمامی موارد نسخه کامل به جز `sha1_hash` و `md5_hash` است و indent نشده است. برای استفاده از داده های کاوه در برنامه های ثانویه، استفاده از این نسخه پیشنهاد می شود.
ساختار فایل به شکل زیر است:
```json
{
  "version": VERSION,
  "docs": {
    MALWARE_CLASS_1: MALWARE_CLASS_1_URL,
    MALWARE_CLASS_2: MALWARE_CLASS_2_URL,
    MALWARE_CLASS_3: MALWARE_CLASS_3_URL,
    ...
  },
  "malware": [
    {
      "sha256_hash": FILE1_SHA256_HASH,
      "detection": [
        MALWARE_CLASS_1,
        MALWARE_CLASS_2,
        ...
      ]
    },
    {
      "sha256_hash": FILE2_SHA256_HASH,
      "detection": [
        MALWARE_CLASS_3,
        ...
      ]
    },
    ...
  ]
}
```
## نسخه بسیار کم حجم (micro.json)

این فایل فقط دارای هش md5 بدافزار ها است و indent نشده است. به جز مواردی که به بهینه سازی شدید نیاز است، استفاده از این نسخه پیشنهاد نمی شود.
ساختار فایل به شکل زیر است:
```json
{
  "version": VERSION,
  "malware": [
    FILE1_MD5_HASH,
    FILE2_MD5_HASH,
    …
  ]
}
```

## نسخه (VERSION)
این فایل نشانگر نسخه فعلی داده های کاوه است. فرمت نسخه، تاریخ انتشار آن با فرمت `YYYYMMDD` می باشد. توسعه دهندگان می توانند قبل از به روزرسانی و دریافت فایل JSON مورد نظر، نسخه فعلی خود را با محتوای این فایل مقایسه کنند تا از وجود نسخه جدیدتر مطلع شوند.