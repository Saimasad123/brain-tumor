# brain-tumor
This project implements a comprehensive brain tumor detection system developed in both MATLAB and Python using OpenCV. The system uses watershed segmentation and morphological operations to detect brain tumors in MRI images, with implementations in both environments for maximum flexibility and accessibility.
Features

    Grayscale Conversion: Converts MRI images to grayscale for processing
    Binary Thresholding: Creates binary images for segmentation
    Watershed Segmentation: Uses Sobel filters and watershed algorithm
    Morphological Processing: Detects tumor regions (displayed as WHITE areas)
    Otsu Thresholding: Alternative segmentation method
    Tumor Classification: Classifies tumors as Benign, Malignant, or No Tumor
    GUI Interface: User-friendly interface similar to the original MATLAB version

Installation

    Install Python dependencies:

pip install -r requirements.txt

    For Windows users, if tkinter is not available:

pip install tk

Usage
Method 1: Compact GUI (Recommended)

python brain_tumor_compact_gui.py

    Optimized for all screen sizes (900x600 minimum)
    Switch between different views using buttons
    Real-time results display

Method 2: Command Line with File Dialog

python brain_tumor_detection.py

    Select image through file dialog
    Results displayed in matplotlib window

Method 3: Test All Images

python test_detection.py

    Automatically processes all images in the current directory
    Saves results as PNG files

Key Differences from MATLAB Version
Tumor Visualization

    WHITE areas in the "Morphological Tumor" image represent detected tumor regions
    This matches the MATLAB implementation where tumor areas appear as white pixels

Processing Pipeline

    Load Image: Resize to 200x200 pixels
    Binary Image: Threshold at 0.6 (60%)
    Watershed: Apply Sobel filters and watershed segmentation
    Morphological Processing:
        Opening operation with disk kernel (radius 5)
        Reconstruction and dilation
        Final tumor mask (white = tumor)
    Thresholding: Otsu's method with small object removal
    Classification: Based on tumor area in cm²

Classification Criteria

    No Tumor: 0 cm²
    Benign Tumor: ≤ 2.37 cm²
    Malignant Tumor: > 2.37 cm²

File Structure

├── brain_tumor_detection.py       # Core detection class
├── brain_tumor_compact_gui.py     # Compact GUI application
├── test_detection.py              # Batch testing script
├── requirements.txt               # Python dependencies
├── README.md                      # This file
├── BrainMRI_GUI.m                 # Original MATLAB GUI
├── BrainTumor.mlx                 # Original MATLAB script
└── *.jpg, *.png, *.jpeg          # Sample MRI images

Technical Details
Morphological Operations

The system uses morphological operations to isolate tumor regions:

    Opening: Removes noise and small objects
    Reconstruction: Restores important structures
    Dilation: Expands tumor boundaries
    Complement: Inverts to highlight tumor areas as white

Watershed Segmentation

    Applies Sobel edge detection
    Calculates gradient magnitude
    Uses watershed algorithm for region segmentation

Area Calculation

    Pixel dimensions: 0.0508 cm × 0.0508 cm
    Converts pixel count to cm² for medical relevance

Sample Output

The system displays 6 images:

    Grayscale MRI: Original processed image
    Binary Image: Thresholded version
    Watershed Segmentation: Color-coded regions
    Morphological Tumor: WHITE areas indicate tumor
    Thresholding Segmentation: Otsu-based segmentation
    Analysis Results: Tumor area and classification

Troubleshooting
Common Issues

    Import Error: Install missing packages with pip install -r requirements.txt
    Tkinter Error: Install tkinter separately or use command-line version
    Image Loading Error: Ensure image files are in supported formats (PNG, JPG, JPEG)

Performance Notes

    Images are automatically resized to 200×200 pixels for consistent processing
    Processing time is typically under 2 seconds per image
    GUI updates in real-time after image selection

Credits
Original MATLAB and Python OpenCV implementations developed by "Rizwan Aleem Tahha | M Ahsan | Moiz Ahmed | Saim Asad" Both implementations maintain the same algorithm and produce consistent results across platforms
