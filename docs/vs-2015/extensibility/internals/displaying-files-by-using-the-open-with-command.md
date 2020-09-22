---
title: 使用 [開啟檔案] 命令顯示檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838847"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>使用開啟方式命令顯示檔案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案可以要求 IDE 顯示 [ **開啟方式** ] 對話方塊。 此要求會提示使用者開啟具有所選標準編輯器的檔案。 下列步驟說明這個程序。  
  
1. 專案會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ，指定參數的 OSE_UseOpenWithDialog 值 `OSEOpenDocEditor` 。  
  
2. 根據檔的副檔名，IDE 會決定登錄中列出的編輯器可以開啟指定的檔，並在 [ **開啟** 檔案] 對話方塊中顯示這項資訊。  
  
    > [!NOTE]
    > 具有必須包含在 [ **開啟方式** ] 對話方塊中之內建編輯器的專案，必須為每個這類編輯器註冊編輯器 factory。 內建編輯器只會與特定類型的專案一起運作，而這會在方法的執行中強制執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 。 IDE 具有適用于核心文字編輯器和二進位編輯器的內建編輯器 factory。 IDE 也會代表每個已註冊的 Windows 檔案關聯建立編輯器 factory 的實例。 Microsoft Word 是這類檔案的範例。  
  
3. 當使用者從 [ **開啟方式** ] 對話方塊中選取專案時，IDE 就會呼叫方法來開啟檔 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 。 如需詳細資訊，請參閱 [如何：開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)。  
  
## <a name="see-also"></a>另請參閱  
 [開啟和儲存專案專案](../../extensibility/internals/opening-and-saving-project-items.md)   
 [使用開啟檔案命令顯示檔案](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)
