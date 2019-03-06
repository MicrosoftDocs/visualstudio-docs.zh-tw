---
title: 使用 [開啟] 命令顯示檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b82be9d7f376c1fbc0bc5b24534298a917d07b2e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624343"
---
# <a name="display-files-by-using-the-open-with-command"></a>使用 [開啟] 命令來顯示檔案
專案可以要求以顯示 IDE**開啟** 對話方塊。 此要求會提示使用者開啟標準編輯器選取的檔案。 下列步驟說明此程序：

1.  此專案會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>，指定的值是`OSE_UseOpenWithDialog`如`OSEOpenDocEditor`參數。

2.  根據文件的副檔名，IDE 會決定哪一個登錄可以中所列的編輯器開啟指定的文件，並顯示這項資訊**開啟** 對話方塊。

    > [!NOTE]
    >  有一個內建的編輯器，必須包含在專案**開啟**對話方塊必須註冊每個這類編輯器的編輯器 factory。 內建編輯器只有函式與特定類型的實作中會強制執行的專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。 IDE 具有內建編輯器 factory 的核心文字編輯器] 和 [二進位編輯器。 IDE 也會建立代表每個已註冊的 Windows 檔案關聯的編輯器 factory 的執行個體。 這類檔案的範例是 Microsoft Word。

3.  當使用者選取的項目**開啟** 對話方塊中，然後在 IDE 開啟文件，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。 如需詳細資訊，請參閱[如何：開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)。

## <a name="see-also"></a>另請參閱
- [開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)
- [使用 開啟檔案命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [如何：開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)
