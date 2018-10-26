---
title: 使用 Interop 組件判斷命令狀態 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8871793d27366771978b2cb23284d1dbe5f4dc5a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948248"
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>使用 Interop 組件判斷命令狀態
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage 必須追蹤的狀態，它可以處理的命令。 VSPackage 中處理的命令會變成啟用或停用時，無法判斷環境。 它是以通知有關命令狀態的環境 VSPackage 的責任，比方說，一般狀態命令，例如**剪下**，**複製**，並**貼上**。  
  
## <a name="status-notification-sources"></a>狀態通知的來源  
 環境接收透過 Vspackage 的命令的相關資訊<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法，這是實作 VSPackage 的一部分的<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 環境呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>的兩個情況下 VSPackage 的方法：  
  
- 當使用者開啟主功能表或操作功能表時 （以滑鼠右鍵按一下） 時，環境便會執行<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>所有該功能表上的命令，以判斷其狀態的方法。  
  
- 當 VSPackage 會要求環境更新目前的使用者介面 (UI)。 這是目前顯示給使用者，這類的命令，就會發生**剪下**，**複製**，並**貼上**標準 工具列上分組、 成為啟用和停用回應內容和使用者的動作。  
  
  因為殼層裝載多個的 Vspackage，殼層的效能會過會降低，不需輪詢來判斷命令狀態的每個 VSPackage。 相反地，VSPackage 應該主動通知環境變更時，變更其 UI 時。 如需有關更新通知的詳細資訊，請參閱[更新使用者介面](../../extensibility/updating-the-user-interface.md)。  
  
## <a name="status-notification-failure"></a>狀態通知失敗  
 通知命令狀態變更的環境失敗 VSPackage 可以將 UI 置於不一致的狀態。 請記住，任何功能表或操作功能表命令的可放入工具列上的使用者。 因此，更新 UI，功能表或操作功能表開啟時，才是不夠的。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [實作](../../extensibility/internals/command-implementation.md)

