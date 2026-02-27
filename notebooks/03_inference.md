# 03 - الاستدلال والتنبؤ (Inference)

## الهدف
تطبيق نموذج YOLOv8 المدرب على صور جديدة والحصول على التنبؤات

## المتطلبات
- نموذج YOLOv8 مدرب (من الدفتر السابق)
- صور اختبار أو فيديوهات

## الخطوات الأساسية

### 1. تحميل النموذج
```python
from ultralytics import YOLO

# تحميل النموذج
model = YOLO('path/to/best.pt')
```

### 2. الاستدلال على الصور
```python
import cv2

# قراءة صورة
img = cv2.imread('image.jpg')

# الاستدلال
results = model(img)

# عرض النتائج
for r in results:
    im_array = r.plot()
    cv2.imshow('YOLOv8', im_array)
    cv2.waitKey(0)
```

### 3. معالجة النتائج
```python
# الحصول على الكائنات المكتشفة
for result in results:
    boxes = result.boxes
    for box in boxes:
        x1, y1, x2, y2 = box.xyxy[0]
        conf = box.conf[0]
        cls = box.cls[0]
        print(f"Class: {cls}, Confidence: {conf}")
```

## ملاحظات مهمة
- تأكد من استخدام نفس الإعدادات أثناء الاستدلال
- معالجة الصور بنفس الطريقة المستخدمة في التدريب
- تجنب الصور الكبيرة جداً لتسريع الاستدلال

## المراجع
**[فتح دفتر التدريب](https://colab.research.google.com/)** - اضغط لفتح دفتر Colab للاستدلال
