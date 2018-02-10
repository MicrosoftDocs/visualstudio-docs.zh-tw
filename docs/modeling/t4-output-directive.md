---
title: "T4 輸出指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc226af7afb14d180dfdc823e293365df2a7a9ca
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="t4-output-directive"></a>T4 輸出指示詞
在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 文字範本中，`output` 指示詞用來定義轉換檔案的副檔名和編碼。  
  
 例如，如果您[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案包含名為的範本檔**MyTemplate.tt**其中包含下列指示詞：  
  
 `<#@output extension=".cs"#>`  
  
 然後[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]會產生名為**MyTemplate.cs**  
  
 在執行階段 (前置處理過的) 文字範本中，不需要 `output` 指示詞。 而是，您的應用程式會呼叫 `TextTransform()` 來取得產生的字串。 如需詳細資訊，請參閱[執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
## <a name="using-the-output-directive"></a>使用輸出指示詞  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 在每個文字範本中，不應該有多個 `output` 指示詞。  
  
## <a name="extension-attribute"></a>擴充屬性  
 指定所產生文字輸出檔案的副檔名。  
  
 預設值是**.cs**  
  
 例如：  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 可接受值：  
 任何有效的副檔名。  
  
## <a name="encoding-attribute"></a>編碼屬性  
 指定要在產生輸出檔案時使用的編碼。 例如：  
  
 `<#@ output encoding="utf-8"#>`  
  
 預設值是文字範本檔所使用的編碼。  
  
 可接受值：  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (系統預設值)  
  
 一般而言，您可以使用 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> 所傳回之任何編碼的 WebName 字串或 CodePage 號碼。