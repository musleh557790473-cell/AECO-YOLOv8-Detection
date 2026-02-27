# مرحلة 2️⃣ تدريب نموذج YOLOv8

> المرحلة الثانية: تدريب نموذج الكشف على البيانات المحضرة.

---

## الخطوات:

### 1️⃣ **المتطلبات:**
- [ ] البيانات محملة من مرحلة 1
- [ ] مقدرة GPU (T4 على الأقل)
- [ ] وقت تدريب: 30-50 حقبة

### 2️⃣ **عينات التدريب:**
```python
from ultralytics import YOLO

# النموذج
 nموذج = YOLO('yolov8n.pt')  # nano (0.78M)
# or
# model = YOLO('yolov8s.pt')  # small (3.2M)

# معاملات التدريب
 model.train(
    data='/path/to/data.yaml',  # Roboflow YAML
    epochs=50,                  # عدد الحقب
    imgsz=640,                 # حجم الصورة
    batch=16,                  # حجم الدفعة
    device=0,                  # GPU
    patience=20,               # early stopping
    save=True,                 # حفظ نصدي الوزن
    verbose=True
)
```

### 3️⃣ **مراقبة التقدم:
```python
# عرض المقاييس
 results = model.train(...)

# المقاييس:
 # - Precision (P)
 # - Recall (R)
 # - mAP50
 # - mAP50-95
```

---

## المخرجات:

- فلدر `runs/detect/train/weights/best.pt` → أفضل نموذج
- منحنيات التدريب (Precision, Recall, mAP)

---

## رابط Colab:

**[Open Training Notebook](https://colab.research.google.com/)** → انتظر رابطاً معللاً لاحقاً

---

❗️ **العرق للمرحلة الثالثة**: [المرحلة 3 - الاستدلال](./03_inference.md)
