---
title: 攔截舊版語言服務命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bb888e83f10d887c15b9ebf9fd67acad28f8e4c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037755"
---
# <a name="intercepting-legacy-language-service-commands"></a>攔截舊版語言服務命令
使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您可以讓 [文字] 檢視會處理的語言服務截距命令。 這是適用於文字檢視不會管理的特定語言的行為。 您可以攔截這些命令加入 [文字] 檢視中的一或多個命令篩選器，從您的語言服務。  
  
## <a name="getting-and-routing-the-command"></a>取得與路由命令  
 命令篩選器是<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>監視特定的字元序列或命令的物件。 您可以關聯多個命令篩選使用單一文字檢視。 每個文字檢視會維護鏈結的命令篩選器。 建立新的命令篩選器之後，您會將篩選新增至適當的文字檢視的鏈結中。  
  
 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>命令篩選器加入鏈結。 當您呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]傳回另一個您可以傳遞命令篩選器不會處理命令的命令篩選條件。  
  
 您有命令處理的下列選項：  
  
- 處理命令，，然後將鏈結中的傳遞到下一個命令篩選器的命令。  
  
- 處理命令，並不會傳遞至下一個命令篩選器的命令。  
  
- 未處理命令，但傳遞到下一個命令篩選器的命令。  
  
- 忽略命令。 不在目前的篩選器中處理它，並請勿將它傳遞到下一個篩選器。  
  
  您的語言服務應處理哪些命令的相關資訊，請參閱[語言服務篩選器的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。