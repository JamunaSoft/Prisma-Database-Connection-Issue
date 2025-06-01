# Prisma-Database-Connection-Issue

আপনি `GRANT` কমান্ডটি **PostgreSQL shell (psql)** এর ভিতরে চালাতে হবে, **Linux shell/terminal**-এ না।

আপনি এখন Linux shell-এ আছেন (`root@...#`), যেখানে `GRANT` কমান্ড **চিনে না**, তাই `"GRANT: command not found"` দেখাচ্ছে।

---

## ✅ সঠিকভাবে GRANT পারমিশন দেওয়ার ধাপ:

### 🔹 Step 1: `psql`-এ ঢুকুন

```bash
psql -U postgres -d cpc_final
```

এতে আপনি PostgreSQL shell-এ প্রবেশ করবেন, যেটা এভাবে দেখাবে:

```
cpc_final=#
```

---

### 🔹 Step 2: এখন `GRANT` কমান্ড দিন

```sql
GRANT CONNECT ON DATABASE cpc_final TO "sharifsarkar786@gmail.com";
GRANT USAGE ON SCHEMA public TO "sharifsarkar786@gmail.com";
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO "sharifsarkar786@gmail.com";
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO "sharifsarkar786@gmail.com";
```

> ⚠️ যেহেতু ইউজারনেমে `@` আছে, তাই **double quotes** ব্যবহার করতেই হবে (`"sharifsarkar786@gmail.com"`)

---

### 🔹 বের হওয়ার জন্য:

```sql
\q
```

---

### এখন pgAdmin থেকে `cpc_final` ডাটাবেসে ফুল পারমিশনে অ্যাক্সেস করতে পারবেন।

অন্য কিছু জানতে চাইলে বলুন, আমি আছি।
