# pdf



## 基础介绍

PDF文件格式组成：（5个部分）
1. Header
2. Body（对象）
3. Cross-Reference Table（交叉引用表）
4. Trailer（尾部信息）
5. startxref（xref 起始偏移）
```csharp
%PDF-1.4
[Body]
xref
[Cross-reference table]
trailer
[Trailer dictionary]
startxref
123456
%%EOF
```

## 核心内容



### Header




### Body

#### Obj
```yaml
obj:
    Number: # 数字类型
    Bool: # 
    Null:
    String:
    Array: # [1 2 3]
    Map: # << /Type /Page >>
    Stream: # 二进制内容块, stream ... endstream
    Ref: # 间接引用，指向另一个对象	（13 0 R）
```



obj基础格式
```vb
[object-number] [generation-number] obj
    [object-body]
endobj
```



每一个 PDF 文件都是由多个 n m obj 的对象组成的对象图
```vb
PDF 文件
├── 1 0 obj: /Catalog
│   └── 2 0 obj: /Pages
│       └── 3 0 obj: /Page
│           └── 4 0 obj: /Contents (stream)
├── 6 0 obj: /Font
├── 10 0 obj: 图像 XObject
├── 20 0 obj: 表单字段
├── 30 0 obj: JavaScript
```


#### Catalog
```vb
1 0 obj
<< /Type /Catalog /Pages 2 0 R >>
endobj
```


#### Pages
```vb
2 0 obj
<< /Type /Pages /Kids [3 0 R] /Count 1 >>
endobj
```


#### Page
```vb
3 0 obj
<< /Type /Page /Parent 2 0 R /MediaBox [0 0 612 792] /Contents 4 0 R >>
endobj
```





#### Stream
```vb
4 0 obj
<< /Length 55 >>
stream
BT
/F1 12 Tf
100 700 Td
(Hello PDF) Tj
ET
endstream
endobj
```





内容流（如页面内容、图像、JS 脚本）



#### Font
```vb
6 0 obj
<< /Type /Font /Subtype /Type1 /BaseFont /Helvetica >>
endobj
```


#### XObject
```vb
10 0 obj
<< /Type /XObject /Subtype /Image /Width 100 /Height 100
   /ColorSpace /DeviceRGB /BitsPerComponent 8 /Filter /DCTDecode /Length 1234 >>
stream
...JPEG binary...
endstream
endobj
```


### XRef

Cross-Reference Table



### Trailer




### EOF