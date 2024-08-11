# Problem Statement - 1 : Regularize Curves

## Introduction
This project focuses on detecting and regularizing various shapes from hand-drawn doodles and curves. The goal is to transform irregular shapes into their idealized forms while accurately identifying the shape types. The approach combines geometric properties and computational techniques to achieve this.

## Methodology
### Detection

1. Convex Hull: Approximates the shape's boundary, aiding in calculations of perimeter and area for shape identification.
2. Aspect Ratio Calculation: Determines width-to-height ratio, useful for distinguishing rectangles from other shapes.
3. Vertex Count: Identifies polygons and regular shapes based on the number of vertices, aiding in the detection of stars and polygons.
4. Angle Calculation: Measures angles between points to identify shapes with distinct features like stars.
5. Compactness and Perimeter: Evaluates how closely a shape resembles a circle by comparing area to perimeter ratio.
6. Least Squares and RDP: Techniques similar to Bezier curve fitting are used for regularizing shapes, though not explicitly employed.

### Regularization

1. Circle Regularization: Determines the circle's radius from the centroid and adjusts it to fit the detected dimensions.
2. Rectangle Regularization: Scales the rectangle to match detected width and height, ensuring it fits within specified dimensions.
3. Ellipse Regularization: Uses EllipseModel from skimage to fit an ellipse to the points, generating a regularized ellipse.
4. Polygon Regularization: Constructs a regular polygon based on average radius and centroid, approximating irregular polygons.
5. Star Regularization: Forms a star shape by alternating outer and inner radii, creating a regular star with a specified number of points.
6. Line Regularization: Ensures lines are straight and connected, adjusting them to fit within the bounding box and extending or shortening segments as needed.
7. Bezier Curve Fitting: Utilizes splprep and splev from scipy to fit a smooth Bezier curve to complex shapes for regularization.

## Results

We analyzed the following datasets for regularization:

