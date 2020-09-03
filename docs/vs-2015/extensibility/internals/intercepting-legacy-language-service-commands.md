---
title: 攔截舊版語言服務命令 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6510df2cc9cc1e504f09af033548e0d1c9b4ae74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195017"
---
# <a name="intercepting-legacy-language-service-commands"></a>攔截舊版語言服務命令
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，您可以讓語言服務攔截文字視圖原本會處理的命令。 這適用于文字視圖無法管理的語言特定行為。 您可以從語言服務將一或多個命令篩選器新增至文字視圖，以攔截這些命令。  
  
## <a name="getting-and-routing-the-command"></a>取得和路由傳送命令  
 命令篩選器是 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 監視特定字元序列或按鍵命令的物件。 您可以將一個以上的命令篩選器與單一文字視圖產生關聯。 每個文字視圖都會維護一鏈的命令篩選準則。 建立新的命令篩選器之後，您可以將篩選新增至適當文字視圖的鏈。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>在上呼叫方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ，將您的命令篩選器新增至鏈。 當您呼叫時 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> ， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 會傳回另一個命令篩選準則，您可以傳遞命令篩選器未處理的命令。  
  
 您有下列命令處理選項：  
  
- 處理命令，然後將命令傳遞至鏈中的下一個命令篩選準則。  
  
- 處理命令，並不要將命令傳遞給下一個命令篩選器。  
  
- 請勿處理命令，但是將命令傳遞給下一個命令篩選器。  
  
- 略過命令。 請勿在目前的篩選中處理它，也不要將它傳遞給下一個篩選準則。  
  
  如需語言服務應處理哪些命令的相關資訊，請參閱 [語言服務篩選的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。
