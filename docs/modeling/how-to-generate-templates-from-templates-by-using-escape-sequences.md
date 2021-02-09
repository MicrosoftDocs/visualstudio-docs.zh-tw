---
title: 從文字模板產生文字模板
description: 提供有關如何使用 escape 序列從另一個文字模板產生文字模板的資訊。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: e3debeeafa55e483e9625c67534694debff6acfa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922788"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>如何：使用逸出序列從範本產生範本
您可以建立文字模板，以建立另一個文字模板作為其產生的文字輸出。 若要這樣做，您必須使用 escape 序列來描繪文字模板標記。 如果您未使用 escape 序列，則產生的文字模板將會有預先定義的意義。 如需在文字模板中使用 escape 序列的詳細資訊，請參閱 [在文字模板中使用 Escape 序列](../modeling/using-escape-sequences-in-text-templates.md)。

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>若要從文字模板內產生文字模板

- 使用反斜線 (\\) 作為 escape 字元，在個別的文字模板檔案中，于指示詞、語句、運算式和類別功能的文字模板內產生必要的標記標記。

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>範例
 下列範例會使用 escape 字元，從文字模板產生文字模板。 指示詞會 `output` 將目的地檔案類型設定為文字模板檔案類型 ( tt) 。

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
