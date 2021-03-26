---
title: RDT_ReadLock 使用量 |Microsoft Docs
description: 瞭解 _VSRDTFLAGS。RDT_ReadLock 旗標，其提供在執行中的檔資料表中鎖定檔的邏輯。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6add02e763c9664c19fe21b1cfc37dd29b3010b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060831"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock 使用方式

[_VSRDTFLAGS。RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) 是一個旗標，可提供在執行中的檔資料表中鎖定檔的邏輯 (RDT) ，也就是目前在 VISUAL STUDIO IDE 中開啟的所有檔的清單。 此旗標會決定檔的開啟時間，以及檔是否在使用者介面中顯示，或在記憶體中以不可見的方式保存。

一般來說，您會使用 [_VSRDTFLAGS。](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) 當下列其中一項為真時 RDT_ReadLock：

- 您想要以不可見的方式開啟檔，而且是唯讀的，但尚未建立它 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 應該擁有的檔。

- 您想要讓使用者在使用者于 UI 中顯示時，提示使用者儲存以不可見的方式開啟的檔，然後再嘗試將其關閉。

## <a name="how-to-manage-visible-and-invisible-documents"></a>如何管理可見和不可見的檔

當使用者在 UI 中開啟檔時， <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 必須建立檔的擁有者及 [_VSRDTFLAGS。](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) 必須設定 RDT_EditLock 旗標。 如果無法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 建立擁有者，則當使用者按一下 [ **全部儲存** ] 或 [關閉 IDE] 時，不會儲存檔。 這表示，如果在記憶體中修改檔時，以不可見的方式開啟檔，而且如果選擇 [ **全部儲存** ]，系統會提示使用者將檔儲存在關閉或儲存時，則 `RDT_ReadLock` 無法使用。 相反地，您必須使用， `RDT_EditLock` 並 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 在 __VSREGDOCLOCKHOLDER 時註冊 [。RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) 旗標。

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock 與檔修改

上述的旗標指出 `RDT_EditLock` 當使用者將檔開啟至可見的 **DocumentWindow** 時，不可見的檔開啟。 發生這種情況時，當可見的 **DocumentWindow** 關閉時，使用者會看到 **儲存** 提示。 `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> 服務的執行一開始僅適用 `RDT_ReadLock` 于 (，亦即，當檔以非程式方式開啟以剖析資訊) 時。 稍後，如果必須修改檔，則鎖定會升級為弱式 **RDT_EditLock**。 如果使用者接著在可見的 **DocumentWindow** 中開啟檔，就 `CodeModel` `RDT_EditLock` 會發行弱式。

如果使用者接著關閉 **DocumentWindow** ，並在系統提示您儲存開啟的檔時選擇 [ **否** ]，則該 `CodeModel` 執行會處置檔中的所有資訊，並在下一次檔需要更多資訊時，以不可見的方式從磁片重新開啟檔。 此行為的奧妙是使用者開啟隱藏的已開啟檔的 **DocumentWindow** 、加以修改、關閉，然後在系統提示您儲存檔時選擇 [ **否** ] 的實例。 在此情況下，如果檔具有 `RDT_ReadLock` ，則檔將不會實際關閉，且修改過的檔將會在記憶體中以不可見的方式保持開啟，即使使用者選擇不儲存檔也是一樣。

如果不可見的檔開啟使用弱式，則會在使用者以可見方式 `RDT_EditLock` 開啟檔時產生鎖定，且不會保留其他鎖定。 當使用者關閉 **DocumentWindow** ，並在系統提示您儲存檔時選擇 [ **否** ]，則必須從記憶體中關閉檔。 這表示不可見的用戶端必須接聽 RDT 事件，才能追蹤這項情況。 下次需要檔時，必須重新開啟檔。
