# Myers diff

This is an implementation of Myers diff algorithm, without the linear space refinment.

The algorithm therefore runs in O((M+N)D) in time and space, where:
* M, N are the sizes of the elements to diff
* D is the number of differences between them

## Example

The `diff` method can take any two sequences of objects. The only requirement is that the objects have the equality operator (`==`) defined.

```python
from diff.myers import diff, Operation

# the diff method returns a list of edits that
# turns the first sequence into the second
for edit in diff([1, 2, 3], [2, 3, 4]):
    if edit.operation == Operation.KEEP:
        print(f' {edit.data}')
    if edit.operation == Operation.INSERT:
        print(f'+{edit.data}')
    if edit.operation == Operation.DELETE:
        print(f'-{edit.data}')
```

Outputs:

```shell
-1
 2
 3
+4
```

## HTML generator

You can generate a pretty view of the diff using the `html` helper.

```python
from diff.html import create_html_diff

html = create_html_diff("ABCABBA", "CBABAC")
open("diff.html", "w").write(html)
```
