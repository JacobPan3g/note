# Find

To convert file encode from GBK to UTF-8

```
find <dir> -type d -exec mkdir -p <utf dir>/{} \;
find <dir> -type f -exec bash -c "iconv -f GBK -t UTF-8 {} > <utf dir>/{}" \;
```

Above, `iconv -f GBK -t UTF-8 <file> > <out file>` can convert encode. In Linux, option `-o <out file>` can instead of `>`.

`{}` in the `find -exec` command represents each line of the output of `find`.
