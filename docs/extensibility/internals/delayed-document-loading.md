---
title: 延遲的檔載入 |Microsoft Docs
description: 瞭解 Visual Studio 中的延遲檔載入，以及如何撰寫延伸模組的程式碼，使其不會在檔載入前查詢檔中的元素。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6489c819efe0fd29cd2d120c08414cf0532ad6f
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328388"
---
# <a name="delayed-document-loading"></a>延遲的檔載入

當使用者重新開啟 Visual Studio 方案時，大部分相關聯的檔都不會立即載入。 文件視窗框架會以暫止的初始化狀態建立，而預留位置檔 (稱為存根框架) 放置於執行中的檔資料表 (RDT) 。

您的延伸模組可能會在載入檔之前，藉由查詢檔中的專案來不必要地載入專案檔案，而這可能會增加 Visual Studio 的整體記憶體量。

## <a name="document-loading"></a>檔載入

當使用者存取檔時，會完全初始化存根框架和檔，例如，藉由選取視窗框架的索引標籤。 您也可以藉由要求檔資料的延伸模組來初始化檔，方法是直接存取 RDT 以取得檔資料，或藉由進行下列其中一項呼叫來間接存取 RDT：

- 視窗框架 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 方法。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>下列任何屬性的視窗框架方法：

  - [__VSFPROPID。VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID。VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID。VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID。VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID。VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID。VSFPROPID_SPProjCoNtext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- 如果您的延伸模組使用 managed 程式碼， <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 除非您確定檔不是處於暫止初始化狀態，或是您想要讓檔完全初始化，否則您不應該呼叫。 原因是此方法一律會傳回檔資料物件，並在必要時建立它。 相反地，您應該在介面上呼叫其中一個方法 `IVsRunningDocumentTable4` 。

- 如果您的延伸模組使用 c + +，您可以 `null` 針對不想要的參數傳遞。

- 您可以先呼叫下列其中一種方法來避免不必要的檔載入，然後再要求相關屬性，然後再要求其他屬性：

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 使用 [__VSFPROPID6。VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>)。

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 這個方法會傳回 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 包含 _VSRDTFLAGS4 值的物件 [。](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) 如果檔尚未初始化，則為 RDT_PendingInitialization。

您可以藉由訂閱已完全初始化檔時所引發的 RDT 事件，找出檔載入的時間。 有兩種可能性：

- 如果事件接收器已實行， <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> 您可以訂閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>

- 否則，您可以訂閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> 。

下列範例是假設性的檔存取案例： Visual Studio 擴充功能想要顯示有關開啟檔的一些資訊，例如編輯鎖定計數，以及檔資料的相關事項。 它會使用來列舉 RDT 中的檔 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> ，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 每個檔，以取得編輯鎖定計數和檔資料。 如果檔處於擱置中的初始化狀態，要求檔資料會導致非必要地將它初始化。

存取檔的更有效率的方式是使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 來取得編輯鎖定計數，然後使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> 判斷是否已初始化檔。 如果旗標不包含 [_VSRDTFLAGS4。RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)，檔已初始化，而要求檔資料時，並 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 不會造成任何不必要的初始化。 如果旗標包含 [_VSRDTFLAGS4。RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)，此延伸模組應避免要求檔資料，直到檔初始化。 您可以在事件處理常式中偵測到此初始化 `OnAfterAttributeChange(Ex)` 。

## <a name="test-extensions-to-see-if-they-force-initialization"></a>測試擴充功能以查看是否強制初始化

沒有可見的提示可指出檔是否已初始化，因此很難找出您的延伸模組是否強制執行初始化。 您可以設定登錄機碼讓驗證變得更容易，因為它會導致未完全初始化的每個檔的標題都有標題中的文字 *[Stub]* 。

在 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad** 中，將 **StubTabTitleFormatString** 設定為 *{0} [Stub]*。
