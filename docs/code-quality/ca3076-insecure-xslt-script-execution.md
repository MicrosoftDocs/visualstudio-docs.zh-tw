---
title: CA3076:不安全的 XSLT 指令碼執行
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d711aad69dbdf3295ca7b2962a2e2022bd259059
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891043"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076:不安全的 XSLT 指令碼執行

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因

如果您在 .NET 應用程式中以不安全的方式執行可延伸樣式表語言轉換 (XSLT)，處理器可能會解析不受信任的 URI 參考，而這些參考可能會將機密資訊洩漏給攻擊者，導致拒絕服務和跨網站攻擊。 如需詳細資訊，請參閱 < [XSLT 安全性 Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations)。

## <a name="rule-description"></a>規則描述

**XSLT** 是全球資訊網協會 (W3C) 針對 XML 資料轉換的一項標準。 XSLT 通常用來寫入 XML 將資料轉換成其他格式，例如 HTML、 固定長度的文字，以逗號分隔的文字或使用不同的 XML 格式的樣式表。 雖然預設為禁止使用，您仍可以針對專案選擇啟用此項目。

若要確保您不會公開受攻擊面，此規則會觸發每當 XslCompiledTransform。<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 接收的不安全組合執行個體<xref:System.Xml.Xsl.XsltSettings>和<xref:System.Xml.XmlResolver>，可讓惡意指令碼處理。

## <a name="how-to-fix-violations"></a>如何修正違規

- 不安全的 XsltSettings 引數取代為 XsltSettings。<xref:System.Xml.Xsl.XsltSettings.Default%2A> 或執行個體的已停用文件函式和指令碼執行。

- 將 <xref:System.Xml.XmlResolver> 引數取代為 null 或 <xref:System.Xml.XmlSecureResolver> 執行個體。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您無法確定輸入是否來自受信任的來源，請不要隱藏這個警告的規則。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>使用 XsltSettings.TrustedXslt 的違規

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
}
```

### <a name="solution-that-uses-xsltsettingsdefault"></a>使用 XsltSettings.Default 解決方案

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>違規&mdash;文件未停用的函式和指令碼執行

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>方案&mdash;停用文件函式和指令碼執行

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## <a name="see-also"></a>另請參閱

- [XSLT 安全性考量 （.NET 指南）](/dotnet/standard/data/xml/xslt-security-considerations)