Sentence window retrieval method
 steps
 1. Read PDF with the SimpleDirectoryReader 
 2. join the document to give better test blending accuracy 
 3. Split the document into individual sentences and then augument each sentence with the surrounding context with the SentenceWindowNode Parser (it contains the window size, window metadata and original sentence metadata).
 4. Build the index with the ServiceContext containig the llm, embedding model and the SentenceWindowNode Parser
 5. Setup the vector index. the vector index containd the service context and the original document
 6. build a Metadatareplacement postprocessor that replaces the chunks retrieved,  with the same chunk and its surrounding context stored  in the metadata when a query is exe.
 7. Use a SentenceTransformerRerank Model to filter out a smaller set of chunkss out of the top most similar chunks fetched from the similarity search engine.
 8. Evaluate with TruLens evaluation tool.