- #论文
- ### Main Techniques Used in CLIP-NeRF
  
  **CLIP-NeRF** combines several advanced techniques to enable text-and-image driven manipulation of Neural Radiance Fields (NeRF). Here are the main techniques used:
  
  1. **Contrastive Language-Image Pre-Training (CLIP)**: CLIP is used to leverage the joint language-image embedding space, allowing the model to understand and manipulate 3D objects based on text prompts or exemplar images¹.
  
  2. **Disentangled Conditional NeRF Architecture**: This architecture allows for individual control over both shape and appearance. Shape conditioning is achieved by applying a learned deformation field to the positional encoding, while color conditioning is deferred to the volumetric rendering stage¹.
  
  3. **Code Mappers**: Two code mappers are designed to bridge the CLIP embedding with the latent codes of NeRF. These mappers take a CLIP embedding as input and update the latent codes to reflect the targeted editing¹.
  
  4. **CLIP-Based Matching Loss**: This loss function ensures the manipulation accuracy by aligning the edited NeRF output with the desired text or image input¹.
  
  5. **Inverse Optimization Method**: This method accurately projects an input image to the latent codes for manipulation, enabling editing on real images¹.
  
  These techniques collectively enable CLIP-NeRF to perform intuitive and precise 3D object manipulations using natural language and images.
- Source: Conversation with Copilot, 10/13/2024
  (1) [2112.05139] CLIP-NeRF: Text-and-Image Driven Manipulation of Neural .... https://arxiv.org/abs/2112.05139.
  (2) CVPR2022: CLIP-NeRF: Text-and-Image Driven Manipulation of ... - GitHub. https://github.com/hha2001/CLIPNeRF/blob/main/README.md.
  (3) GitHub - cassiePython/CLIPNeRF: CLIP-NeRF: Text-and-Image Driven .... https://github.com/cassiePython/CLIPNeRF.
  (4) undefined. https://doi.org/10.48550/arXiv.2112.05139.