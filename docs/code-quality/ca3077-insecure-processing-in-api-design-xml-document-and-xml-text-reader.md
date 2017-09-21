---
title: "CA3077：API 設計、XML 文件和 XML 文字讀取器中的不安全處理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3077：API 設計、XML 文件和 XML 文字讀取器中的不安全處理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|分類|Microsoft.Security|  
|中斷變更|非中斷|  
  
## 原因  
 針對衍生自 XMLDocument 和 XMLTextReader 的 API 進行設計時，請留意 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>。  若在參考或解析外部實體來源時使用不安全的 DTDProcessing 執行個體，或在 XML 中設定不安全的值，都可能會導致資訊洩漏。  
  
## 規則描述  
 [文件類型定義 \(DTD\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) 是 [World Wide Web Consortium \(W3C\) Extensible Markup Language \(XML\) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/) 中針對 XML 剖析器用來判斷文件有效性所定義之兩種方式的其中一種。 此規則會搜尋已接受不受信任之資料的屬性和執行個體，藉此警告開發人員潛在的 [資訊洩露](../Topic/Information%20Disclosure.md) 威脅，這些威脅可能會導致 [Denial of Service \(DoS\)](../Topic/Denial%20of%20Service.md) 攻擊。 下列情況會觸發此規則：  
  
-   <xref:System.Xml.XmlDocument> 或 <xref:System.Xml.XmlTextReader> 類別針對 DTD 處理使用預設解析程式的值。  
  
-   未針對 XmlDocument 或 XmlTextReader 衍生的類別定義任何建構函式，或在 <xref:System.Xml.XmlResolver> 中使用不安全的值。  
  
## 如何修正違規  
  
-   妥善捕捉並處理所有 XmlTextReader 例外狀況，以避免路徑資訊外洩。  
  
-   使用  <xref:System.Xml.XmlSecureResolver> 而不是 XmlResolver，以限制 XmlTextReader 可以存取的資源。  
  
## 隱藏警告的時機  
 如果您無法確定輸入是否來自受信任的來源，請不要隱藏這個警告的規則。  
  
## 虛擬程式碼範例  
  
### 違規  
  
```c#  
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
  
### 方案  
  
```c#  
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