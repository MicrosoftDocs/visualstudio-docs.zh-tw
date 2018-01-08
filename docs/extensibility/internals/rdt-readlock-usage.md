---
title: "RDT_ReadLock 使用量 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31c13d9255442459c884379e83b619e1f73a1c2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock 使用量

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>是一個旗標，提供邏輯以鎖定文件中執行文件資料表 (RDT)，即目前開啟的 Visual Studio IDE 中的所有文件的清單。 這個旗標決定文件開啟時，以及文件是在使用者介面中顯示還是以隱藏在記憶體中保留。

一般而言，您會使用<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>下列其中之一為真時：

- 當您想要開啟的文件，以隱藏或唯讀狀態，但其尚未建立的<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>應擁有。

- 當您想要會提示您儲存的使用者顯示在 UI，並將它關閉，則嘗試之前，以隱藏已開啟的文件的使用者。

## <a name="how-to-manage-visible-and-invisible-documents"></a>How to Manage 可見及不可見的文件

當使用者在 UI 中，開啟文件<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>文件的擁有者必須先建立和<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>旗標必須設定。 如果沒有<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>可以建立擁有者，然後將不會儲存文件，當使用者按一下**全部儲存**或關閉 IDE。 這表示如果文件開啟時無形地修改在記憶體中，且使用者是系統提示您儲存文件，在關閉或如果儲存**全部儲存**選擇，則`RDT_ReadLock`無法使用。 相反地，您必須使用`RDT_EditLock`並註冊<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>時<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>旗標。

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock 和文件修改

先前所述的旗標指出會產生不可見的文件開啟其`RDT_EditLock`文件開啟時使用者為可見**DocumentWindow**。 當發生這種情況時，使用者會看見**儲存**提示時顯示**DocumentWindow**已關閉。 `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`使用實作，<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>服務一開始運作時唯一`RDT_ReadLock`會採取 （亦即，當剖析資訊無形地開啟文件）。 稍後，如果文件必須經過修改，然後鎖定會升級到弱式**RDT_EditLock**。 如果使用者再開啟文件中可見**DocumentWindow**、`CodeModel`的弱式`RDT_EditLock`釋放。

如果使用者再關閉**DocumentWindow**並選擇**否**當系統提示您儲存開啟的文件，然後在`CodeModel`實作處置的文件中的所有資訊，並重新開啟從磁碟無形地需要文件的詳細資訊，下一次的文件。 此行為的微妙的地方是在使用者開啟其中的執行個體**DocumentWindow**不可見的開啟文件，加以修改，就會關閉它，以及然後選擇**否**當系統提示您儲存文件。 在此情況下，如果文件`RDT_ReadLock`、 文件將不實際上會關閉，然後修改過的文件會保持開啟以隱藏在記憶體中，即使使用者選擇不儲存文件。

如果看不見文件的開頭使用弱式`RDT_EditLock`，則它會產生其鎖定，當使用者開啟文件明顯地，且沒有其他鎖定會保留。 當使用者關閉**DocumentWindow**並選擇**否**當系統提示您儲存文件，然後關閉文件必須可從記憶體。 這表示不可見的用戶端必須接聽 RDT 事件來追蹤出現在這裡。 下次文件為必要項，必須重新開啟文件。