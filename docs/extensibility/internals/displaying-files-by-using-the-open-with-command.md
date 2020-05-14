---
title: 使用「打開」命令顯示檔 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708585"
---
# <a name="display-files-by-using-the-open-with-command"></a>使用「開啟使用」指令顯示檔案
專案可以要求 IDE 顯示 **「打開」** 對話方塊。 此請求提示使用者打開具有標準編輯器選擇的檔案。 以下步驟描述了此過程:

1. 項目呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>,指定 參數`OSE_UseOpenWithDialog``OSEOpenDocEditor`的值 。

2. 根據文件的檔案名副檔名,IDE 確定註冊表中列出的哪些編輯器可以打開指定的文件,並在 **「打開使用」** 對話框中顯示此資訊。

    > [!NOTE]
    > 具有必須包含在「**打開使用」** 對話方塊中的內在編輯器的項目必須為每個此類編輯器註冊一個編輯器工廠。 內部編輯器僅與特定類型的專案一起運行,在<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法的實現中強制執行。 IDE 具有用於核心文字編輯器和二進位編輯器的內建編輯器工廠。 IDE 還代表每個已註冊的 Windows 檔關聯創建編輯器工廠的實例。 此類檔的一個範例是Microsoft Word。

3. 使用者從 **「打開使用」** 對話方塊中選擇專案後,IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>就會透過呼叫方法打開文檔。 關於詳細資訊,請參閱[如何:開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)。

## <a name="see-also"></a>另請參閱
- [開啟並儲存項目項目項目](../../extensibility/internals/opening-and-saving-project-items.md)
- [使用「開啟檔案」指令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [如何:開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)
