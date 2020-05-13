---
title: 延遲文件載入 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708817"
---
# <a name="delayed-document-loading"></a>延遲的文件載入

當使用者重新打開 Visual Studio 解決方案時,大多數關聯的文檔不會立即載入。 文件視窗框架以掛起初始化狀態創建,占位符文件(稱為存根框架)放置在正在運行的文檔表 (RDT) 中。

通過載入文檔中的元素,擴展可能會導致專案文檔不必要地載入,這會增加 Visual Studio 的總體記憶體佔用空間。

## <a name="document-loading"></a>文件載入

當使用者訪問文檔時,通過選擇視窗框架的選項卡,將完全初始化存根框架和文檔。 文檔還可以通過請求文件資料的擴展進行初始化,該擴展通過直接存取 RDT 獲取文件數據,或者通過進行以下調用之一間接存取 RDT:

- 視窗框架<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>方法。

- 以下任一<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>屬性上的視窗框架方法:

  - [__VSFPROPIDVSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPIDVSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPIDVSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPIDVSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPIDVSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPIDVSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- 如果延伸使用託管代碼,則不應呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>,除非您確定文件未處於掛起初始化狀態,或者您希望文檔完全初始化。 原因是該方法始終返回 doc 數據物件,並在必要時創建它。 相反,您應該調用`IVsRunningDocumentTable4`介面上的一種方法。

- 如果擴展使用C++,則可以傳遞`null`不需要的參數。

- 在請求其他屬性之前,可以通過調用以下方法之一來避免不必要的文檔載入:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>使用[__VSFPROPID6。VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>). .

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 這個方法傳回<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>含有 _VSRDTFLAGS4值的物件[。如果](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)文檔尚未初始化,RDT_PendingInitialization。

通過訂閱文檔完全初始化時引發的 RDT 事件,可以找出文檔載入時間。 有兩種可能性:

- 如果事件接收器實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>,則可以<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>訂閱 。

- 否則,您可以訂閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>。

下面的範例是假設的文件存取方案:Visual Studio 擴展希望顯示有關打開文檔的一些資訊,例如編輯鎖計數和文件數據。 它使用<xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>枚舉 RDT 中的<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A>文件,然後調用每個文檔以檢索編輯鎖計數和文檔數據。 如果文件處於掛起的初始化狀態,則請求文檔數據會導致它不必要地初始化。

訪問文檔的更有效方法是<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A>使用 來獲取編輯鎖計數,<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>然後用於確定文檔是否已初始化。 如果標誌不包含[_VSRDTFLAGS4。RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>),文檔已初始化,<xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A>請求文檔 資料不會導致任何不必要的初始化。 如果標誌包含[_VSRDTFLAGS4。RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>),擴展應避免請求文檔資料,直到文檔初始化。 可以在事件處理程式中`OnAfterAttributeChange(Ex)`檢測到此初始化。

## <a name="test-extensions-to-see-if-they-force-initialization"></a>測試延伸以檢視它們是否強制初始化

沒有指示文件是否已初始化的可見提示,因此很難確定擴展是否強制初始化。 您可以設置一個註冊表項,使驗證更容易,因為它會導致未完全初始化的每個文檔的標題在標題中包含文本 *[Stub]。*

在**HKEY_CURRENT_USER_軟體\微軟_VisualStudio_14.0\背景解決方案載入中**,將**StubTabTitle格式字串**設置為*{0}[Stub]。*
