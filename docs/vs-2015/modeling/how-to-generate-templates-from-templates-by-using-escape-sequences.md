---
title: 如何：使用 Escape 序列從範本產生範本 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 501b7f040cb841d19c06ccc8fe7615a5b4a5e70d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657338"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>如何：使用逸出序列從範本產生範本
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以建立文字模板，以建立另一個文字模板作為其產生的文字輸出。 若要這樣做，您必須使用 escape 序列來界定文字模板標記。 如果您不使用 escape 序列，則產生的文字模板會有預先定義的意義。 如需在文字模板中使用 escape 序列的詳細資訊，請參閱[在文字模板中使用 Escape 序列](../modeling/using-escape-sequences-in-text-templates.md)。

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>若要從文字模板內產生文字模板

- 使用反斜線（\\）做為逸出字元，以在個別的文字模板檔案中，為指示詞、語句、運算式和類別功能的文字模板中產生必要的標記標記。

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>範例
 下列範例會使用換用字元，從文字模板產生文字模板。 @No__t_0 指示詞會將目的地檔案類型設定為文字模板檔案類型（tt）。

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

 產生的文字輸出是文字模板。

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
