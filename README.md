# GROUP-16
Morphological-Based Object Counting in Binary Images
# Morphological-Based Object Counting in Binary Images

## Project Overview
This project demonstrates how morphological image processing techniques can be used to automatically detect and count objects in binary images. The approach mimics how humans visually separate objects from the background, but performs the task using computational methods.

## 1. Objectives
- Convert real-world images into binary representations
- Apply morphological operations to remove noise and enhance object shapes
- Count distinct objects using connected component analysis
- Evaluate the effectiveness and limitations of the approach

   
## 2. Theory: Morphological-Based Object Counting in Binary Images

### Binary Image
A binary image contains two pixel values: foreground (objects) and background.
We obtain it via thresholding:  
- If pixel intensity ≥ T → foreground (1 or 255)  
- Else → background (0)

### 2.1 Binary Image Formation

A grayscale image is converted into a **binary image** using thresholding:

\[
B(x,y) =
\begin{cases}
255, & I(x,y) \ge T \\
0, & I(x,y) < T
\end{cases}
\]

where:
- \(I(x,y)\) is the grayscale intensity
- \(T\) is the threshold value

In this project, **Otsu’s method** is used to automatically determine an optimal threshold.

### 2.2 Morphological Image Processing

Morphological operations analyze object shapes using a **structuring element**.

- **Erosion (\(A \ominus B\))**  
  Removes boundary pixels and small noise.

- **Dilation (\(A \oplus B\))**  
  Expands object boundaries and fills gaps.

- **Opening**  
  \[
  A \circ B = (A \ominus B) \oplus B
  \]  
  Removes small objects and noise.

- **Closing**  
  \[
  A \bullet B = (A \oplus B) \ominus B
  \]  
  Fills small holes within objects.

---

### 2.3 Object Counting Techniques
### Counting Idea
After producing a clean binary image, we can:
- Count connected components (separate blobs), OR
- Separate touching objects using distance transform + watershed, then count.
  
Two approaches are used:

1. **Connected Component Analysis**  
   Counts distinct connected foreground regions.

2. **Watershed Segmentation**  
   Separates touching objects using distance transform and marker-based segmentation.

### 2.4 Morphological Operations
Morphology uses a **structuring element** (kernel) to probe shapes.

1. **Erosion (⊖)**
Shrinks foreground objects by removing boundary pixels.
If B is the structuring element and A is the foreground set:
A ⊖ B = { x | B shifted to x is fully inside A }

2. **Dilation (⊕)**
Expands foreground objects by adding boundary pixels:
A ⊕ B = { x | (B shifted to x) intersects A }

3. **Opening**
Opening = Erosion then Dilation:
A ○ B = (A ⊖ B) ⊕ B  
Removes small noise and thin protrusions.

4. **Closing**
Closing = Dilation then Erosion:
A • B = (A ⊕ B) ⊖ B  
Fills small holes and gaps.


## 3. Implementation

### 3.1 Tools Used
- Python  
- OpenCV  
- NumPy  
- Matplotlib  
- Jupyter Notebook  


### 3.2 Methodology

The processing pipeline is as follows:

1. Load image from the `Images/` folder  
2. Convert image to grayscale  
3. Apply Gaussian blur to reduce noise  
4. Convert image to binary using Otsu thresholding  
5. Apply morphological opening and closing  
6. Perform connected component analysis  
7. Apply watershed segmentation for touching objects  
8. Count objects and measure execution time  
9. Display original and processed images  

The code is **modular, well-commented, and structured** for clarity.


## 4. Results

- **Real and publicly available images** were used.
- For each image, the notebook displays:
  - Original image
  - Binary image
  - Morphologically cleaned image
  - Connected component result and count
  - Watershed segmentation result and count
- Comparisons between **Connected Components** and **Watershed** results are included.
- Execution time is measured:
  - Per image
  - Per algorithm
  - Total runtime


## 5. Discussion
Morphological operations significantly improve counting accuracy by removing noise and separating objects. However, challenges arise when objects overlap or have low contrast with the background.
### 5.1 Analysis of Results

- Connected Component Analysis performs well when objects are clearly separated.
- It tends to **overcount** in the presence of noise.
- Watershed segmentation effectively separates **touching objects** but can undercount or over-segment if parameters are not well tuned.


### 5.2 Strengths
- Computationally efficient
- No training data required
- Easy to interpret
- Suitable for real-time applications in controlled environments


### 5.3 Limitations
- Sensitive to lighting conditions and shadows
- Requires parameter tuning
- Struggles with complex backgrounds and heavy overlap


### 5.4 Real-World Applications
- Agricultural produce counting
- Cell counting in medical imaging
- Industrial quality control
- Simple traffic or object monitoring systems


## 6. Documentation

- Code is clean, modular, and well-commented.
- The notebook contains:
  - Introduction
  - Theory
  - Methodology
  - Results
  - Discussion
  - Conclusion
- All project files are maintained in a GitHub repository.


## 7. Conclusion

This project demonstrates that **morphological image processing techniques** can be effectively used to count objects in images.  
By combining thresholding, morphological operations, and segmentation, reliable object counts can be obtained without machine learning, making the approach suitable for simple and efficient applications.The system successfully detects and counts objects across multiple image categories such as coins, grains, fruits, pills, and industrial components. Original and processed images are presented for comparison.


## 8. Applications
- Industrial quality control
- Agricultural produce counting
- Traffic and parking analysis
- Automated inspection systems

## 9. Image Sources
All images used in this project were obtained from publicly available and royalty-free sources from pexels.com and are used strictly for academic purposes.

## 10. Contributors
#### 1.**Aggrey Paintsil Ishmeal** - **11125864**  (Group Leader)
#### 2. **Addo Naa Shidaa Adjorkor** - **11307343**
#### 3.**Kelvin Kwaku Siaw Ashong** - **11296303**
#### 4.**Joshua Andoh-Mensah** - **11024515**
#### 5. **Raphae Quaye** - **11253474**
#### 6. **Benson Steve Fafa Kofi** - **11357947**
#### 7. **Nana Ampomah Arhin** - **11019735**
#### 8. **Abigail Akua Ninsin** - **11125864**

