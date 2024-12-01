## Few important steps before you begin

* create a Couchbase Capella db with search, index and query services (a free account will work!)
* create a bucket named 'hello' with default scope and collection
* create the application credentials (application / Pwd12345!)
* whitelist your public IP (go wild! go 0.0.0.0/0!) 
* import with `cbimport json --format list -c couchbase://<your capella url> -u application -p Pwd12345! -b hello -d file://path/to/this/repo/generated_db_export.json `
* create a PRIMARY index (CREATE PRIMARY INDEX on `hello.`_default`.`default`)
* import in the search console the vector index definition `hello._default.products_emb_idx.json`
* An API_KEY from OpenAI:
* * Mandatory for summurization (you can skip this, it's already done when you import the data)
  * Creation of embeddings (you can skip this, it's already done like the one before)
  * Vector search demo (from `Run a semantic search query on the processed reviews` on)
  
