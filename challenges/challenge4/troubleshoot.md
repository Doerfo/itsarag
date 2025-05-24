## AttributeError: module 'its_a_rag.ingestion' has no attribute 'create_multimodal_vectore_store'

**Description:**  
This error occurs when calling `ingestion.create_multimodal_vectore_store`. The correct function name in the custom library is `create_multimodal_vector_store` (without the extra "e" in "vector").

**Fix:**  
- Change `create_multimodal_vectore_store` to `create_multimodal_vector_store` in your code.
- Ensure the argument names match the function signature in `ingestion.py`.

---

## Confusion: Should I check for images before calling `get_image_description`?

**Description:**  
You might wonder if you need to check `if the doc metadata is an image` before calling `ingestion.get_image_description(docs)`.

**Clarification:**  
You do **not** need to manually check for images before calling this function.  
The `get_image_description` function already inspects each document's metadata and separates images and texts accordingly.  
Just call `ingestion.get_image_description(docs)` directly with the retrieved documents.

**Reference:**  
See the implementation of `get_image_description` in `ingestion.py` for details.




