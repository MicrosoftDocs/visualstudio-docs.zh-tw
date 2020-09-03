---
title: CA3076：不安全的 XSLT 腳本執行 |Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b3e06bb7a150c4bb07eefc0571818f1127fe460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545115"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076:不安全的 XSLT 指令碼執行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|類別|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 如果您在 .NET 應用程式, 中執行 [ (XSLT) 的可擴充樣式表單語言轉換 ](https://support.microsoft.com/kb/313997) ，處理器可能會解析可能將機密資訊洩漏給攻擊者的 [不受信任 URI 參考](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) ，進而導致阻絕服務和跨網站攻擊。

## <a name="rule-description"></a>規則描述
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) 是全球資訊網協會 (W3C) 針對 XML 資料轉換的一項標準。 XSLT 通常用來撰寫可將 XML 資料轉換為其他格式的樣式表，例如 HTML、固定長度的文字、以逗號分隔的文字或不同的 XML 格式。 雖然預設為禁止使用，您仍可以針對專案選擇啟用此項目。

 為了確保您不會公開受攻擊面，此規則會在 XslCompiledTransform 時觸發。<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 接收與的不安全性群組合實例 <xref:System.Xml.Xsl.XsltSettings> <xref:System.Xml.XmlResolver> ，以允許惡意的腳本處理。

## <a name="how-to-fix-violations"></a>如何修正違規

- 使用 XsltSettings 取代不安全的 XsltSettings 引數。<xref:System.Xml.Xsl.XsltSettings.Default%2A> 或具有已停用檔功能和腳本執行的實例。

- 將 <xref:System.Xml.XmlResolver> 引數取代為 null 或 <xref:System.Xml.XmlSecureResolver> 執行個體。

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

### <a name="solution"></a>解決方法

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

### <a name="solution"></a>解決方法

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
