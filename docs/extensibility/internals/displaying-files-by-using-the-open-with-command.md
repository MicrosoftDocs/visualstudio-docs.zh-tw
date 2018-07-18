---
title: 使用 [開啟] 命令顯示檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9c708bb5a510748b08cac5b46b6829b908e74e0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128614"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>使用 [開啟] 命令顯示檔案
專案可以要求顯示 IDE**開啟** 對話方塊。 此要求會提示使用者開啟的標準編輯器中選取的檔案。 下列步驟說明此程序。  
  
1.  專案呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>，指定的值是針對 OSE_UseOpenWithDialog`OSEOpenDocEditor`參數。  
  
2.  根據文件的檔案名稱副檔名，IDE 會判斷登錄可以中所列的編輯器開啟指定的文件並顯示這項資訊**開啟** 對話方塊。  
  
    > [!NOTE]
    >  專案中必須包含的內建函式編輯器**開啟**對話方塊必須登錄 editor factory 每個這類編輯器。 內建函式編輯器只有函式與特定類型的專案，會強制執行中的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法。 IDE 提供內建編輯器 factory 的核心文字編輯器和二進位編輯器。 IDE 也會建立代表每個已註冊的 Windows 檔案關聯編輯器 factory 的執行個體。 這類檔案的範例是 Microsoft Word。  
  
3.  當使用者選取的項目**開啟**對話方塊中，然後在 IDE 開啟文件，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法。 如需詳細資訊，請參閱[如何： 開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開啟並儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)   
 [使用 開啟檔案命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)