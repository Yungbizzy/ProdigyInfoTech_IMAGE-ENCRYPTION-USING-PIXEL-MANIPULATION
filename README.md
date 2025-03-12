# ProdigyInfoTech_IMAGE-ENCRYPTION-USING-PIXEL-MANIPULATION
## 1. Introduction
Image encryption is a crucial technique used to protect digital images from unauthorized access and manipulation. In this project, we implemented an image encryption and decryption system using pixel manipulation. The method involves shifting pixel values to transform the original image into an encrypted version and then reversing the shift to restore the original image. This ensures that image data remains secure and can only be decrypted with the correct key (shift value).

The implementation was carried out in a Kali Linux environment using Python 3, with the Pillow and NumPy libraries for image processing. A virtual environment was also used to manage dependencies efficiently.

## 2. Objectives
The objectives of this project were:
- To implement an image encryption and decryption system using Python.
- To secure image files by modifying pixel values through pixel manipulation.
- To demonstrate encryption and decryption using a shift-based approach.
- To validate the effectiveness of the encryption and decryption process.

## 3. System Requirements
- **Operating System:** Kali Linux
- **Programming Language:** Python 3
- **Libraries Used:**
  - `Pillow`: For image processing
  - `NumPy`: For numerical operations on image pixels


## 4. Step-by-Step Implementation

### Step 1: Setting Up the Environment
Before writing the Python script, we need to set up a Python virtual environment and install the necessary libraries.

# Create and activate a virtual environment
python3 -m venv myenv
source myenv/bin/activate
![image](https://github.com/user-attachments/assets/1f933d0c-8ed8-47c7-b9a1-9f5850d64627)

# Install required libraries
pip install numpy pillow


### Step 2: Writing the Image Encryption and Decryption Script

#### Create a Python Script:
Open a terminal and create a new Python file:

nano image_encryption.py

#### Paste the Following Python Code:

```python
from PIL import Image
import numpy as np

def encrypt_image(input_image_path, output_image_path, shift_value):
    image = Image.open(input_image_path)
    img_array = np.array(image)
    
    # Apply pixel shift
    encrypted_array = np.clip(img_array + shift_value, 0, 255)
    
    encrypted_image = Image.fromarray(encrypted_array.astype(np.uint8))
    encrypted_image.save(output_image_path)
    print(f"Image encrypted successfully! Saved as {output_image_path}")

def decrypt_image(input_image_path, output_image_path, shift_value):
    encrypted_image = Image.open(input_image_path)
    encrypted_array = np.array(encrypted_image)
    
    # Reverse pixel shift
    decrypted_array = np.clip(encrypted_array - shift_value, 0, 255)
    
    decrypted_image = Image.fromarray(decrypted_array.astype(np.uint8))
    decrypted_image.save(output_image_path)
    print(f"Image decrypted successfully! Saved as {output_image_path}")

def main():
    print("Image Encryption/Decryption Tool")
    
    input_image = input("Enter the input image file name (e.g., image.jpg): ")
    shift_value = int(input("Enter the shift value for encryption (integer): "))
    
    operation = input("Do you want to (e)ncrypt or (d)ecrypt the image? ").lower()
    
    if operation == 'e':
        output_image = input("Enter the name for the encrypted output image (e.g., encrypted_image.jpg): ")
        encrypt_image(input_image, output_image, shift_value)
    elif operation == 'd':
        output_image = input("Enter the name for the decrypted output image (e.g., decrypted_image.jpg): ")
        decrypt_image(input_image, output_image, shift_value)
    else:
        print("Invalid choice! Please enter 'e' to encrypt or 'd' to decrypt.")

if __name__ == "__main__":
    main()
```

#### Save and Exit:
- Press `CTRL + O`, then Enter to save the file.
- Press `CTRL + X` to exit nano.
![image](https://github.com/user-attachments/assets/a900075c-1aef-4626-bb67-3075494302c8)
![image](https://github.com/user-attachments/assets/eecf4589-1187-46d8-bca5-f9c3e02971ce)


## Step 3: Running the Encryption and Decryption Process

### 3.1 Encrypting an Image
Run the Python script:

python3 image_encryption.py

**User Input for Encryption:**
```plaintext
Image Encryption/Decryption Tool
Enter the input image file name (e.g., image.jpg): Yungbizzy.jpg
Enter the shift value for encryption (integer): 30
Do you want to (e)ncrypt or (d)ecrypt the image? e
Enter the name for the encrypted output image (e.g., encrypted_image.jpg): yung.jpg
![image](https://github.com/user-attachments/assets/0f6906ad-656b-42c2-b9cd-d8c22e6798da)


![image](https://github.com/user-attachments/assets/a99e8a25-d6e5-4789-b228-0169483c621b)


### 3.2 Decrypting an Image
Run the Python script again:
python3 image_encryption.py
**User Input Decryption:**
Image Encryption/Decryption Tool
Enter the input image file name (e.g., image.jpg): yung.jpg
Enter the shift value for encryption (integer): 30
Do you want to (e)ncrypt or (d)ecrypt the image? d
Enter the name for the decrypted output image (e.g., decrypted_image.jpg): Yungbizy.jpg
![image](https://github.com/user-attachments/assets/cd22a9b4-d896-4fad-a0f6-6b4e2a7e02e9)


## 5. Observations and Results
1. The encrypted image (`yung.jpg`) was visually altered, indicating successful encryption.
2. The decrypted image (`Yungbizy.jpg`) was identical to the original image, proving that the decryption process successfully restored the original data.
3. Different shift values resulted in varying levels of encryption intensity.
4. The method worked efficiently for various image formats, including `.jpg` and `.png`.


## 6. Recommendations
1. **Use Stronger Encryption Techniques:** While pixel shifting provides basic encryption, integrating cryptographic algorithms like AES or RSA would improve security.
2. **Increase Randomization:** Instead of a fixed shift value, a random shift pattern could enhance encryption strength.
3. **Enhance User Interface:** A GUI-based application would improve usability over the command-line interface.
4. **Automate Key Management:** Securely storing and managing encryption keys would ensure better protection against unauthorized access.

## 7. Conclusion
This project successfully demonstrated image encryption and decryption using pixel manipulation. The shift-based approach effectively altered pixel values to protect image content. While the implementation was simple, it provided a foundation for more advanced encryption techniques in digital image security. Future improvements could involve integrating cryptographic standards and developing a more user-friendly application.
