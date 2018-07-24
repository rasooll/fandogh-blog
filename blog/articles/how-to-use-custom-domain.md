# چطور از دامنه شخصی خود برای سرویس فندق استفاده کنیم؟

 مواردی وجود دارد که کاربران نیاز دارند تا برای سرویسهای خود روی فندق از دامنه دلخواهی مثل
`api.my-domain.com`
استفاده کنند.
این کار به سادگی توسط CLI فندق امکان پذیر است، ابتدا باید دامنه را ثبت و مالیکت خود را اثبات کنید سپس می‌توانید سرویس را روی دامنه مورد نظر دیپلوی کنید.

## ثبت دامنه جدید در قندق
ابتدا در CLI ‌لاگین کنید سپس دستور زیر را اجرا کنید:
```
$ fandogh domain add --name api.my-domain.com
```

با اجرای این دستور دامنه شما در اکانت شما ثبت می‌شود و یک Key ‌نمایش داده می‌شود. برای اینکه مالکیت خود را روی دامنه اثبات کنید لازم است یک TXT رکورد روی دامنه  `api.my-domain.com` ایجاد کنید و مقدار Key ای که از CLI دریافت کردید را آنجا ست کنید.
اگر TXT record ‌به درستی تنظیم شده باشد دامنه شما تایید می‌شود و به اکانت فندق شما اضافه می‌شود.

## دیپلوی سرویس روی دامنه مورد نظر

دیپلوی سرویس روی دامنه مورد نظر مثل دیپلوی هر سرویس دیگری است تنها کافیست از سویچ `host—-` استفاده کنید:
```
fandogh service deploy --host api.my-domain.com

```

به این ترتیب اگر دامنه به درستی ثبت و تایید شده باشد سرویس شما دیپلوی می‌شود و روی آدرس مورد نظر قابل دسترس است.

## تنظیم کردن CNAME
توجه داشته باشید که باید روی DNS Server دامنه مورد نظر یک CNAME  به آدرس فندق سرویس خود ایجاد کنید.
مثلا اگر نام سرویس شما some-api  است و نام namespace شما my-company است آدرس فندق سرویس شما
 `some-api-my-company.fandogh.cloud` خواهد بود و به یک رکورد CNAME در `api.my-domain.com` ‌نیاز دارید که به آدرس فندقی اشاره کند.

