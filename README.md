# 📌 Image Caption Generator with Streamlit + BLIP

import streamlit as st
from transformers import BlipProcessor, BlipForConditionalGeneration
from PIL import Image
import torch

# Load model + processor
@st.cache_resource  # cache so model loads only once
def load_model():
    processor = BlipProcessor.from_pretrained("Salesforce/blip-image-captioning-base")
    model = BlipForConditionalGeneration.from_pretrained("Salesforce/blip-image-captioning-base")
    return processor, model

processor, model = load_model()

st.title("📸 Image Caption Generator")
st.write("Upload an image and get an AI-generated caption!")

# File uploader
uploaded_file = st.file_uploader("Choose an image...", type=["jpg", "jpeg", "png"])

if uploaded_file is not None:
    # Display the uploaded image
    image = Image.open(uploaded_file).convert("RGB")
    st.image(image, caption="Uploaded Image", use_column_width=True)

    # Generate caption button
    if st.button("Generate Caption"):
        inputs = processor(images=image, return_tensors="pt")
        output = model.generate(**inputs, max_new_tokens=30)
        caption = processor.decode(output[0], skip_special_tokens=True)
        st.success(f"📝 Caption: {caption}")
