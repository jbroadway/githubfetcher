## GithubFetcher - PHP 5.3+ GitHub project fetching class

* Copyright: (c) 2012 Johnny Broadway
* License: http://www.opensource.org/licenses/mit-license.php

A very basic Github public project fetching tool. Uses v3 of the Github
API through CURL. Useful for quickly fetching a project from Github,
and much smaller than the full Github PHP client library.
    
### Usage:

```php
<?php

require 'GithubFetcher.php';

$github = new GithubFetcher ('git://github.com/codeguy/Slim.git');

// get all files/folders from the repository
$tree = $github->tree ();

$first_file = false

foreach ($tree as $item) {
	printf ("%s: %s\n", $item->type, $item->path);
	if (! $first_file && $item->type === 'blob') {
		$first_file = $item;
	}
}

// print the contents of the file
echo $github->get ($first_file);

?>
```
