Lucene-Index-Search-Example
===========================

This is a simple example of how to use apache lucene to index and search a directory.

Currently, the application is set to index files ending in "java" which can be changed in the main method of Indexer.java
```java
public static void main(String[] args) throws Exception {
	//lucene index directory
	Directory directory = FSDirectory.open(
				new File("/Users/julespaulynice/Documents/luna/index")
				);
	
	//directory to index
	File dataDir = new File("/Users/julespaulynice/Documents/workspace");
	
	//file types
	String suffix = "java";

	FileIndexer indexer = new FileIndexerImpl();

	int numIndex = indexer.index(directory, dataDir, suffix);

	System.out.println("Total files indexed " + numIndex);
}
```

Several indexing files are then created.  

Then using Searcher.java class, we search for "lucene" and list the file paths that match our query.

```java
public static void main(String[] args) throws Exception {
	//lucene index directory
	File indexDir = new File("/Users/julespaulynice/Documents/luna/index");
	Directory directory = FSDirectory.open(indexDir);

	//query string
	String query = "lucene";
	
	//top hits
	int hits = 100;

	FileSearcher searcher = new FileSearcherImpl();
	searcher.searchIndex(directory, query, hits);
}
```
