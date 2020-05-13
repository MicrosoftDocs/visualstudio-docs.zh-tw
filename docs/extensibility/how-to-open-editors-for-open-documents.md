---
title: 如何:打開開啟文件的編輯器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710919"
---
# <a name="how-to-open-editors-for-open-documents"></a>如何:開啟開啟文件的編輯器
在項目打開文件視窗之前,專案首先必須確定該檔是否已在另一個編輯器的文檔視窗中打開。 這個檔案可以在特定於項目的編輯器中開啟,也可以在中註冊的標準編輯器之一開啟[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。

## <a name="open-a-project-specific-editor"></a>開啟特定於項目的編輯器
 使用以下過程為已打開的文件打開特定於專案的編輯器。

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>開啟檔案開啟特定於項目的編輯器

1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 方法。

    如果適用,此調用返回指向文檔層次結構、層次結構項和視窗框架的指標。

2. 如果文件處於打開狀態,則項目必須檢查是否存在文檔數據物件,或者文檔檢視物件是否也存在。

   - 如果存在文件檢視物件,並且此檢視用於其他層次結構或層次結構項,則專案使用指向視圖視窗框架的指標重新顯示現有視窗。

   - 如果存在文件檢視物件,並且此視圖適用於同一層次結構和層次結構項,則如果專案可以附加到基礎文檔數據物件,則可以打開第二個檢視。 否則,專案應使用指向檢視視窗框架的指標重新顯示現有視窗。

   - 如果僅存在文件數據物件,則專案應確定是否可以將文檔數據物件用於其檢視。 如果文件資料物件相容,則完成[打開特定於專案的編輯器](../extensibility/how-to-open-project-specific-editors.md)中討論的步驟。

     如果文件數據物件不相容,則應向使用者顯示指示檔當前正在使用的錯誤。 此錯誤應僅在暫態情況下顯示,例如當用戶嘗試使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文本編輯器以外的編輯器打開檔的同時編譯檔時。 核心文字編輯器可以與編譯器共享文檔數據物件。

3. 如果文件由於沒有文件資料物件或文檔檢視物件而未打開,則完成[「打開特定於項目的編輯器」](../extensibility/how-to-open-project-specific-editors.md)中的步驟。

## <a name="open-a-standard-editor"></a>開啟標準編輯器
 使用以下過程為已打開的文件打開標準編輯器。

### <a name="to-open-a-standard-editor-for-an-open-file"></a>開啟檔案開啟標準編輯器

1. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。

     此方法首先通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>驗證文檔尚未打開。 如果文件已打開,則其編輯器視窗將重新顯示。

2. 如果文件未打開,則完成[「如何打開標準編輯器](../extensibility/how-to-open-standard-editors.md)」中的步驟。

## <a name="see-also"></a>另請參閱
- [開啟與儲存項目項目](../extensibility/internals/opening-and-saving-project-items.md)
- [如何:開啟特定於項目的編輯器](../extensibility/how-to-open-project-specific-editors.md)
- [如何:開啟標準編輯器](../extensibility/how-to-open-standard-editors.md)
