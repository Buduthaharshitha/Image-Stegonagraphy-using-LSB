**🔐 Image Steganography using LSB Technique in C**

**Project Overview**
This project implements Image Steganography using the Least Significant Bit (LSB) technique in C programming. It enables secure embedding and extraction of secret text data inside a 24-bit BMP image without causing visible distortion.
Steganography is the technique of hiding confidential information within another digital medium such as an image, audio, or video file. In this implementation, secret text is embedded into a BMP image by modifying only the least significant bits of pixel values, ensuring the image appears visually unchanged.

**1.Objectives**
-Understand the concept of digital steganography
-Implement LSB-based data hiding technique
-Perform bit-level manipulation in C
-Develop modular C code for encoding and decoding
-Preserve image quality after embedding secret data

**2.Working Principle**
-In a 24-bit BMP image:
-Each pixel consists of 3 color channels (Red, Green, Blue)
-Each channel contains 8 bits
-Total = 24 bits per pixel
-The Least Significant Bit (LSB) is the rightmost bit in a byte
Example:-

Original byte:10110110
After embedding 1 bit of secret data:10110111
Since only the last bit changes, the difference is not noticeable to the human eye.

**3.Encoding Process (Hiding Data)**

-The encoding process works as follows:
  1.Open and validate the BMP image.
  2.Read the secret text file.
  3.Embed the following into image pixel data using LSB:
    ->Magic string (for decoding validation)
    ->File extension
    ->Secret file size
    ->Actual secret data
  4.Save the modified image as output.bmp.
The resulting image (stego image) visually looks identical to the original image.

**4. Decoding Process (Extracting Data)**

The decoding process performs the reverse operation:
  1.Open the stego image.
  2.Verify the magic string.
  3.Extract:
    ->File extension
    ->Secret file size
    ->Hidden data
  4.Reconstruct the original secret file (e.g., decoded.txt).
  
**5. Project Structure**

├── main.c        → Entry point & command-line handling.
├── encode.c      → LSB embedding implementation.
├── encode.h      → Encoding declarations.
├── decode.c      → LSB extraction implementation.
├── decode.h      → Decoding declarations.
├── common.h      → Shared structures & macros.
├── beautiful.bmp → Sample cover image.
├── secret.txt    → Sample secret message.

 **6.Compilation**
   Use GCC to compile:
    -> gcc main.c encode.c decode.c -o stego
    
**7.Execution**
  → Encoding
      ./stego -e beautiful.bmp secret.txt output.bmp
    Creates a new stego image (output.bmp) containing hidden data.

→ Decoding
    ./stego -d output.bmp decoded.txt
   Extracts hidden data and saves it into decoded.txt.

** Key Concepts Implemented**

-->Least Significant Bit (LSB) embedding

-->Bit masking and bitwise manipulation

-->Binary data processing

-->BMP header preservation

-->Command-line argument parsing

-->Modular C programming

**Applications**

-->Secure communication
-->Digital watermarking
-->Confidential data transfer
-->Cybersecurity applications
-->Military data concealment systems
