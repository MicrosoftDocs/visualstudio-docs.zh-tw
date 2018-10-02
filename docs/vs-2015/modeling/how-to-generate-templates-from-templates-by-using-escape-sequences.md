---
title: 如何： 使用逸出序列從範本產生範本 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7cc523aed43dfbe3339c3f3cc054c09b39a4f060
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497724"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>如何：使用逸出序列從範本產生範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 產生的範本，從樣板藉由使用逸出序列](https://docs.microsoft.com/visualstudio/modeling/how-to-generate-templates-from-templates-by-using-escape-sequences)。  
  
您可以建立的文字範本會建立另一個文字範本，做為其產生的文字輸出。 若要這樣做，您必須使用逸出序列來描述文字範本標記。 如果您不使用逸出序列，產生的文字範本會有預先定義的意義。 如需文字範本中使用逸出序列的詳細資訊，請參閱[文字範本中使用逸出序列](../modeling/using-escape-sequences-in-text-templates.md)。  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>若要產生的文字範本內從文字範本  
  
-   使用反斜線 (\\) 當做逸出字元，產生的文字範本指示詞、 陳述式、 運算式、 內所需的標記和類別不同的文字範本檔案中的功能。  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## <a name="example"></a>範例  
 下列範例會使用逸出字元來產生文字範本，從文字範本。 `output`指示詞將目的地檔案類型設定為文字範本檔案類型 (.tt)。  
  
```csharp  
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



