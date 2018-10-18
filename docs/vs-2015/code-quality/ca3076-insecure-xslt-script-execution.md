---
title: CA3076： 不安全的 XSLT 指令碼執行 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7143b7a13c5200071ee18975c94944b6a60359a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279886"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076：不安全的 XSLT 指令碼執行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 如果您在 .NET 應用程式中以不安全的方式執行 [Extensible Stylesheets Language Transformations (XSLT) (可延伸樣式表語言轉換 (XSLT))](https://support.microsoft.com/en-us/kb/313997) ，處理器可能會 [解析不受信任的 URI 參考](http://msdn.microsoft.com/en-us/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) ，而這些參考可能會將機密資訊洩漏給攻擊者，導致拒絕服務和跨網站攻擊。

## <a name="rule-description"></a>規則描述
 [XSLT](http://msdn.microsoft.com/en-us/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) 是全球資訊網協會 (W3C) 針對 XML 資料轉換的一項標準。 XSLT 通常用來撰寫可將 XML 資料轉換為其他格式的樣式表，例如 HTML、固定長度的文字、以逗號分隔的文字或不同的 XML 格式。 雖然預設為禁止使用，您仍可以針對專案選擇啟用此項目。

 若要確保您不會公開受攻擊面，此規則會觸發每當 XslCompiledTransform。<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 接收的不安全組合執行個體<xref:System.Xml.Xsl.XsltSettings>和<xref:System.Xml.XmlResolver>，可讓惡意指令碼處理。

## <a name="how-to-fix-violations"></a>如何修正違規

-   不安全的 XsltSettings 引數取代為 XsltSettings。<xref:System.Xml.Xsl.XsltSettings.Default%2A> 或執行個體的已停用文件函式和指令碼執行。

-   將 <xref:System.Xml.XmlResolver> 引數取代為 null 或 <xref:System.Xml.XmlSecureResolver> 執行個體。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您無法確定輸入是否來自受信任的來源，請不要隱藏這個警告的規則。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

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

### <a name="solution"></a>方案

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

### <a name="violation"></a>違規

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

### <a name="solution"></a>方案

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



