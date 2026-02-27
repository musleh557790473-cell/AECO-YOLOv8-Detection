# مرحلة 1️⃣ تحضير البيانات (Data Preparation)

> هذه المرحلة الأولى من خطة طوارئ المشروع. يجب إكمال هذه الخطوات بنجاح.

---

## الخطوات الأساسية:

### 1️⃣ **الشروط المسبقة:**
- [ ] الدخول إلى Roboflow بحسابك
- [ ] العثور على مشروع البيانات للبنية التحتية (AECO)
- [ ] نسخ API Key من Roboflow

### 2️⃣ **تحميل Roboflow API:؛**
```python
# القطعة الأولى - تثبيت مكتبات
!pip install roboflow ultralytics opencv-python

# القطعة الثانية - متغيرات للوصول الآمن

ROBOFLOW_API_KEY = "ع[YOUR_API_KEY_HERE]ع"
ROBOFLOW_WORKSPACE = "ع[YOUR_WORKSPACE]ع"
ROBOFLOW_PROJECT = "عconstruction-safetyع"
ROBOFLOW_VERSION = 1
```

### 3️⃣ **تحميل بيانات YOLO:**
```python
from roboflow import Roboflow

rf = Roboflow(api_key=ROBOFLOW_API_KEY)
project = rf.workspace(ROBOFLOW_WORKSPACE).project(ROBOFLOW_PROJECT)
dataset = project.versions(ROBOFLOW_VERSION).download("yolov8")

print(آآآالبيانات محملة بنجات!")
print(fآآPath: {dataset.location}")
```

### 4️⃣ **التحقق من بنية البيانات:**
```python
import os
from pathlib import Path

data_dir = Path(dataset.location)

print(آآالتركيبة:")
print(f"- مجلد التدريب: {data_dir / 'train'}")
print(f"- مجلد التحقق: {data_dir / 'val'}")
print(f"- مجلد الاختبار: {data_dir / 'test'}")

# عد الصور
نافذائ_train = len(list((data_dir / 'train' / 'images').glob('*.jpg')))
نافذائ_val = len(list((data_dir / 'val' / 'images').glob('*.jpg')))

print(f"\nالإحصائيات:")
print(f"- عدد صور التدريب: {train_images}")
print(f"- عدد صور التحقق: {val_images}")
print(f"- النسبة: 80% تدريب / 20% تحقق")
```

---

## رابط Colab:
ــــــــــــــ

### مهم: ابدأ هنا:

لسرعة العمل عبر Google Colab:

1. اشغل [هذا الرابط](هينافذ) في Google Colab
2. اعدل مراد هبوط:
   - `ROBOFLOW_API_KEY`
   - `ROBOFLOW_WORKSPACE`  
   - `ROBOFLOW_PROJECT`
3. امري Runtime > Run all
4. انزل البيانات

---

## معلومات مهمة:

⏱️ **الوقت المتوقع**: 5-10 دقائق
💾 **نوع العتاد**: GPU (الأبل - لكن يعمل على CPU أيضاً)
✅ **النتيجة المتوقعة**: بيانات YOLO مميعة على Colab

---

❗️ **العرق للمرحلة الثانية**: [المرحلة 2 - النمذجة](./02_model_training.md)
