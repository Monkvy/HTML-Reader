# HTML-Reader
Read HTML data and convert it into python classes.
There are bugs when you're trying to read data from nested elements. Maybe i'll fix it later.


## Installation
From PyPi:

```shell
pip install HTML-Reader
```
From Github Repo:

```shell
pip install git+https://github.com/Monkvy/HTML-Reader
```


## Usage

### Get elements by class, id, src, etc.
* Open a HTML-File or create a string with HTML code.
* Get HTML-Element by calling Element.Get() and insert a keyword.

Example HTML-File "example.html":
```HTML
<div class="content">
	<h1 class="title">Example title</h1>
	<p>
		Lorem ipsum dolor sit amet, 
		consetetur sadipscing elitr, sed diam
	</p>
</div>
```
Python Code:
``` Python
import HTMLReader

with open("example.html", "r") as file:
	raw_html = file.read()
	title = HTMLReader.Element.Get(raw_html, "class=\"title\"")[0]
	
	print(title.content)
```
Output:
```shell
Example title
```

### Get elements by tag
* Open a HTML-File, created in the example above.
* Get HTML-Element by calling Element.GetWithTag() and insert a tag.

``` Python
import HTMLReader

with open("example.html", "r") as file:
	raw_html = file.read()
	title = HTMLReader.Element.GetWithTag(raw_html, "p")[0]
	
	print(title.content)
```
Output:
```shell
Lorem ipsum dolor sit amet, 
consetetur sadipscing elitr, sed diam
```

### Other utilities

* ReplaceMultStr() replaces mutiple substrings of a string:
	``` python
	string = "Hello World"
	new_string = ReplaceMultStr(string, ["He", "ld"], "")
	print(new_string)
	```
	Output:
	``` shell
	llo Wor
	```

* RemoveBetweenChar() removes all substrings between the given chars:
	``` python
	string = "He$TEST$llo World%Remove me%"
	new_string = RemoveBetweenChar(string, ["$", "%"])
	print(new_string)
	```
	Output:
	``` shell
	Hello World 
	```

* FindIndexReverse() get the distance of a char to the given index (offset):
	``` python
	string = "Hello W$orld"
	o_index = HTMLReader.FindIndexReverse(string, "o", string.index("$"))
	print(string[o_index])
	```
	Output:
	``` shell
	o
	```
