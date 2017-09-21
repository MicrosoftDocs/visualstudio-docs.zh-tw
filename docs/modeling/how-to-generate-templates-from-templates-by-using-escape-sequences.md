---
title: "如何：使用逸出序列從範本產生範本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, 從範本產生範本"
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 35
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 35
---
# 如何：使用逸出序列從範本產生範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以建立文字範本，以建立另一個文字範本做為產生的文字輸出。  若要這麼做，您必須使用逸出序列來描述文字範本標記。  如果沒有使用逸出序列，產生的文字範本就含有預先定義的意義。  如需在文字範本中使用逸出序列的詳細資訊，請參閱[使用文字範本中的逸出序列](../modeling/using-escape-sequences-in-text-templates.md)。  
  
### 若要從文字範本中產生文字範本  
  
-   使用反斜線 \(\\\) 做為逸出字元，在文字範本內產生必要的標記，以便在別的文字範本中提供指示詞、陳述式、運算式和類別等功能。  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## 範例  
 下列範例會使用逸出字元，從文字範本產生文字範本。  `output` 指示詞會將目的檔案類型設定為文字範本檔案類型 \(.tt\)。  
  
```c#  
\<#@ output extension=".tt" \#>  
\<#@ assembly name="System.Xml.dll" \#>  
\<#@ import namespace="System.Xml" \#>  
\<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {\#>  
           \<#= attr.Name \#>  
       \<#}  
     }  
\#>  
```  
  
 產生的文字輸出是文字範本。  
  
```  
<#@ output extension=".tt" #>  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {#>  
           <#= attr.Name #>  
       <#}  
     }  
#>  
```