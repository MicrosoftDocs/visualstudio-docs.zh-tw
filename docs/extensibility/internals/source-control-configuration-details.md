---
title: "原始檔控制設定的詳細資訊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2f8a2cc2f1c13c46b3ac4838d95ce588d0461347
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-configuration-details"></a>原始檔控制設定的詳細資料
若要實作原始檔控制，您需要正確地設定您的專案系統或編輯器，請執行下列：  
  
-   要求權限轉換至已變更的狀態  
  
-   要求權限來儲存檔案  
  
-   要求權限來加入、 移除或重新命名專案中的檔案  
  
## <a name="request-permission-to-transition-to-changed-state"></a>要求權限轉換至已變更的狀態  
 專案或編輯器必須藉由呼叫要求轉換為已變更 (dirty) 狀態的權限<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>。 實作每個編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和接收核准，才可從環境中變更文件，再傳回`True`如`M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`。 專案為基本上專案檔中，如編輯器，且如此一來，具有相同負責實作專案檔的狀態變更追蹤，因為文字編輯器會為它的檔案。 環境處理的方案時，已變更的狀態，但您必須處理的任何物件參考方案，但不會儲存，例如專案檔或其項目已變更的狀態。 一般情況下，如果您的專案或編輯器是負責管理持續性項目，然後它會負責實作狀態變更追蹤。  
  
 以回應`IVsQueryEditQuerySave2::QueryEditFiles`呼叫時，環境可以執行下列動作：  
  
-   拒絕對變更的呼叫，編輯器或專案在此情況下必須維持不變 （乾淨） 狀態。  
  
-   指出應重新載入文件資料。 專案中，環境會重新載入專案的資料。 編輯器必須重新載入的資料從磁碟透過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>實作。 在任一情況下，重新載入資料時，可以變更專案或編輯器中的內容。  
  
 它是複雜且困難的工作不適當`IVsQueryEditQuerySave2::QueryEditFiles`到現有的程式碼基底的呼叫。 如此一來，這些呼叫應該在建立專案或編輯器期間整合。  
  
## <a name="request-permission-to-save-a-file"></a>要求權限來儲存檔案  
 專案或編輯器在儲存檔案之前，必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>。 對於專案檔案，這些呼叫會自動完成的解決方案，知道何時要儲存專案檔。 編輯器會負責除非發出這些呼叫的編輯器實作`IVsPersistDocData2`使用 helper 函式<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>。 如果您的編輯器實作`IVsPersistDocData2`在這種方式，然後呼叫`IVsQueryEditQuerySave2::QuerySaveFile`或`IVsQueryEditQuerySave2::QuerySaveFiles`就自動完成。  
  
> [!NOTE]
>  一律先進行這些呼叫 — 也就是當您的編輯器是能夠接收取消一次。  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>要求權限來加入、 移除或重新命名專案中的檔案  
 專案可以加入、 重新命名或移除檔案或目錄之前，它必須呼叫適當`IVsTrackProjectDocuments2::OnQuery*`要求權限，從環境的方法。 如果授與權限時，則專案必須完成此作業，然後再呼叫 適當`IVsTrackProjectDocuments2::OnAfter*`方法來通知作業已完成的環境。 專案必須呼叫的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>介面的所有檔案 （例如特殊的檔案） 和不只是父檔案。 檔案呼叫是必要項，但目錄呼叫是選擇性的。 如果您的專案具有目錄資訊，則它應該呼叫適當<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法，但如果沒有這項資訊，則環境會推斷的目錄資訊。  
  
 專案不應該呼叫的方法`IVsTrackProjectDocuments2`於專案中，開啟或關閉。 想要將此資訊在啟動的接聽程式可以等待<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>事件並逐一查看方案以尋找所需的資訊。 在關閉，不需要這項資訊。 `IVsTrackProjectDocuments2`提供從<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>。  
  
 對於每個新增、 重新命名及移除動作，沒有`OnQuery*`方法和`OnAfter*`方法。 呼叫`OnQuery*`方法來要求權限加入，請重新命名或移除檔案或目錄。 呼叫`OnAfter*`方法之後，加入、 重新命名或移除檔案或目錄的專案狀態會反映新的狀態。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)