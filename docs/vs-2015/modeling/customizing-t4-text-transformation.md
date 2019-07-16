---
title: 自訂 T4 文字轉換 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ea2881cfebaf10d7a72e8651214cf3a6f64debae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164678"
---
# <a name="customizing-t4-text-transformation"></a>自訂 T4 文字轉換
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

文字範本特有的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，可讓您產生程式碼或其他文字檔案，完成轉換程序。 使用[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]，您可以擴充預設範本轉換流程自訂文字範本指示詞處理器或文字範本主應用程式。  
  
## <a name="in-this-section"></a>本節內容  
 [文字範本轉換流程](../modeling/the-text-template-transformation-process.md)  
 說明文字轉換的運作方式，並說明範本主應用程式和指示詞處理器的角色。  
  
 [建立自訂 T4 文字範本指示詞處理器](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 指示詞處理器會處理指示詞，在範本中，例如`<#@template#>.`它執行的範本，在編譯期間，可以載入組件和其他資源。 它也可以插入程式碼，將會載入在執行階段的資源。 您可以藉由定義自己的指示詞處理器，來降低複雜性，您的範本。  
  
 [叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 如果您正在撰寫[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]例如功能表命令或事件處理常式的延伸模組，您的延伸模組可以使用文字範本化服務來轉換任何文字範本。 您可以將參數資料傳遞至範本中，使用工作階段物件，並取得使用的範本內的值從`<#@parameter#>`指示詞。  
  
 [使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 文字範本的程式碼執行時，主機會提供存取外部的檔案和應用程式的狀態。 例如，主應用程式中執行文字轉換[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]可存取方案總管 中。 它也會顯示錯誤訊息視窗中的錯誤。 如果您想要在不同的內容中執行文字轉換，您可以定義自己的主機可存取該內容中可用的服務。  
  
 如果您正在撰寫[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]延伸模組，請考慮使用現有的文字轉換服務，而不需要撰寫自己的主機。 如需詳細資訊，請參閱 <<c0> [ 叫用 VS 擴充功能中的文字轉換](../modeling/invoking-text-transformation-in-a-vs-extension.md)。  
  
## <a name="reference"></a>參考資料  
 [撰寫 T4 文字範本](../modeling/writing-a-t4-text-template.md)  
  
 提供的文字範本指示詞和控制區塊的語法。
