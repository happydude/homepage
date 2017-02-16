---
author: Jason Davis
layout: post
title: Scroll Elasticsearch with Elastica 5.0
---

Recently I needed to grab all of the items in an Elasticsearch index.
Elasticsearch 5.0 defaults to a limit of 10,000 results in a query.
Rather than trying to get around that limit it seemed like a good time to “do it right ™”.
I had a heck of a time figuring out how to scroll results with Elastica, a PHP client for elasticsearch.
So, on the off chance this is useful to someone or my future self, here is a working scroll query.

```php
<?php
//start with an Elastica client
$client = new \Elastica\Client(array('host'=>'localhost','port'=>'9200'));
//add the client to our search object
$search = new \Elastica\Search($client);
//filter on types, if we want
//$search->addTypes(['some_type']);
//create null query because I want everything
$query = new \Elastica\Query(null);
//pick the fields we want
$query->setStoredFields(['id','type']);
//limit the page size to one result because I want to be able to use getId() and getType() on every record
$query->setSize(1);
//add the query to the search object
$search->setQuery($query);
//return a scoll iterator with a 1 minute scroll timeout (the default),
//this is how long we have to make our next request before elasticsearch forgets us
$scrollIterator = $search->scroll('1m');
//Execute the search
$scrollIterator->rewind();

while ($scrollIterator->valid()) {
    //scroll takes care of fetching records when the foreach calls the next function
    foreach ($scrollIterator as $page) {
        $document = $page->current();

        echo $document->getId() . " " . $document->getType() . " \n";
    }
}
```
