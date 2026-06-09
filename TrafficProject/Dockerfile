# 1. نسخة بايثون مطابقة لنسختك
FROM python:3.11-slim

# 2. تثبيت المكتبات اللازمة للنظام
RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    && rm -rf /var/lib/apt/lists/*

# 3. تحديد مجلد العمل (المجلد الرئيسي للمشروع)
WORKDIR /app

# 4. نسخ المتطلبات وتثبيتها
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 5. نسخ كل شيء كما هو (يحافظ على ترتيب مجلداتك تماماً)
COPY . .

# 6. فتح منفذ فلاسك
EXPOSE 5000

# 7. التعديل الجوهري هنا:
# سنقوم بتشغيل الفلاسك من المجلد الرئيسي ونشير لمسار الملف بدقة
# هذا يضمن أن "المسار الحالي" (Base Directory) هو المجلد الرئيسي حيث يوجد الموديل
CMD ["python", "project/app.py"]