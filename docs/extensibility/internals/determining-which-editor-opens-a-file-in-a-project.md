---
title: 判斷哪一個編輯器在專案中開啟檔案 |Microsoft Docs
description: 瞭解 Visual Studio 用來判斷哪一個編輯器在專案中開啟檔案的登錄機碼和 Visual Studio SDK 方法。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f9574a3319d3c43c17d7351e462b6956ae899d84
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328401"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>判斷哪一個編輯器在專案中開啟檔案
當使用者在專案中開啟檔案時，環境會經歷輪詢程式，最後開啟該檔案的適當編輯器或設計工具。 適用于標準和自訂編輯器的環境所採用的初始程式都相同。 當您輪詢要用來開啟檔案的編輯器，且 VSPackage 在此程式期間必須與環境協調時，環境會使用各種準則。

 例如，當使用者 **從 [檔案**] 功能表選取 [**開啟**] 命令，然後選擇 [*檔案名*] (或) 副檔名為 *.rtf* 的任何其他檔案時，環境就會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 每個專案的執行，最後會迴圈執行方案中的所有專案實例。 專案會傳回一組旗標，以依優先權識別檔上的宣告。 使用最高優先順序時，環境會呼叫適當的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 方法。 如需有關輪詢進程的詳細資訊，請參閱 [加入專案和專案專案範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。

 [其他檔案] 專案會宣告其他專案未宣告的所有檔案。 如此一來，自訂編輯器就可以在標準編輯器開啟檔之前開啟檔。 如果其他檔案專案宣告檔案，則環境會呼叫方法， <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 以使用標準編輯器開啟檔案。 環境會檢查其已註冊之編輯器的內部清單，以處理 *.rtf* 檔案。 這份清單位於登錄的下列機碼中：

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ \<version> \Editors \\ \<editor factory guid> \Extensions**

 環境也會針對具有子機碼 **DocObject** 的任何物件，檢查 **HKEY_CLASSES_ROOT\CLSID** 機碼中的類別識別碼。 如果找到副檔名，就會在 Visual Studio 就地建立內嵌版本的應用程式（例如 Microsoft Word）。 這些檔物件必須是執行介面的複合檔案 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> ，否則物件必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 介面。

 如果登錄中的 *.rtf* 檔案沒有編輯器 factory，則環境會尋找 **HKEY_CLASSES_ROOT \\ .rtf** 金鑰，並開啟該處指定的編輯器。 如果在 **HKEY_CLASSES_ROOT** 中找不到副檔名，則環境會使用 Visual Studio core 文字編輯器來開啟檔案（如果檔案為文字檔）。

 如果核心文字編輯器失敗（如果檔案不是文字檔，就會發生這種情況），則環境會針對檔案使用其二進位編輯器。

 如果環境在其登錄中找到 *.rtf* 副檔名的編輯器，則會載入可執行這個編輯器 Factory 的 VSPackage。 環境會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 在新的 VSPackage 上呼叫方法。 VSPackage 會 `QueryService` `SID_SVsRegistorEditor` 使用方法在環境中 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 註冊編輯器 factory，來呼叫。

 環境現在會重新檢查其已註冊之編輯器的內部清單，以尋找適用于 *.rtf* 檔案的新註冊編輯器 factory。 環境會呼叫您的方法的執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ，並傳入要建立的檔案名和檢視類型。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