1. **isolated**
   ![Screenshot (17)](https://github.com/user-attachments/assets/747b6f20-0a79-45b1-b188-0526eab3874f)

2. **frag1**

   ![Screenshot (18)](https://github.com/user-attachments/assets/a4f654bf-c483-421b-9370-a93a90826793)

3. **frag2**

   ![Screenshot (19)](https://github.com/user-attachments/assets/6940c866-ad53-4cdf-9b2f-e1cb82cc6655)


## Conclusion
The implemented algorithms and methods provide a robust framework for detecting and regularizing shapes from doodles. By leveraging geometric properties and computational techniques, the project effectively transforms irregular shapes into well-defined forms. The use of libraries like NumPy, Pandas, SciPy, scikit-image, and OpenCV ensures precise shape detection and regularization, making the approach both accurate and efficient.

# Problem Statement - 2 : Exploring Symmetry in Curves

## Introduction
In this project, we aimed to identify and analyze the symmetry properties of various 2D shapes and curves. We started by examining sample shapes and checking them for different types of symmetry, including vertical, horizontal, diagonal, reflective, and rotational symmetry. We then moved on to working with polylines and Bézier curves, investigating the symmetry of individual curves and the overall shape formed by the collection of curves.

## Methodology

### Sample Shapes
We began by considering sample shapes and checking them for various types of symmetry:

1. **Vertical Symmetry**: For each point (x, y), we checked if the point (-x, y) existed in the shape.
2. **Horizontal Symmetry**: For each point (x, y), we checked if the point (x, -y) existed in the shape.
3. **Diagonal Symmetry**: For each point (x, y), we checked if the point (y, x) existed in the shape.
4. **Reflective Symmetry**: We checked for symmetry about the y-axis by verifying if for each point (x, y), the point (-x, y) existed in the shape.
5. **Rotational Symmetry**: We checked for symmetry about the origin by verifying if for each point (x, y), the point (-x, -y) existed in the shape.

### Polylines and Bézier Curves
Next, we worked with polylines and Bézier curves. We checked the symmetry of individual curves and the overall shape formed by the collection of curves:

1. **Individual Curve Symmetry**: For each Bézier curve defined by control points (P0, P1, P2, P3), we checked for reflective symmetry about the y-axis and rotational symmetry about the origin.
2. **Overall Shape Symmetry**: We checked the entire shape formed by the collection of Bézier curves for reflective symmetry about the y-axis and rotational symmetry about the origin.

## Results

We analyzed the following datasets for symmetry:

1. **frag01**

   ![image](https://github.com/user-attachments/assets/dd9fcb7b-eeff-4d80-b346-4e79292e1f87)
   ![image](https://github.com/user-attachments/assets/9c199c1f-c8c8-418b-a4ed-6690a7668f9a)


2. **frag2**

   ![image](https://github.com/user-attachments/assets/f26b73f2-6bf1-4b88-8526-6ffd1ff17333)
   ![image](https://github.com/user-attachments/assets/65fcbbf8-50b4-4e00-b4d3-ed0e04bc2895)

4. **isolated**

   ![image](https://github.com/user-attachments/assets/bed4bfa5-1491-4d1d-9de8-a5699d2b4157)
   ![image](https://github.com/user-attachments/assets/95473b85-05ce-41f9-83b8-7e4a644d6a7b)


6. **occlusion1**

   ![image](https://github.com/user-attachments/assets/707363b6-082e-4ab9-9156-d3b55dd94dd6)
   ![image](https://github.com/user-attachments/assets/5fc4c0ae-fdbb-475f-950d-8135e4c8304f)


8. **occlusion2**

    ![image](https://github.com/user-attachments/assets/22cfa379-759e-472c-aa68-04e9ed348fdd)
    ![image](https://github.com/user-attachments/assets/974a137a-510b-4295-a2bb-52ec8deaf82e)



Our analysis revealed that all the individual Bézier curves in these datasets exhibited reflective symmetry about the y-axis and rotational symmetry about the origin. However, when considering the overall shape formed by the collection of curves, not all shapes were symmetric.

## Conclusion
In this project, we successfully implemented algorithms to identify various types of symmetry in 2D shapes and curves. We started with sample shapes and then moved on to analyzing polylines and Bézier curves. Our findings suggest that while individual Bézier curves may exhibit symmetry, the overall shape formed by a collection of curves may not necessarily be symmetric.

This project serves as a foundation for further exploration of symmetry in curves and shapes, with potential applications in areas such as computer graphics, image processing, and pattern recognition.


# Problem Statement - 3: Occlusion Detection and Shape Simplification

## Introduction

In this project, we aimed to detect and simplify shapes with occlusions in 2D datasets. The objective was to identify incomplete shapes, fill the gaps, and simplify the shapes while preserving their geometric integrity. By applying advanced algorithms like the RDP simplification and Bezier curve fitting, the project provides a robust approach to handling and processing complex shape data.

## Methodology

### Occlusion Detection

We started by analyzing the shape data to detect occlusions—gaps or missing parts in the shapes:

1.  **RDP Simplification**: We used the Ramer-Douglas-Peucker (RDP) algorithm to reduce the complexity of the shape paths while preserving the key geometric features. This simplification process made it easier to identify and fill occlusions.
    
2.  **Convex Hull Filling**: For shapes identified with occlusions, we applied a convex hull algorithm to fill the gaps, ensuring the shapes were continuous and connected.
    

### Shape Simplification and Fitting

After detecting and filling the occlusions, we simplified the shapes further:

1.  **Bezier Curve Fitting**: We applied Bezier curves to smooth out the shapes, creating more visually appealing and simplified representations of the original shapes.
    
2.  **Connectivity Analysis**: We analyzed the connectivity of the shapes before and after the occlusion filling process to ensure the shapes formed a single, cohesive structure without gaps or breaks.
    

## Results

We analyzed the following datasets for occlusions and simplifications:

1.  **occlusion1**
  ![Dataset Image 1](https://raw.githubusercontent.com/Violetcv/adobe-gensolve-team_IGDTUW/main/Occlusion_PS3/occlusion1.png?token=GHSAT0AAAAAACUCSOCLKKLVN27AMXCAHFF6ZVY6NKQ)  
     ![Dataset 1 Solution](https://raw.githubusercontent.com/Violetcv/adobe-gensolve-team_IGDTUW/main/Occlusion_PS3/occlusion1_sol.png?token=GHSAT0AAAAAACUCSOCK7ZPPQMXO5VX6LRXUZVY6N7A)
  



  
2.  **occlusion2**![Dataset Image 2](https://raw.githubusercontent.com/Violetcv/adobe-gensolve-team_IGDTUW/main/Occlusion_PS3/occlusion2.png?token=GHSAT0AAAAAACUCSOCLSZMEPFE27KG6G4AAZVY6O2A)
    
    ![Dataset 2 Solution](https://raw.githubusercontent.com/Violetcv/adobe-gensolve-team_IGDTUW/main/Occlusion_PS3/occlusion2_sol.png?token=GHSAT0AAAAAACUCSOCK2DWAG4LO3ASUB5MEZVY6PGQ) 
    

Our analysis showed that the RDP algorithm effectively simplified the shapes, while the convex hull approach successfully filled the occlusions. The Bezier curve fitting further enhanced the shapes, resulting in smooth, connected structures. The connectivity analysis confirmed that the occlusion-filling process transformed disconnected shapes into connected ones.

## Conclusion

We developed a comprehensive approach to detect and fill occlusions in 2D shapes. The combination of RDP simplification, convex hull filling, and Bezier curve fitting provided a powerful tool for handling complex shape data. Our results demonstrated the effectiveness of this approach, transforming disconnected and incomplete shapes into cohesive, simplified structures.

This project serves as a foundation for further exploration of shape simplification and occlusion detection, with potential applications in fields such as computer graphics, image processing, and geometric modeling.
