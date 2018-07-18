---
title: CA3075：不安全的 DTD 處理
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 821a2a3f50f94808482d50a8e1e36feefb184173
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922425"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075：不安全的 DTD 處理
|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 如果您使用不安全的 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> 執行個體或參考外部實體來源，剖析器可能會接受未受信任的輸入，而將機密資訊洩漏給攻擊者。

## <a name="rule-description"></a>規則描述
 A*文件類型定義 (DTD)* 所定義 XML 剖析器可以判斷文件中，有效性的兩種方式之一是[World Wide Web Consortium (W3C) 可延伸標記語言 (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)。 此規則會搜尋已接受不受信任之資料的屬性和執行個體，藉此警告開發人員潛在的 [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) 威脅，這些威脅可能會導致 [Denial of Service (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) 攻擊。 下列情況會觸發此規則：

-   <xref:System.Xml.XmlReader> 執行個體上已啟用 DtdProcessing，它會使用 <xref:System.Xml.XmlUrlResolver>解析外部 XML 項目。

-   XML 中有設定 <xref:System.Xml.XmlNode.InnerXml%2A> 屬性。

-   <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> 屬性設定為 Parse。

-   使用 <xref:System.Xml.XmlResolver> 來處理未受信任的輸入，而不是 <xref:System.Xml.XmlSecureResolver> 。

-   XmlReader。<xref:System.Xml.XmlReader.Create%2A> 方法會叫用不安全<xref:System.Xml.XmlReaderSettings>執行個體或所有執行個體。

-   <xref:System.Xml.XmlReader> 會透過不安全的預設值或值。

 上述每個案例皆會造成一樣的結果：如果內容是來自處理 XML 之電腦的檔案系統或網路共用，這些內容就會公開給攻擊者，而被用來當做 DoS 向量。

## <a name="how-to-fix-violations"></a>如何修正違規

-   妥善捕捉並處理所有 XmlTextReader 例外狀況，以避免路徑資訊外洩。

-   使用 <xref:System.Xml.XmlSecureResolver> 來限制 XmlTextReader 可以存取的資源。

-   藉由將 <xref:System.Xml.XmlReader> 屬性設為 <xref:System.Xml.XmlResolver> null **，來禁止**開啟外部資源。

-   請確認 <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> 的 <xref:System.Data.DataViewManager> 屬性是從受信任的來源位置指派。

 .NET 3.5 和更早的版本

-   如果您正在處理不受信任的來源，請將 <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> 屬性設為 **true** 以停用 DTD 處理。

-   XmlTextReader 類別具有完全信任的繼承要求。

 .NET 4 和更新版本

-   請避免啟用 DtdProcessing，如果您正在處理未受信任來源，藉由設定<xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType>屬性**禁止**或**忽略**。

-   請確認在所有 InnerXml 案例中 Load() 方法皆會使用 XmlReader 執行個體。

> [!NOTE]
>  此規則可能會在一些有效的 XmlSecureResolver 執行個體上出現誤判報告。 我們會努力在 2016 年中旬前解決此問題。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您無法確定輸入是否來自受信任的來源，請不要隱藏這個警告的規則。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>違規

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>違規

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>違規

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>違規

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>違規

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>方案

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>違規

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```