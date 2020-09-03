---
title: RDT_ReadLock 使用量 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9a6b5f86f0cfbb71f6264bdc74df72ad9209c9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154141"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock 使用方式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 這是一個旗標，可提供在執行中的檔資料表中鎖定檔的邏輯 (RDT) ，也就是目前在 Visual Studio IDE 中開啟的所有檔的清單。 此旗標會決定檔的開啟時間，以及檔是否在使用者介面中顯示，或在記憶體中以不可見的方式保存。  
  
 一般來說， <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 當下列其中一項為真時，您將會使用：  
  
- 當您想要以非程式和唯讀方式開啟檔時，但尚未建立它 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 應該擁有的檔。  
  
- 當您想要讓使用者在使用者于 UI 中顯示時，提示使用者儲存以不可見的方式開啟的檔，然後再嘗試將其關閉。  
  
## <a name="how-to-manage-visible-and-invisible-documents"></a>如何管理可見和不可見的檔  
 當使用者在 UI 中開啟檔時， <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 必須建立檔的擁有者，而且 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 必須設定旗標。 如果無法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 建立擁有者，則當使用者按一下 [ **全部儲存** ] 或 [關閉 IDE] 時，不會儲存檔。 這表示，如果在記憶體中修改檔時，以不可見的方式開啟檔，而且如果選擇 [ **全部儲存** ]，系統會提示使用者將檔儲存在關閉或儲存時，則 `RDT_ReadLock` 無法使用。 相反地，您必須使用， `RDT_EditLock` 並在旗標上註冊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> 。  
  
## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock 與檔修改  
 上述的旗標指出 `RDT_EditLock` 當使用者將檔開啟至可見的 **DocumentWindow**時，不可見的檔開啟。 發生這種情況時，當可見的**DocumentWindow**關閉時，使用者會看到**儲存**提示。 使用此服務的 CodeModel <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> 執行一開始僅適用 `RDT_ReadLock` 于 (，亦即，以不可見的方式開啟檔以剖析資訊) 。 稍後，如果必須修改檔，則鎖定會升級為弱式 **RDT_EditLock**。 如果使用者接著在可見的 **DocumentWindow**中開啟檔，就 `CodeModel` `RDT_EditLock` 會發行弱式。  
  
 如果使用者接著關閉 **DocumentWindow** ，並在系統提示您儲存開啟的檔時選擇 [ **否** ]，則該 `CodeModel` 執行會處置檔中的所有資訊，並在下一次檔需要更多資訊時，以不可見的方式從磁片重新開啟檔。 此行為的奧妙是使用者開啟隱藏的已開啟檔的 **DocumentWindow** 、加以修改、關閉，然後在系統提示您儲存檔時選擇 [ **否** ] 的實例。 在此情況下，如果檔具有 `RDT_ReadLock` ，則檔將不會實際關閉，且修改過的檔將會在記憶體中以不可見的方式保持開啟，即使使用者選擇不儲存檔也是一樣。  
  
 如果不可見的檔開啟使用弱式，則會在使用者以可見方式 `RDT_EditLock` 開啟檔時產生鎖定，且不會保留其他鎖定。 當使用者關閉 **DocumentWindow** ，並在系統提示您儲存檔時選擇 [ **否** ]，則必須從記憶體中關閉檔。 這表示不可見的用戶端必須接聽 RDT 事件，才能追蹤這項情況。 下次需要檔時，必須重新開啟檔。
