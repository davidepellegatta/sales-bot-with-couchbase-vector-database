## Few important steps before you begin

* create a Couchbase Capella db with search, index and query services
* create a bucket named 'hello' with default scope and collection
* create the application credentials
* whitelist your public IP
* import with `cbimport json --format list -c couchbase://127.0.0.1 -u Administrator -p password -b hello -d file://generated_db_export.json `
* create a PRIMARY index
* import in the search console the vector index definition `hello._default.products_emb_idx.json`
* An API_KEY from OpenAI:
* * Mandatory for summurization (you can skip this, it's already done)
  * Creation of embeddings (you can skip this, it's already done)
  * Vector search demo (from `Run a semantic search query on the processed reviews` on)
  
