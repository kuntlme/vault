#### **Sampling: Digitizing Spatial Coordinates**

- **Definition**: Sampling discretizes the spatial coordinates (x,y)(x,y) of an image. It involves measuring the intensity of the continuous image at discrete points (pixels) arranged in a grid.
    
- **Process**:
    
    - The image plane is divided into an M×NM×N grid (rows × columns).
        
    - The intersection of each row and column defines a **pixel** (picture element).
        
    - The value f(m,n)f(m,n) represents the intensity at pixel location (m,n)(m,n), where m=0,1,…,M−1m=0,1,…,M−1 and n=0,1,…,N−1n=0,1,…,N−1.
        
- **Effect on Resolution**:
    
    - **Spatial resolution** is determined by the number of samples (pixels). Higher sampling (more pixels) captures finer details but increases storage requirements.
        
    - Example: A 1024×10241024×1024 image has higher spatial resolution than a 512×512512×512 image.
        
- **Visualization**:
    
    - A continuous line segment ABAB in an image is sampled at equally spaced points. The density of these points dictates the sharpness of edges and details in the digital image









