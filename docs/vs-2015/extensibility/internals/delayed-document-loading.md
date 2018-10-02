---
title: 延遲載入文件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3469484518a4d802c8fc0de11a32533fa429d3d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487627"
---
# <a name="delayed-document-loading"></a>已延遲載入文件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[延遲載入文件](https://docs.microsoft.com/visualstudio/extensibility/internals/delayed-document-loading)。  
  
當使用者重新開啟 Visual Studio 方案時，大部分的相關聯的文件並不會立即載入。 在初始化暫止狀態下，建立文件視窗框架和預留位置文件 （稱為虛設常式框架） 會放在執行文件表格 」 (RDT)。  
  
 您的延伸模組可能會導致不必要地載入，藉由查詢文件中的項目，然後才載入的專案文件。 適用於 Visual Studio 可能增加整體的記憶體耗用量。  
  
## <a name="document-loading"></a>載入文件  
 當使用者存取文件，例如藉由選取的視窗框架 索引標籤，虛設常式框架和文件會完全初始化。 文件也可以初始化要求文件的資料時，可以存取直接以取得文件資料，RDT 或間接存取 RDT，進行下列呼叫的其中一個延伸模組：  
  
-   視窗框架顯示方法： <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>。  
  
-   視窗框架的 GetProperty 方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>任何下列屬性：  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 如果您的延伸模組會使用 managed 程式碼，您不應該呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>除非您確定文件不是處於暫止的初始化狀態，或您想要完全初始化的文件... 這是因為此方法一律會傳回文件資料物件，如有必要，請建立它。 相反地，您應該將其中一個方法呼叫 IVsRunningDocumentTable4 介面上。  
  
 如果您的延伸模組會使用 c + +，您可以傳遞`null`您不想要的參數。  
  
 您可以呼叫下列方法之一，然後再要求相關的屬性，以避免不必要的文件載入： 您有要求其他屬性之前。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 使用<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 這個方法會傳回<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>物件，其中包含的值<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>尚未初始化文件時。  
  
 文件已載入文件已完全初始化時，會引發 RDT 事件訂閱時，您可以了解。 有兩種可能性：  
  
-   如果事件接收器會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>，您可以訂閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>，  
  
-   否則，您可以訂閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>。  
  
 以下是假設的文件存取案例。 Visual Studio 擴充功能要顯示開啟的文件的一些資訊，例如編輯鎖定計數和相關文件資料的項目。 它會列舉在 RDT 中使用的文件<xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>，然後呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>擷取編輯鎖定計數和文件資料的每份文件。 如果文件處於暫止的初始化狀態，要求的文件資料會導致不必要地初始化。  
  
 這是為了使用這種做法更有效率的方式<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A>來取得編輯鎖定計數，然後使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>來判斷是否已初始化文件。 如果未包含旗標<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>，文件已經初始化，並要求使用的文件資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A>不會造成任何不必要的初始化。 如果包含旗標<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>，擴充功能應該避免要求文件資料，直到初始化文件。 這可以偵測 OnAfterAttributeChange(Ex) 事件處理常式中。  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>測試以查看它們強制執行初始化的延伸模組  
 沒有任何可見的提示來指出是否已初始化文件，因此它可能難以找出初始化時，是否要強制您的延伸模組。 您可以設定登錄機碼，更輕鬆驗證，因為這會導致文字並未完全初始化每個文件的標題`[Stub]`標題中。  
  
 在 [ **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**，將**StubTabTitleFormatString**來 **{0} [Stub]**。

