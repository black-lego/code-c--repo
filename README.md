
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Conv2D, MaxPooling2D, Flatten, Dense
from tensorflow.keras.preprocessing import image
import numpy as np

# بناء النموذج
model = Sequential([
    Conv2D(32, (3, 3), activation='relu', input_shape=(150, 150, 3)),
    MaxPooling2D((2, 2)),
    Conv2D(64, (3, 3), activation='relu'),
    MaxPooling2D((2, 2)),
    Conv2D(128, (3, 3), activation='relu'),
    MaxPooling2D((2, 2)),
    Conv2D(128, (3, 3), activation='relu'),
    MaxPooling2D((2, 2)),
    Flatten(),
    Dense(512, activation='relu'),
    Dense(3, activation='softmax')
])

# تحديد المعلمات الخاصة بعملية التدريب
model.compile(optimizer='adam',
              loss='categorical_crossentropy',
              metrics=['accuracy'])

# تحميل الوزن المدربة مسبقًا إذا كانت متاحة
model.load_weights('trash_classification_model_weights.h5')

# دالة للتصنيف
def classify_trash(image_path):
    img = image.load_img(image_path, target_size=(150, 150))
    img_array = image.img_to_array(img)
    img_array = np.expand_dims(img_array, axis=0)
    predictions = model.predict(img_array)
    trash_types = ['ورق', 'بلاستيك', 'زجاج']
    predicted_trash = trash_types[np.argmax(predictions)]
    return predicted_trash

# تجربة التصنيف على صورة جديدة
image_path = 'new_trash_image.jpg'
predicted_label = classify_trash(image_path)
print("القمامة في الصورة هي:", predicted_label)
