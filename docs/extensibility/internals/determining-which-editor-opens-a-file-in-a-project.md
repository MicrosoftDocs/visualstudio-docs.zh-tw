---
title: "判斷哪一個編輯器在專案中開啟的檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f7c69bc08d0f1bb72a37b76fca2d402d73036deb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>決定編輯器開啟的專案中的檔案
當使用者開啟檔案的專案中時，環境會經歷輪詢程序，最後開啟適當的編輯器或設計工具，該檔案。 初始環境所採用的程序是相同的標準和自訂編輯器。 輪詢要用來開啟檔案時，環境會使用各種不同的準則，VSPackage 必須與環境協調在這個程序。  
  
 例如，當使用者選取**開啟**命令**檔案**功能表，然後選擇`filename`.rtf （或任何其他副檔名是.rtf） 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>實作可用於每個專案，最終輪流方案中的所有專案執行個體。 專案會傳回一組旗標的優先順序來識別文件上的宣告。 使用最高的優先順序，環境會呼叫適當<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>方法。 如需輪詢程序的詳細資訊[加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)。  
  
 其他檔案專案宣告不快其他專案的所有檔案。 如此一來，自訂編輯器可以開啟文件之前標準編輯器開啟它們。 環境的其他檔案專案宣告檔案，如果呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法來使用標準編輯器開啟檔案。 環境會檢查其內部清單的處理.rtf 檔案的其中一個已註冊的編輯器。 此清單位於位於下列機碼的登錄：  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 環境也會檢查在 HKEY_CLASSES_ROOT\CLSID 機碼具有子機碼 DocObject 的任何物件的類別識別項。 如果那里找到檔案的副檔名，內嵌的應用程式，例如 Microsoft Word、 版本是就地建立 Visual Studio 中。 這些文件物件必須實作的複合檔案<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>介面或物件必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>介面。  
  
 如果未在登錄中，.rtf 檔案的編輯器 factory，則環境會查詢 HKEY_CLASSES_ROOT \\.rtf 金鑰，並那里指定編輯器開啟。 如果 HKEY_CLASSES_ROOT 中找不到副檔名，環境會使用 Visual Studio 核心的文字編輯器來開啟檔案，如果它是一個文字檔。  
  
 如果核心文字編輯器就會失敗，發生如果檔案不是文字檔案，然後環境會使用其二進位編輯器的檔案。  
  
 如果環境並在其登錄中找到編輯器.rtf 延伸模組，它會載入 VSPackage 實作這個編輯器 factory。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>上新的 VSPackage 的方法。 VSPackage 呼叫`QueryService`如`SID_SVsRegistorEditor`，並使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>方法，登錄 editor factory 與環境。  
  
 環境時，現在重新檢查已註冊的編輯器，以尋找新註冊的 editor factory.rtf 檔案的內部清單。 環境呼叫您的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>方法，傳入要建立的檔案名稱及檢視類型。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>