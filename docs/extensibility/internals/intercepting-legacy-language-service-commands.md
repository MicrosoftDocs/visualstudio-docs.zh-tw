---
title: 攔截舊版語言服務命令 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38f025e9dab6f93d87660a59421cbd778c92165a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="intercepting-legacy-language-service-commands"></a>攔截舊版語言服務命令
與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您可以讓 [文字] 檢視會處理的語言服務截距命令。 這是適用於文字檢視不會管理的特定語言的行為。 您可以攔截這些命令加入文字檢視中的一或多個命令篩選器，從您的語言服務。  
  
## <a name="getting-and-routing-the-command"></a>取得及路由命令  
 命令篩選器是<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>監視特定的字元序列或命令的物件。 您可以將多個命令篩選器與單一文字檢視。 每個文字檢視維護鏈結 of 命令篩選器。 建立新的命令篩選器之後，您會將篩選條件新增至適當的文字檢視鏈結中。  
  
 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>命令篩選器加入鏈結。 當您呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]傳回另一個您可以傳遞命令篩選器不會處理命令的命令篩選條件。  
  
 您有命令處理的下列選項：  
  
-   處理命令，然後傳遞至下一個命令篩選器的命令鏈結中。  
  
-   處理命令並不會傳遞至下一個命令篩選命令。  
  
-   無法處理命令，但傳遞至下一個命令篩選命令。  
  
-   忽略命令。 不要在目前的篩選器中處理，不要將它傳遞至下一個篩選條件。  
  
 語言服務應該處理哪一個命令的相關資訊，請參閱[重要命令語言服務篩選](../../extensibility/internals/important-commands-for-language-service-filters.md)。