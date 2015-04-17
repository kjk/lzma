Project home for the `code.google.com/p/lzma` package ver. 1.0.0 and for the `code.google.com/p/lzma/lzma_go` tool.

The package code.google.com/p/lzma is a port of the lzma compression algorithm from <a href='http://www.7-zip.org/sdk.html'>LZMA SDK v4.65</a> to <a href='http://golang.org'>Go 1</a>.

See also <a href='http://code.google.com/p/lzma/wiki/go_get'>the installation instructions</a> and <a href='http://code.google.com/p/lzma/wiki/usage'>a couple of examples</a>.


NOTEs:

Only the lzma v1 compression algorithm is supported; the newer lzma v2 from LZMA SDK v9.xx came after this library was released.

The archiving formats 7z, xz (and others that use lzma internally) are also different beasts.