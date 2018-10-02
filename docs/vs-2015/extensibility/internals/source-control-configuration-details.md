---
title: 原始檔控制設定的詳細資訊 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aed814ee319f9713a7b4a4c5925abcda63a04e49
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499870"
---
# <a name="source-control-configuration-details"></a>原始檔控制組態的詳細資料
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[原始檔控制組態的詳細資料](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-configuration-details)。  
  
若要實作原始檔控制，您需要適當地設定您的專案系統或編輯器來執行下列作業：  
  
-   要求轉換至已變更狀態的權限  
  
-   權限，才能儲存檔案  
  
-   要求權限來新增、 移除或重新命名專案中的檔案  
  
## <a name="request-permission-to-transition-to-changed-state"></a>要求轉換至已變更狀態的權限  
 專案或編輯器必須藉由呼叫要求轉換至已變更 (dirty) 狀態的權限<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>。 實作每個編輯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>收發核准才可從環境中變更文件，再傳回`True`如`M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`。 此專案是本質上的專案檔中，編輯器，並如此一來，已實作之專案檔的狀態變更追蹤，其檔案的文字編輯器一樣的相同責任。 環境會處理已變更的狀態的解決方案，但您必須處理的任何物件參考解決方案，但不會儲存，例如專案檔或其項目已變更的狀態。 一般情況下，如果您的專案或編輯器是負責管理持續性的項目，然後它會負責實作已變更狀態的追蹤。  
  
 以回應`IVsQueryEditQuerySave2::QueryEditFiles`呼叫時，環境也可以執行下列動作：  
  
-   拒絕對變更的呼叫，編輯器或專案在此情況下必須保持不變 （全新） 狀態。  
  
-   表示應重新載入文件資料。 針對專案中，環境將會重新載入專案的資料。 編輯器必須重新載入的資料磁碟，透過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>實作。 在任一情況下，重新載入資料時，可以變更專案或編輯器中的內容。  
  
 它是複雜且困難的工作，改建適當`IVsQueryEditQuerySave2::QueryEditFiles`到現有的程式碼基底的呼叫。 如此一來，這些呼叫應該在建立專案或編輯器整合。  
  
## <a name="request-permission-to-save-a-file"></a>權限，才能儲存檔案  
 專案或編輯器儲存檔案之前，必須呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>。 對於專案檔案，這些呼叫會自動完成此解決方案，知道何時要儲存專案檔。 編輯器會負責進行這些呼叫，除非編輯器實作`IVsPersistDocData2`會使用協助程式函式<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>。 如果您的編輯器實作`IVsPersistDocData2`中，如此一來，然後呼叫`IVsQueryEditQuerySave2::QuerySaveFile`或`IVsQueryEditQuerySave2::QuerySaveFiles`就自動完成。  
  
> [!NOTE]
>  一定要先進行這些呼叫 — 亦即，當您的編輯器是能夠接收取消一次。  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>要求權限來新增、 移除或重新命名專案中的檔案  
 專案可以新增、 重新命名或移除檔案或目錄之前，必須呼叫適當`IVsTrackProjectDocuments2::OnQuery*`從環境的方法來要求權限。 如果授與權限時，則專案必須完成作業，然後再呼叫 適當`IVsTrackProjectDocuments2::OnAfter*`方法來通知環境已完成的作業。 專案必須呼叫的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>介面的所有檔案 （例如特殊的檔案） 和不只是父檔案。 檔案呼叫是必要項目，但目錄呼叫都是選擇性。 如果您的專案具有目錄資訊，則它應該呼叫適當<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法，但如果它並沒有這項資訊，則環境會推斷目錄資訊。  
  
 專案不應該呼叫的方法`IVsTrackProjectDocuments2`在專案開啟或關閉。 想要這項資訊在啟動的接聽程式可以等待<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>事件並逐一查看方案，以尋找所需的資訊。 關閉時，不需要這項資訊。 `IVsTrackProjectDocuments2` 提供從<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>。  
  
 針對每個新增、 重新命名 和 移除 動作中，沒有`OnQuery*`方法和`OnAfter*`方法。 呼叫`OnQuery*`方法來要求權限新增，請重新命名或移除檔案或目錄。 呼叫`OnAfter*`方法之後新增、 重新命名或移除檔案或目錄的專案狀態會反映新的狀態。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)

