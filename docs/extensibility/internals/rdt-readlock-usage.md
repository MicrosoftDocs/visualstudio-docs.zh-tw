---
title: RDT_ReadLock Usage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d90e2fcdd07738aaa9cdda28f8d131767bf7ffe
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011724"
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock 使用方式

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> 這是旗標可提供邏輯以鎖定文件中執行文件資料表 (RDT)，這目前在 Visual Studio IDE 中開啟的所有文件的清單。 這個旗標會判斷文件開啟時，以及文件是在使用者介面中顯示或隱藏在記憶體中保留。

一般而言，您會使用<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>下列其中之一為 true 時：

- 當您想無形的方式開啟的文件和唯讀的但它尚未建立的<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>應該擁有。

- 當您希望使用者會提示您儲存使用者在 UI 中顯示，並嘗試將它關閉之前無形的方式開啟的文件。

## <a name="how-to-manage-visible-and-invisible-documents"></a>How to Manage 可見和不可見的文件

當使用者在 UI 中，開啟文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>文件的擁有者，必須先建立和<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>旗標必須設定。 如果沒有<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>可以建立擁有者，則當使用者按一下時，將不會儲存文件**全部儲存**或關閉 IDE。 這表示如果已開啟文件無形的方式修改記憶體中，且使用者是系統提示您關閉時儲存文件，或如果儲存**全部儲存**選擇，則`RDT_ReadLock`無法使用。 相反地，您必須使用`RDT_EditLock`，並註冊<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>當<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>旗標。

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock 和文件修改

先前所述的旗標會指出不可見的文件開啟會產生其`RDT_EditLock`文件開啟時使用者到可見**DocumentWindow**。 當發生這種情況時，使用者會看見**儲存**提示時看見**DocumentWindow**已關閉。 `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` 使用的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>服務一開始運作，當只有`RDT_ReadLock`會採取 （亦即，當剖析資訊無形的方式開啟文件）。 更新版本中，如果必須修改文件，然後鎖定會升級到較弱**RDT_EditLock**。 如果使用者再開啟文件中可見**DocumentWindow**，則`CodeModel`的弱式`RDT_EditLock`發行。

如果使用者再關閉**DocumentWindow**並選擇**No**當系統提示您儲存開啟的文件，則`CodeModel`實作會處置的文件中的所有資訊，並重新開啟從磁碟無形的方式下一次的詳細資訊文件所需的文件。 此行為的一些微妙的差異是，在使用者開啟執行個體**DocumentWindow**的不可見的開啟文件中，修改它，關閉它，然後選擇**No**當系統提示您儲存文件。 在此情況下，如果文件`RDT_ReadLock`，然後在文件將不實際上會關閉，並修改的文件會保持開啟狀態無形的方式在記憶體中，即使使用者選擇不儲存文件。

如果看不見文件的開頭使用弱式`RDT_EditLock`，則它會產生其鎖定，當使用者開啟文件明顯地和任何其他鎖定會保留。 當使用者關閉**DocumentWindow**並選擇**No**當系統提示您儲存文件，然後關閉文件必須可從記憶體。 這表示不可見的用戶端必須接聽 RDT 事件來追蹤這項問題。 下一次的文件是必要項，必須重新開啟文件。