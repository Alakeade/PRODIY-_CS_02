# Simple Image Encryption Tool

This repository provides a Python program to encrypt and decrypt images by modifying pixel values using a numeric key. It uses basic pixel manipulation techniques such as the XOR operation to ensure ease of use and flexibility.

## Features

- **Encrypt Images**: Modify pixel values using a key to make the image unreadable.
- **Decrypt Images**: Reverse the encryption process using the same key.
- Supports `.png`, `.jpg`, and other common image formats.

## Requirements

- Python 3.7 or higher
- `Pillow` library
- `numpy` library

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/image-encryption-tool.git
   ```
2. Navigate to the project directory:
   ```bash
   cd image-encryption-tool
   ```
3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Run the program:
   ```bash
   python image_encryption_tool.py
   ```
2. Follow the prompts to encrypt or decrypt an image:
   - Input the path to the image file.
   - Specify a numeric key (0-255).
   - Choose an encryption or decryption operation.

## Example

### Encryption
```plaintext
Simple Image Encryption Tool
1. Encrypt Image
2. Decrypt Image
Choose an option (1 or 2): 1
Enter the path to the input image: example.png
Enter the path to save the output image: encrypted_example.png
Enter a numeric key (0-255): 42
Image encrypted and saved to encrypted_example.png
```

### Decryption
```plaintext
Simple Image Encryption Tool
1. Encrypt Image
2. Decrypt Image
Choose an option (1 or 2): 2
Enter the path to the input image: encrypted_example.png
Enter the path to save the output image: decrypted_example.png
Enter a numeric key (0-255): 42
Image decrypted and saved to decrypted_example.png
```

## File Structure

- `image_encryption_tool.py`: Main script containing the encryption and decryption logic.
- `README.md`: Documentation for the project.
- `requirements.txt`: Lists the required Python libraries.

## Implementation

The tool works by reading the image's pixel values and applying a mathematical operation (XOR) with the user-provided key. The process is reversible, so the same key can be used to decrypt the image.

### Code Example
```python
from PIL import Image
import numpy as np

def encrypt_image(input_path, output_path, key):
    """Encrypt an image by modifying its pixel values."""
    image = Image.open(input_path)
    pixels = np.array(image)
    encrypted_pixels = pixels ^ key
    encrypted_image = Image.fromarray(encrypted_pixels.astype('uint8'))
    encrypted_image.save(output_path)

def decrypt_image(input_path, output_path, key):
    """Decrypt an image by reversing the encryption process."""
    image = Image.open(input_path)
    pixels = np.array(image)
    decrypted_pixels = pixels ^ key
    decrypted_image = Image.fromarray(decrypted_pixels.astype('uint8'))
    decrypted_image.save(output_path)
```
