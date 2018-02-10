---
title: "自訂 T4 文字轉換 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: db6d65c5dd0c79549516ff3b9c58b8b59c4be885
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-t4-text-transformation"></a>自訂 T4 文字轉換
文字範本是的功能[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可讓您產生程式碼或其他文字檔案，完成轉換程序。 使用[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]，您可以自訂文字範本指示詞處理器或文字範本主應用程式來延伸預設範本轉換流程。  
  
## <a name="in-this-section"></a>本節內容  
 [文字範本轉換流程](../modeling/the-text-template-transformation-process.md)  
 說明文字轉換的運作方式，並說明範本主應用程式和指示詞處理器的角色。  
  
 [建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 指示詞處理器會處理指示詞在範本中，例如`<#@template#>.`它執行範本，在編譯期間，可以載入組件和其他資源。 它也可以插入程式碼，將會載入在執行階段的資源。 藉由定義您自己的指示詞處理器，您可以減少您的範本的複雜性。  
  
 [叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 如果您要撰寫[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]擴充功能，例如功能表命令或事件處理常式，您的擴充功能可以使用文字範本化服務來轉換的任何文字範本。 您可以使用工作階段物件，將參數資料傳遞至範本，並從取得值的範本中使用`<#@parameter#>`指示詞。  
  
 [使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 文字範本的程式碼執行時，主機會提供存取外部的檔案和應用程式的狀態。 例如，主應用程式中執行文字轉換[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可存取方案總管 中。 它也會顯示錯誤訊息視窗中的錯誤。 如果您想要在不同的內容中執行文字轉換，您可以定義自己的主機可存取該內容中可用的服務。  
  
 如果您要撰寫[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]延伸模組，請考慮使用現有的文字轉換服務，而不撰寫自己的主機。 如需詳細資訊，請參閱[叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
## <a name="reference"></a>參考資料  
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)  
  
 提供的文字範本指示詞和控制區塊的語法。