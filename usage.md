To import the package in your code, use:
```
    import "code.google.com/p/lzma"
```


---

Usage examples. Write compressed data to a buffer:
```
 var b bytes.Buffer
 w := lzma.NewWriter(&b)
 w.Write([]byte("hello, world\n"))
 w.Close()
```
and read it back:
```
 r := lzma.NewReader(&b)
 io.Copy(os.Stdout, r)
 r.Close()
```


---

If the data is bigger than you'd like to hold into memory, use pipes. Write
compressed data to an io.PipeWriter:
```
 pr, pw := io.Pipe()
 go func() {
     defer pw.Close()
     w := lzma.NewWriter(pw)
     defer w.Close()
     // the bytes.Buffer would be an io.Reader used to read uncompressed data from
     io.Copy(w, bytes.NewBuffer([]byte("hello, world\n")))
 }()
```
and read it back:
```
 defer pr.Close()
 r := lzma.NewReader(pr)
 defer r.Close()
 // the os.Stdout would be an io.Writer used to write uncompressed data to
 io.Copy(os.Stdout, r)
```


---

For more examples, see the `*_test.go` files in the <a href='http://code.google.com/p/lzma/source/browse'>root folder</a> and the `lzma_go` demo tool in the <a href='http://code.google.com/p/lzma/source/browse/lzma_go'>lzma_go folder</a>.