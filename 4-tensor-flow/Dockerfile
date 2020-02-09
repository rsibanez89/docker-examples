FROM python:3.7

# Following this example:
#   https://github.com/tensorflow/hub/tree/master/tensorflow_hub/tools/make_image_classifier

# Download and install tensorflow:
RUN pip install tensorflow~=2.0 && \
  pip install tensorflow-hub[make_image_classifier]~=0.6

# Creating a workspace folder inside the container:
RUN mkdir /workspace
WORKDIR /workspace

# Download flowers training data:
# /workspace
#   /flower_photos
#     /daisy
#     /dandelion
#     /roses
#     /sunflowers
#     /tulips
RUN curl -sS http://download.tensorflow.org/example_images/flower_photos.tgz > flower_photos.tgz && \
  tar -xvf flower_photos.tgz && \
  rm flower_photos.tgz

# Run image classifier and save labels and model:
# /workspace
#   /model_dir
#   class_labels.txt
#   flower_photos_model.tflite
RUN make_image_classifier \
    --image_dir flower_photos dir \
    --tfhub_module https://tfhub.dev/google/tf2-preview/mobilenet_v2/feature_vector/4 \
    --saved_model_dir model_dir \
    --labels_output_file class_labels.txt \
    --tflite_output_file flower_photos_model.tflite

# Download the image labeling:
# /workspace
#   label_image.py
RUN curl -sS https://raw.githubusercontent.com/tensorflow/tensorflow/master/tensorflow/lite/examples/python/label_image.py > label_image.py

# Copy test images into the container
COPY . .

# Print the workspace content:
RUN find -maxdepth 2 -ls

# Test rose1:
RUN python label_image.py \
  --input_mean 0 --input_std 255 \
  --model_file flower_photos_model.tflite --label_file class_labels.txt \
  --image rose1.jpg

# Test rose2:
RUN python label_image.py \
  --input_mean 0 --input_std 255 \
  --model_file flower_photos_model.tflite --label_file class_labels.txt \
  --image rose2.jpg

# Test tulips1:
RUN python label_image.py \
  --input_mean 0 --input_std 255 \
  --model_file flower_photos_model.tflite --label_file class_labels.txt \
  --image tulips1.jpg

# Test tulips2:
RUN python label_image.py \
  --input_mean 0 --input_std 255 \
  --model_file flower_photos_model.tflite --label_file class_labels.txt \
  --image tulips2.jpg