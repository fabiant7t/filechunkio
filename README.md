# FileChunkIO
FileChunkIO represents a chunk of an OS-level file containing bytes data.
Python 2.6+ is required.

## Background
I wrote FileChunkIO to upload huge files to Amazon S3 in multiple parts
without having to split them physically upfront (which requires more time and
twice the disk space) or creating in-memory chunks as StringIO instances.

## Example
```python
>>> from filechunkio import FileChunkIO
>>> chunk = FileChunkIO('LICENCE', offset=646, bytes=201)
>>> chunk.read()
'THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR\nIMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,\nFITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.'
>>> chunk.tell()
201L
>>> chunk.seek(4)
>>> chunk.read(8)
'SOFTWARE'
>>> chunk.seek(0)
>>> chunk.readline()
'THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR\n'
```
