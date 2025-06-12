# Docx



## 基础介绍

`.docx`是MicrosoftWord使用的默认文档格式，它基于OfficeOpenXML（OOXML）标准，本质上是一个结构化的ZIP压缩包，里面包含了多个XML文件及资源文件来描述Word文档的内容、结构、样式和资源等。



## 核心内容
```yaml
docx:
    /_rels: # 顶层关系文件
        .rels: # 定义顶层文件之间的引用关系，比如 document.xml 是主文档：
    /docProps: # 文档属性（作者、版本等）
        app.xml:
        core.xml:
        custom.xml:
    /word: # Word文档主体内容
        /_rels:
            document.xml.rels: #  正文引用资源的关系表（图片id、）
        /media: #  图片、视频等媒体资源
        /theme: #  主题样式
            theme1.xml:
        document.xml: #  正文内容（最重要）
        fontTable.xml: #  字体表
        numbering.xml: #  列表编号（有序/无序）
        settings.xml: #  页面设置、打印选项
        styles.xml: #  样式定义（字体、标题样式）
    [Content_Types].xml: # 文档内容类型定义
```

### [Content_Types].xml

描述整个包中所有文件的 类型（MIME）映射表


### document.xml
```yaml
<w:document>:
    <w:body>:
        <w:drawing>: # 图片
        <w:p>: # 段落（paragraph）
            <w:r>: # 文本运行（run，可能包含字体、加粗等）
                <w:t>: # 实际文本内容（text）
        <w:pStyle>: # 样式引用
        <w:sectPr>: # 页设置
        <w:tbl>: # 表格
            <w:tr>: # 表格行
                <w:tc>: # 单元格
```

文档的正文内容全部以 XML 标签结构组织。