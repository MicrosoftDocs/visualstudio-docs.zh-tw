---
title: RDT_ReadLock用法 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705922"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock 使用方式

[_VSRDTFLAGSRDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>)是一個標誌,用於在正在運行的文檔表 (RDT) 中鎖定文檔的邏輯,該表是當前在 Visual Studio IDE 中打開的所有文件的清單。 此標誌確定何時打開文檔,以及文檔在用戶介面中可見或不可見地在記憶體中。

通常,您使用[_VSRDTFLAGS。當](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>)下列原因之一為 true 時,RDT_ReadLock:

- 您希望在不可見和唯讀時打開文檔,但尚未確定應擁有文<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>檔。

- 您希望提示使用者保存在使用者在 UI 中顯示文檔之前不可見地打開的文件,然後嘗試將其關閉。

## <a name="how-to-manage-visible-and-invisible-documents"></a>如何管理可見文件與不可見文件

當使用者在 UI 中打開文檔<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>時,必須建立文檔的擁有者並[_VSRDTFLAGS。](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>)必須設置RDT_EditLock標誌。 如果無法<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>建立擁有者,則當用戶按一下「**全部儲存」** 或關閉 IDE 時,將不會保存文檔。 這意味著,如果文檔在記憶體中修改時處於不可見狀態打開,並且系統會提示使用者在關閉時保存文檔,或者如果選擇了 **"全部儲存**`RDT_ReadLock`",則無法使用。 相反,您必須使用`RDT_EditLock`並在 __VSREGDOCLOCKHOLDER<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>時註冊 。 [RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>)標誌。

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock與文件修改

前面提到的標誌表示,當使用者將文件打開到可見的**DocumentWindow**`RDT_EditLock`中時,文檔的不可見打開將生成其。 發生這種情況時,當可見的**文件視窗**關閉時,將顯示一個**保存**提示。 `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`最初使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>服務的實現僅`RDT_ReadLock`在採用 時(即,當文檔以不可見地打開以解析資訊時)時工作。 稍後,如果必須修改文檔,則鎖將升級到弱**RDT_EditLock**。 如果用戶隨後在可見的**DocumentWindow**中打開`CodeModel`文檔, 則會釋放`RDT_EditLock`的弱文檔。

如果使用者隨後關閉**DocumentWindow,** 並在提示保存開啟的文件時選擇 **「否**」,則`CodeModel`實現將釋放文檔中的資訊,並在下次文檔需要更多資訊時無形中從磁盤中重新打開該文檔。 此行為的微妙之處是使用者打開不可見打開文檔**的 DocumentWindow、** 修改文檔、關閉它,然後在提示保存文檔時選擇 **"否**"。"的實例。 在這種情況下,如果文檔有`RDT_ReadLock`, 則文件實際上不會關閉,並且修改後的文檔將在記憶體中不可見地保持打開狀態,即使用戶選擇不保存文檔也是如此。

如果文檔的不可見打開使用`RDT_EditLock`弱 ,則當使用者明顯打開文檔且沒有其他鎖時,它將生成其鎖。 當使用者關閉**DocumentWindow**並在提示保存文件時選擇 **「否**」時,必須從記憶體中關閉文檔。 這意味著不可見的客戶端必須偵聽 RDT 事件才能跟蹤此事件。 下次需要文檔時,必須重新打開該文檔。
