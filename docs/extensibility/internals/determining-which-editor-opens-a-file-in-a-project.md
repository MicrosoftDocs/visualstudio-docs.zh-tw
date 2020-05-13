---
title: 確定哪個編輯器在項目開啟檔案 。微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708652"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>確定哪個編輯器開啟檔案
當使用者在項目中打開檔時,環境將經歷輪詢過程,最終打開該檔的相應編輯器或設計器。 對於標準和自定義編輯器,環境使用的初始過程是相同的。 輪詢要使用哪個編輯器來打開檔時,環境使用各種條件,並且 VSPackage 必須在此過程中與環境協調。

 例如,當使用者從 **「檔」** 選單中選擇**Open**命令,然後選擇*filename.rtf(* 或具有 *.rtf*擴充名的任何其他檔<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>)時,環境將調用每個項目的實現,最終迴圈遍解決方案中的所有專案實例。 專案返回一組標誌,這些標誌按優先順序標識文檔上的聲明。 使用最高優先順序,環境調用適當的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。 有關輪詢過程的詳細資訊,請參閱[添加專案和專案項範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

 "雜項檔"專案聲明其他專案未聲明的所有檔。 這樣,自定義編輯器可以在標準編輯器打開文檔之前打開文檔。 如果「雜項檔」專案聲明檔,則環境將調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法以使用標準編輯器打開檔。 環境檢查其內部註冊的編輯器清單,以查找處理 *.rtf*檔。 此清單位於註冊表中,位於以下鍵:

 **HKEY_LOCAL_MACHINE_軟體_微軟_VisualStudio\\\<版本>_\\\<編輯器工廠 guid>\擴展**

 環境還檢查**HKEY_CLASSES_ROOT_CLSID**鍵中的類識別碼,以檢查具有子鍵**DocObject**的任何物件。 如果找到文件副檔名,則在 Visual Studio 中就地創建應用程式的嵌入式版本,如 Microsoft Word。 這些文件物件必須是實現介面的<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>複合檔,或者該物件必須實現<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>介面。

 如果註冊表中沒有 *.rtf*檔的編輯器工廠,則環境將在**HKEY_CLASSES_ROOT\\.rtf**鍵中尋找,並打開其中指定的編輯器。 如果在**HKEY_CLASSES_ROOT**中找不到檔案副檔名,則環境使用 Visual Studio 核心文字編輯器打開該檔(如果該檔是文本檔)。

 如果核心文本編輯器失敗(如果檔不是文本檔,則發生這種情況),則環境會對其檔使用其二進位編輯器。

 如果環境在其註冊表中確實找到了 *.rtf*擴展的編輯器,它將載入實現此編輯器工廠的 VSPackage。 環境調用新<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>VSPackage 上的方法。 VSPackage 調`QueryService``SID_SVsRegistorEditor`用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>,使用 方法將編輯器工廠註冊到環境中。

 環境現在重新檢查其註冊編輯器的內部清單,以查找*新註冊的編輯器工廠.rtf*檔。 環境呼叫方法的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, 傳入要建立的檔案名稱和檢視類型。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
