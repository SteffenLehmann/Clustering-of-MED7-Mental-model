
<!-- rnb-text-begin -->

---
title: "R Notebook"
output: html_notebook
---


<!-- rnb-text-end -->



<!-- rnb-text-begin -->



<!-- rnb-text-end -->



<!-- rnb-text-begin -->



<!-- rnb-text-end -->


<!-- rnb-chunk-begin -->


<!-- rnb-source-begin eyJkYXRhIjoiYGBgclxuI2dldCBsYWJlbHMgZm9yIGVhY2ggY2FyZFxuZGYubGFiZWxzID0gZGZbMToyXVxuI3RhYmxlKGRhdGEubGFiZWxzKVxuXG4jUmVtb3ZpbmcgdGhlIGxhYmVscyBmcm9tIHRoZSBkYXRhXG5jYXJkX2RhdGEgPC0gZGZbMzozM11cbiNGaWd1cmUgb3V0IGEgYmV0dGVyIG1ldGhvZCBmb3IgcmVtb3ZpbmcgY29sdW1ucyhUT0RPKVxuXG5jYXJkX2RhdGEkRGVzaWduLkFWIDwtIE5VTExcbmNhcmRfZGF0YSRQQkwuTWV0aG9kcy4gPC0gTlVMTFxuY2FyZF9kYXRhJERldmVsb3BtZW50LmFuZC5hbmFseXNpcyA8LSBOVUxMXG5cbiNzY2FsaW5nIHRoZSBkYXRhIG9yIG5vcm1hbGl6aW5nIGl0XG5DYXJkX2RhdGFfc2NhbGUgPC0gc2NhbGUoY2FyZF9kYXRhKVxuXG4jQ29tcHV0aW5nIHRoZSBkaXN0YW5jZS4gVGhpcyB3aWxsIGJlIHVzZWQgZHVyaW5nIHRoZSBjbHVzdGVyaW5nIGFzIGl0IGNvbXBhcmVzIGVhY2ggZGF0YSBwb2ludCdzIGRpc3RhbmNlIHRvIGEgY2VudHJvaWQuXG5jYXJkX2RhdGEgPC0gZGlzdChDYXJkX2RhdGFfc2NhbGUpXG5cbiNwcmluY2lwYWwgY29tcG9uZW50IGFuYWx5c2lzLCB3c3MgPSBXaXRoaW4gU3VtIHNxdWFyZXMuIFRoZSBsb25nZXN0IGludHJhIGNsdXN0ZXIgZGlzdGFuY2Vcbk9wdGltYWxfbnVtYmVyX29mX2NsdXN0ZXJzPC0gZnZpel9uYmNsdXN0KENhcmRfZGF0YV9zY2FsZSwga21lYW5zLCBtZXRob2QgPSBcIndzc1wiKSBcblxuI0ttZWFucyBjbHVzdGVyaW5nXG5LTUMgPC1rbWVhbnMoQ2FyZF9kYXRhX3NjYWxlLCBjZW50ZXJzID0gNiwgbnN0YXJ0ID0gMTAwLCBpdGVyLm1heCA9IDEwMCkgXG5cbiNQTG90dGluZyB0aGUgS21lYW5zIGNsdXN0ZXJzIGFuZCBhZGRpbmcgdGhlIGNhcmQgbmFtZXMobGFiZWxzKSBiYWNrIHRvIHRoZSBkYXRhIHNldFxuS21lYW5zLmNsdXN0ZXIgPC0gS01DJGNsdXN0ZXJcbnJvd25hbWVzKENhcmRfZGF0YV9zY2FsZSkgPC0gZGF0YSRDYXJkLm5hbWVcbmBgYCJ9 -->

```r
#get labels for each card
df.labels = df[1:2]
#table(data.labels)

#Removing the labels from the data
card_data <- df[3:33]
#Figure out a better method for removing columns(TODO)

card_data$Design.AV <- NULL
card_data$PBL.Methods. <- NULL
card_data$Development.and.analysis <- NULL

#scaling the data or normalizing it
Card_data_scale <- scale(card_data)

#Computing the distance. This will be used during the clustering as it compares each data point's distance to a centroid.
card_data <- dist(Card_data_scale)

#principal component analysis, wss = Within Sum squares. The longest intra cluster distance
Optimal_number_of_clusters<- fviz_nbclust(Card_data_scale, kmeans, method = "wss") 

#Kmeans clustering
KMC <-kmeans(Card_data_scale, centers = 6, nstart = 100, iter.max = 100) 

#PLotting the Kmeans clusters and adding the card names(labels) back to the data set
Kmeans.cluster <- KMC$cluster
rownames(Card_data_scale) <- data$Card.name
```

<!-- rnb-source-end -->

<!-- rnb-output-begin eyJkYXRhIjoiRXJyb3IgaW4gZGF0YSRDYXJkLm5hbWUgOiBvYmplY3Qgb2YgdHlwZSAnY2xvc3VyZScgaXMgbm90IHN1YnNldHRhYmxlXG4ifQ== -->

```
Error in data$Card.name : object of type 'closure' is not subsettable
```



<!-- rnb-output-end -->

<!-- rnb-chunk-end -->

