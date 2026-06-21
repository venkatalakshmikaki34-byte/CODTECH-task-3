# CODTECH-task-3
import os
from PIL import Image, ImageFilter

# 1. Load an image from the local directory
# Replace 'input_image.jpg' with your actual image path
input_path = "input_image.jpg"

try:
    # Open the image file
    with Image.open(input_path) as img:
        img.load()  # Load into memory to allow closing the file safely
        
        print("=== Original Image Information ===")
        print(f"Format: {img.format}")
        print(f"Size:   {img.size} (Width, Height)")
        print(f"Mode:   {img.mode}")
        
        # 2. Resize the image (returns a new Image object)
        # Dimensions are passed as a tuple: (width, height)
        resized_img = img.resize((400, 400))
        
        # 3. Rotate the image 
        # Degrees are measured counter-clockwise
        rotated_img = resized_img.rotate(90)
        
        # 4. Crop a portion of the image
        # Coordinates: (left, upper, right, lower)
        crop_box = (100, 100, 300, 300)
        cropped_img = rotated_img.crop(crop_box)
        
        # 5. Apply a filter (e.g., Blur effect)
        final_img = cropped_img.filter(ImageFilter.BLUR)
        
        # 6. Save the processed image
        output_path = "processed_output.png"
        final_img.save(output_path)
        print(f"\n[Success] Processed image saved to: {output_path}")
        
        print("\n=== Processed Image Information ===")
        print(f"Size:   {final_img.size}")
        print(f"Mode:   {final_img.mode}")

except FileNotFoundError:
    print(f"Error: Could not find the image '{input_path}'. Please check the path.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")




***output***
=== Original Image Information ===
Format: JPEG
Size:   (1920, 1080) (Width, Height)
Mode:   RGB

[Success] Processed image saved to: processed_output.png

=== Processed Image Information ===
Size:   (200, 200)
Mode:   RGB

