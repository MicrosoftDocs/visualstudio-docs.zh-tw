---
title: T4 輸出指示詞 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9262ec994ec847c38ec8d5c1ad95010a929cc4ba
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58945292"
---
# <a name="t4-output-directive"></a>T4 輸出指示詞
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 文字範本中，`output` 指示詞用來定義轉換檔案的副檔名和編碼。  
  
 例如，如果您[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]專案包含名為範本檔**MyTemplate.tt**其中包含下列指示詞：  
  
 `<#@output extension=".cs"#>`  
  
 然後[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]會產生名為**MyTemplate.cs**  
  
 在執行階段 (前置處理過的) 文字範本中，不需要 `output` 指示詞。 而是，您的應用程式會呼叫 `TextTransform()` 來取得產生的字串。 如需詳細資訊，請參閱 <<c0> [ 執行階段使用 T4 文字範本產生文字](../modeling/run-time-text-generation-with-t4-text-templates.md)。  
  
## <a name="using-the-output-directive"></a>使用輸出指示詞  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 在每個文字範本中，不應該有多個 `output` 指示詞。  
  
## <a name="extension-attribute"></a>擴充屬性  
 指定所產生文字輸出檔案的副檔名。  
  
 預設值是 **.cs**  
  
 例如：  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 可接受值：  
 任何有效的副檔名。  
  
## <a name="encoding-attribute"></a>編碼方式屬性  
 指定要在產生輸出檔案時使用的編碼。 例如:   
  
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
