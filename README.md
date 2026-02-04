# Project README: C++ Steganography Tool (BMP & PPM)

This project is a command-line utility developed in **C++20** for **Steganography**—the practice of hiding secret messages within digital images. The tool supports the Least Significant Bit (LSB) method for embedding data into `.bmp` and `.ppm` files without visibly altering the image.

---

## 🛠 Project Components

The application is structured as a modular C++ project, utilizing modern standards and external libraries for enhanced functionality.

### 1. Core Steganography Engine

The system implements LSB (Least Significant Bit) insertion across two major image formats:

* **BMP Processing (`processBMP.cpp`)**: Handles the complex structure of Bitmap files, including header parsing and pixel data manipulation.
* **PPM Processing (`processPPM.cpp`)**: Supports both "P3" (ASCII) and "P6" (Binary) portable pixmap formats.
* **Capacity Validation (`canWriteMessage.cpp`)**: A safety module that calculates the available space in an image (total pixels / 8 bits) to ensure the secret message can fit before starting the write process.

### 2. File Metadata & Information

Beyond hiding messages, the tool provides detailed file forensics:

* **Permissions**: Displays read/write/execute status.
* **Timestamps**: Reports last access, last modification, and status change times.
* **Image Specs**: Extracts and displays width, height, bits per pixel, and file size.

### 3. Build & Configuration

* **Build System**: Uses **CMake** (3.30+) for cross-platform compilation.
* **Dependencies**: Integrates the `{fmt}` library via `FetchContent` for high-performance string formatting.

---

## 🚀 How to Use

### Build Instructions

```bash
g++ -std=c++20 -o steganography main.cpp
# Or using CMake
cmake . && make

```

### Primary Commands

| Flag | Description | Example Usage |
| --- | --- | --- |
| `-i` | **Info**: Display image metadata | `./steganography -i image.bmp` |
| `-e` | **Encrypt**: Hide a message in an image | `./steganography -e image.ppm "Secret Text"` |
| `-d` | **Decrypt**: Extract a hidden message | `./steganography -d encoded_image.bmp` |
| `-c` | **Check**: Verify if a message fits | `./steganography -c image.bmp "Message"` |
| `-h` | **Help**: Show all available options | `./steganography -h` |

---

## 📂 File Manifest

* **`main.cpp`**: Entry point and command-line argument parser.
* **`canWriteMessage.cpp`**: Validation logic for storage capacity.
* **`CMakeLists.txt`**: Build configuration and dependency management.
* **`commands.txt`**: List of test cases and usage examples.
* **`FileInfo/`**: Sub-module for file system forensics (permissions, size, time).
* **`BMP/` & `PPM/**`: Dedicated encoders and decoders for each image format.
