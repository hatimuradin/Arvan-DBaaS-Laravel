## راهنمای اتصال به دیتابیس ابری در Laravel
ابتدا از پنل کاربری خود دیتابیس ابری کلاستر دیتابیس را با تنظیمات مورد نظر ایجاد کنید.

پس از اتمام مراحل ساخت که ممکن است کمی زمان بر باشد کلاستر دیتابیس شما ساخته میشود و در وضعیت فعال قرار میگیرد.
دیتابیس پیش فرض پس از ساخت default و کاربر پیش فرض برای این دیتابیس base-user است.

اگر به دیتابیس و کاربر دیتابیس دیگری احتیاج دارید میتوانید از همین پنل اقدام به ساخت آن‌ها بکنید.
با توجه به این مشخصات تنظیمات زیر را در بخش مربوط به دیتابیس در فایل تنظیمات پروژه‌ی خود (پیش فرض .env است) پروژه‌ی خود قرار دهید.
مثال برای postgresql:


```
DB_CONNECTION=pgsql
DB_HOST=XXXXXXXXXXXXXXXXXX.db.arvandbaas.ir
DB_PORT=5432
DB_DATABASE=default
DB_USERNAME=base-user
DB_PASSWORD=SECRET_PASSWORD
```

برای اطمینان از صحت تنظیمات دیتابیس خود میتوانید دستور php artisan tinker را اجرا کرده و در shell موجود با دستور زیر صحت ارتباط با دیتابیس را بررسی کنید:

```
DB::connection()->getPdo();
```
خروجی نمونه:
```
= Pdo\Pgsql {#5296
    inTransaction: false,
    attributes: {
      CASE: NATURAL,
      ERRMODE: EXCEPTION,
      PERSISTENT: false,
      DRIVER_NAME: "pgsql",
      SERVER_INFO: "PID: 555; Client Encoding: UTF8; Is Superuser: off; Session Authorization: base-user; Date Style: ISO, MDY",
      ORACLE_NULLS: NATURAL,
      CLIENT_VERSION: "16.4",
      SERVER_VERSION: "17.3 (Debian 17.3-3.pgdg120+1)",
      STATEMENT_CLASS: [
        "PDOStatement",
      ],
      EMULATE_PREPARES: false,
      CONNECTION_STATUS: "Connection OK; waiting to send.",
      STRINGIFY_FETCHES: false,
      DEFAULT_FETCH_MODE: BOTH,
    },
  }
```

برای اعمال جداول در دیتابیس هم از php artisan migrate استفاده کنید و صحت آن ها را با هر یک از کلاینت‌های دیتابیس خود بررسی کنید.
