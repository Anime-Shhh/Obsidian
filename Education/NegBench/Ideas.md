Similar to how the WAN diffusion model uses negative conditioning to provide more accurate, clear, and realistic diffusion images, something similar can be done for retrieval of negated queries. WAN tries to maximize the cosine angle between the embedding vector of the user query, and the embedding vector of the negation conditioning. In this case, it works since its just based off 2 vectors. but lets say you wanted to do something similar for retrieval models like clip where you queried for "pictures of cats with no dogs", but it keeps getting pictures of cats with pictures of dogs in the background. Since clip shares embedding space between image and text, could you in the same way generate the negation conditioning text, embed it, using semantic extraction, creating 2 embeddings "image of cats" and "no dogs". now in the same way, lets say the user wants 10 pictures, can we have the model do something like retrieve 1.2 x user_pic_count_request and then calculate the cosine similarity between those and then negative conditioning embedding. then return the top 10 images, which will result in minimizing misinterpretation of user queries and avoid misunderstanding of negation.

---
# Plan
## 1. CLIP embeddings and negative conditioning

CLIP maps text and images into a shared embedding space.  

**Positive query:** `"image of cats"` → embedding `v_pos`  

**Negative query:** `"no dogs"` → embedding `v_neg`  

Your idea: compute adjusted similarity for retrieval:

$$
\text{score}(I) = \cos(v_\text{img}, v_\text{pos}) - \alpha \cdot \cos(v_\text{img}, v_\text{neg})
$$

Where:  
- $v_\text{img}$ = embedding of candidate image  
- $\alpha$ = scaling factor for negative guidance  

This is exactly analogous to positive–negative conditioning in diffusion.

---
## 2. Retrieval workflow for multiple images

If the user wants \(k\) images (e.g., 10):  

1. Retrieve a larger candidate set: $k' = k \times 1.2$ (overfetching)  
2. Compute adjusted score for each candidate using the formula above  
3. Sort by descending adjusted score  
4. Return top $(k)$ images  

This helps reduce inclusion of unwanted elements (dogs) while keeping desired ones (cats).

---
## 3. How to generate the negative conditioning embedding

- **Option 1:** User-provided text: `"no dogs"`  
- **Option 2:** Semantic extraction / automated negation detection:  
  - NLP pipeline detects unwanted entities or attributes in the query  
  - Generates negative prompt embedding dynamically  
Example: `"cats without dogs, no toys"` → extract `"dogs, toys"` → embed → negative guidance