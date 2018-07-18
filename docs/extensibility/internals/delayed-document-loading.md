---
title: 延遲的文件載入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc10d7807633433b38fa8587d41c2ac3c0273ebe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134433"
---
# <a name="delayed-document-loading"></a>延遲的文件載入
當使用者重新開啟 Visual Studio 方案時，大部分的相關聯的文件並不會立即載入。 文件視窗框架建立的暫止的初始化狀態，並 （稱為虛設常式框架） 預留位置文件放置執行文件資料表 (RDT) 中。  
  
 您的擴充功能可能會導致不必要地載入，藉由查詢文件中的項目，再將它們載入專案文件。 適用於 Visual Studio，這會增加整體的記憶體耗用量。  
  
## <a name="document-loading"></a>文件載入  
 當使用者存取文件，例如藉由選取的視窗框架 索引標籤，虛設常式畫面格和文件會完全初始化。 文件也可以初始化要求文件的資料，藉由存取 RDT 直接以取得文件資料，或藉由下列呼叫其中間接存取 RDT 延伸模組：  
  
-   視窗框架 show 方法： <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>。  
  
-   視窗框架 GetProperty 方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>任何下列屬性：  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 如果您的延伸模組會使用 managed 程式碼，您不應該呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>除非您特定的文件不是處於暫止的初始化狀態，或您想要完整初始化的文件... 這是因為這個方法一律會傳回文件資料物件，如有必要，請建立它。 相反地，您應該在 IVsRunningDocumentTable4 介面上呼叫其中一個方法。  
  
 如果您的延伸模組會使用 c + +，您可以傳遞`null`您不想使用的參數。  
  
 您可以呼叫下列方法之一之前您尋求相關的屬性,，以避免不必要的文件載入： 您有要求其他屬性之前。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 使用<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 這個方法會傳回<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>物件，其中包含的值<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>如果文件尚未初始化。  
  
 您可以找出時已載入文件訂閱 RDT 事件完全初始化文件時引發。 有兩種可能性：  
  
-   如果事件接收實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>，您可以訂閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>，  
  
-   否則，您可以訂閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>。  
  
 以下是假設的文件存取案例。 Visual Studio 擴充功能要顯示開啟的文件的一些資訊，例如編輯鎖定計數和相關文件資料的項目。 它會列舉 RDT 使用中的文件<xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>，然後呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>每份文件，以便擷取編輯鎖定計數和文件資料。 如果文件處於暫止的初始化狀態時，要求文件資料會使它不必要地初始化。  
  
 這麼做的更有效率的方式是使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A>來取得編輯鎖定計數，然後使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>來判斷是否已初始化文件。 如果未包含旗標<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>，已經初始化文件，並要求使用的文件資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A>不會造成任何不必要的初始化。 如果旗標包含<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>，擴充功能應該避免要求文件資料之前會初始化文件。 這可以偵測 OnAfterAttributeChange(Ex) 事件處理常式中。  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>測試以查看它們強制執行初始設定的擴充功能  
 沒有任何顯示的提示，表示是否已初始化文件，所以您可能會難以找出您的延伸模組為強制執行初始化。 您可以設定登錄機碼，使驗證更容易，因為這會導致所有未完全初始化文字的文件的標題`[Stub]`標題中。  
  
 在**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**，將**StubTabTitleFormatString**至 **{0} [Stub]**。