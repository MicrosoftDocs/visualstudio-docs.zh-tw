---
title: 延遲的檔載入 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196863"
---
# <a name="delayed-document-loading"></a>已延遲載入文件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當使用者重新開啟 Visual Studio 方案時，大部分相關聯的檔都不會立即載入。 文件視窗框架會以暫止的初始化狀態建立，而預留位置檔 (稱為存根框架) 放置於執行中的檔資料表 (RDT) 。  
  
 在載入檔之前，您的延伸模組可能會在檔中查詢元素，導致不必要地載入專案檔案。 這可能會增加 Visual Studio 的整體記憶體使用量。  
  
## <a name="document-loading"></a>檔載入  
 當使用者存取檔時，會完全初始化存根框架和檔，例如，藉由選取視窗框架的索引標籤。 您也可以藉由要求檔資料的延伸模組來初始化檔，方法是直接存取 RDT 以取得檔資料，或藉由進行下列其中一項呼叫來間接存取 RDT：  
  
- 視窗框架顯示方法： <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 。  
  
- 下列任何屬性的視窗框架 GetProperty 方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> ：  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  如果您的延伸模組使用 managed 程式碼， <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 除非您確定檔不是處於暫止初始化狀態，或是您想要讓檔完全初始化，否則您不應該呼叫。 這是因為此方法一律會傳回檔資料物件，並在必要時建立它。 相反地，您應該在 IVsRunningDocumentTable4 介面上呼叫其中一個方法。  
  
  如果您的延伸模組使用 c + +，您可以 `null` 針對不想要的參數傳遞。  
  
  您可以在要求相關屬性之前，先呼叫下列其中一種方法來避免不必要的檔載入：要求其他屬性。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 使用 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> 。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>如果尚未初始化檔，這個方法會傳回包含值的物件 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 。  
  
  您可以藉由訂閱已完全初始化檔時所引發的 RDT 事件，找出檔載入的時間。 有兩種可能性：  
  
- 如果事件接收器已實行， <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> 您可以訂閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>  
  
- 否則，您可以訂閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> 。  
  
  以下是假設的檔存取案例。 Visual Studio 擴充功能想要顯示有關開啟檔的一些資訊，例如編輯鎖定計數，以及檔資料的相關內容。 它會使用來列舉 RDT 中的檔 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> ，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 每個檔，以取得編輯鎖定計數和檔資料。 如果檔處於擱置中的初始化狀態，要求檔資料會導致非必要地將它初始化。  
  
  更有效率的方法是使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 來取得編輯鎖定計數，然後使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> 判斷是否已初始化檔。 如果旗標不包含 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> ，則檔已初始化，而要求檔資料不 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 會造成任何不必要的初始化。 如果旗標包含 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> ，擴充功能應該避免要求檔資料，直到檔初始化。 這可以在 OnAfterAttributeChange (例如) 事件處理常式中偵測到。  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>測試擴充功能以查看是否強制初始化  
 沒有可見的提示可指出檔是否已初始化，因此很難找出您的延伸模組是否強制執行初始化。 您可以設定登錄機碼讓驗證變得更容易，因為它會導致每份未完全初始化的檔標題都具有 `[Stub]` 標題中的文字。  
  
 在**HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]** 中，將**StubTabTitleFormatString**設定為** {0} [Stub]**。
