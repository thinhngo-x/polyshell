# PolyShell

## Objective

The PolyShell project addresses **Challenge 31 - PolyShell** within the ECMWF Code for Earth 2025 initiative. The core objective of this challenge is to **design and implement a new algorithm to approximate concave polygon shapes with simpler polygons, while ensuring the simplified polygon completely encompasses the original shape**.

This need arises from the implementation of ECMWF's new data retrieval service, Polytope, which can become inefficient when handling 2-dimensional polygons defined by a large number of vertices. While many line reduction algorithms exist (such as the **Ramer-Douglas-Peucker algorithm**), they often fail to consistently overestimate the approximated shape, especially for concave polygons.

Therefore, PolyShell aims to develop an alternative line reduction algorithm with the **key property that the output always completely encompasses the input shape**, while maintaining the overall shape and concavities of the input polygon. Furthermore, given that shape extractions are expected to take only a few seconds, the algorithm must also be **very efficient**. The final implementation of this algorithm is intended to be in **Rust** for high performance.

## Code in `polyshell_demo.ipynb`

The `polyshell_demo.ipynb` notebook (summarized in our conversation history) provides a **Python-based exploration and implementation of several functionalities related to polygon manipulation and simplification**. It serves as a **prototyping and experimentation platform** for developing the core ideas behind the PolyShell project.

The notebook includes the following key functionalities:

*   **Polygon Orientation:** Determines if a polygon's vertices are ordered clockwise or counter-clockwise using the **shoelace formula**.
*   **Concave Vertex Identification:** Identifies concave vertices in a polygon based on the cross product of consecutive edges.
*   **Visvalingam-Whyatt Simplification:** Implements the **Visvalingam-Whyatt algorithm**, which simplifies a polygon by iteratively removing vertices that form triangles with the smallest area.
*   **Random Concave Polygon Generation:** Provides a method to generate random concave polygons with adjustable parameters.
*   **Visualization:** Includes a function to visualize Shapely polygons, allowing for comparison between original and simplified versions using **Matplotlib**.

**Potential improvement**

* Optimize the `visvalingam_whyatt` function to improve performance:
    * Use Binary Heap to store the triangles and their areas to quickly find the triangle with the smallest area.
    * Update only the affected triangles when a vertex is removed, instead of recalculating all triangles.
* Implement Rumer-Douglas-Peucker with the integration of convex vertices identification.
* Rewrite in Rust for better performance.