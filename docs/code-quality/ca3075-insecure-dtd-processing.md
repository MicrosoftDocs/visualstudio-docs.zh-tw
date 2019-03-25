---
title: CA3075:不安全的 DTD 處理
ms.date: 03/18/2019
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de817e3aaecbdd1c89cc2174e91126ea39d99d7
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194615"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075:不安全的 DTD 處理

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

如果您使用不安全的 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> 執行個體或參考外部實體來源，剖析器可能會接受未受信任的輸入，而將機密資訊洩漏給攻擊者。

## <a name="rule-description"></a>規則描述

*文件類型定義 (DTD)* 是  [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)中針對 XML 剖析器用來判斷文件有效性所定義之兩種方式的其中一種。 此規則會搜尋屬性和執行個體不受信任的資料已接受的警告開發人員潛在[資訊洩漏](/dotnet/framework/wcf/feature-details/information-disclosure)威脅或[阻絕服務 (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service)攻擊。 下列情況會觸發此規則：

- <xref:System.Xml.XmlReader> 執行個體上已啟用 DtdProcessing，它會使用 <xref:System.Xml.XmlUrlResolver>解析外部 XML 項目。

- XML 中有設定 <xref:System.Xml.XmlNode.InnerXml%2A> 屬性。

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> 屬性設定為 剖析。

- 未受信任的輸入處理使用<xref:System.Xml.XmlResolver>而不是<xref:System.Xml.XmlSecureResolver>。

- <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType>方法會叫用不安全<xref:System.Xml.XmlReaderSettings>執行個體或完全沒有執行個體。

- <xref:System.Xml.XmlReader> 建立不安全的預設值或值。

在每個這種情況下，結果會是相同： 其中一個檔案系統或網路共用位置處理 XML 的機器的內容將會公開給攻擊者，或 DTD 處理可用來當做 DoS 向量。

## <a name="how-to-fix-violations"></a>如何修正違規

- 可以攔截並處理所有 XmlTextReader 例外狀況，正確地以避免路徑資訊外洩。

- 使用<xref:System.Xml.XmlSecureResolver>來限制 XmlTextReader 可以存取的資源。

- 藉由將 <xref:System.Xml.XmlReader> 屬性設為 <xref:System.Xml.XmlResolver> null **，來禁止**開啟外部資源。

- 請確認<xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A?displayProperty=nameWithType>屬性會被指派來自受信任的來源。

**.NET 3.5 和更早版本**

- 停用 DTD 處理，如果您正在處理不受信任的來源藉由設定<xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A>屬性，以 **，則為 true**。

- XmlTextReader 類別具有完全信任的繼承要求。

**.NET 4 和更新版本**

- 避免啟用 DtdProcessing，如果您正在處理不受信任的來源，藉由設定<xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType>屬性，以**禁止**或是**忽略**。

- 請確認在所有 InnerXml 案例中 Load() 方法皆會使用 XmlReader 執行個體。

> [!NOTE]
> 此規則可能會在一些有效的 XmlSecureResolver 執行個體上出現誤判報告。

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
    XmlReader reader = XmlReader.Create(sreader, new XmlReaderSettings() { XmlResolver = null });
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
            XmlReader reader = XmlReader.Create(stream, new XmlReaderSettings() { XmlResolver = null });
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
            XmlReader reader = XmlReader.Create(path, new XmlReaderSettings() { XmlResolver = null });
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
            XmlReaderSettings settings = new XmlReaderSettings() { XmlResolver = null };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```
