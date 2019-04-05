---
title: 判斷哪一個編輯器在專案中開啟檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945333"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>決定要開啟專案中檔案的編輯器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當使用者開啟檔案，在專案中時，環境會經歷輪詢的程序，最後會開啟適當的編輯器或設計工具，該檔案。 初始環境所採用的程序也適用於標準和自訂編輯器。 輪詢的編輯器，用以開啟檔案時，環境會使用各種不同的準則，VSPackage 必須協調與環境，在此程序。  
  
 比方說，當使用者選取**開放**命令**檔案**功能表，然後選擇`filename`.rtf （或任何其他副檔名為.rtf），環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>每個專案，最後一一巡視所有的專案執行個體，在方案中實作。 專案會傳回一組文件上的宣告識別優先順序的旗標。 使用最高的優先順序，環境會呼叫適當<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。 如需輪詢程序的進一步資訊[加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
 其他檔案專案宣告不宣告的其他專案的所有檔案。 如此一來，自訂編輯器可以開啟文件之前標準編輯器開啟它們。 如果其他檔案專案中宣告的檔案，環境會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法，以使用標準編輯器開啟檔案。 環境會檢查其內部處理.rtf 檔案的其中一個已註冊的編輯器清單。 此清單位於登錄中的下列機碼：  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`>\Editors\\{<`editor factory guid`>}\Extensions]  
  
 環境也會檢查任何物件具有子機碼的 DocObject HKEY_CLASSES_ROOT\CLSID 機碼中的類別識別碼。 如果那里找到檔案的副檔名，則內嵌的應用程式，例如 Microsoft Word 版本是就地建立 Visual Studio 中。 這些文件物件必須實作的複合檔案<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>介面或物件必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>介面。  
  
 如果在登錄中，.rtf 檔案的任何編輯器 factory 則環境會尋找在 HKEY_CLASSES_ROOT \\.rtf 金鑰，並開啟編輯器指定。 如果 HKEY_CLASSES_ROOT 裡找不到檔案的副檔名，環境會使用 Visual Studio 核心的文字編輯器開啟檔案，如果它是一個文字檔。  
  
 如果核心文字編輯器就會失敗，就會出現如果檔案不是文字檔案，則環境會使用其二進位編輯器的檔案。  
  
 如果環境可找出編輯器.rtf 延伸模組在其登錄中，它會載入 VSPackage 實作此編輯器 factory。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>新 vspackage 的方法。 VSPackage 呼叫`QueryService`for `SID_SVsRegistorEditor`，並使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>編輯器 factory 向環境的方法。  
  
 環境時，現在重新檢查其已註冊的編輯器，來尋找.rtf 檔案的新註冊的編輯器 factory 的內部清單。 環境呼叫您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法並傳入要建立的檔案名稱並檢視類型。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
