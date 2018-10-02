---
title: 'CA3077: API 設計、 XML 文件和 XML 文字讀取器中的不安全處理 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 175d655c2283dfe764564d42b6893b12d1f09e22
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588384"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077：API 設計、XML 文件和 XML 文字讀取器中的不安全處理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA3077： 設計、 XML 文件和 XML 文字讀取器中的不安全處理](https://docs.microsoft.com/visualstudio/code-quality/ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader)。

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 針對衍生自 XMLDocument 和 XMLTextReader 的 API 進行設計時，請留意 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>。  若在參考或解析外部實體來源時使用不安全的 DTDProcessing 執行個體，或在 XML 中設定不安全的值，都可能會導致資訊洩漏。

## <a name="rule-description"></a>規則描述
 A[文件類型定義 (DTD)](https://msdn.microsoft.com/library/aa468547.aspx)是下列其中一種 XML 剖析器用來判斷文件有效性所定義[World Wide Web Consortium (W3C) 可延伸標記語言 (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)。 此規則會搜尋屬性和執行個體不受信任的資料已接受的警告開發人員潛在[資訊洩漏](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c)威脅，這可能會導致[阻絕服務 (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600)攻擊。 下列情況會觸發此規則：

-   <xref:System.Xml.XmlDocument> 或<xref:System.Xml.XmlTextReader>類別針對 DTD 處理會使用預設解析程式的值。

-   未針對 XmlDocument 或 XmlTextReader 衍生的類別定義任何建構函式，或在 <xref:System.Xml.XmlResolver>中使用不安全的值。

## <a name="how-to-fix-violations"></a>如何修正違規

-   可以攔截並處理所有 XmlTextReader 例外狀況，正確地以避免路徑資訊外洩。

-   使用 <xref:System.Xml.XmlSecureResolver>而不是 XmlResolver，以限制 XmlTextReader 可以存取的資源。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您無法確定輸入是否來自受信任的來源，請不要隱藏這個警告的規則。

## <a name="pseudo-code-examples"></a>虛擬程式碼範例

### <a name="violation"></a>違規

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>方案

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```



