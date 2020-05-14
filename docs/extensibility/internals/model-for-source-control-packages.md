---
title: 源控制套件模型 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707076"
---
# <a name="model-for-source-control-packages"></a>原始檔控制套件的模型
以下模型表示原始程式碼管理實現的範例。 在模型中,您將看到必須實現的介面和必須調用的環境服務。 與所有服務一樣,您實際上調用通過服務獲取的特定介面的方法。 標識類的名稱是為了更輕鬆地查看原始程式碼管理是如何執行的。

 ![SCC&#95;TUP 範例](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")來源控制項目範例

## <a name="interfaces"></a>介面
 您可以使用下表中顯示的介面清單在 Visual Studio 中實現新項目類型的原始程式碼管理。

|介面|使用|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|在專案和編輯器保存或更改(臟)檔之前調用它們。 使用此<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>服務訪問此介面。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|由專案呼叫以請求添加、刪除或重命名檔案或目錄的許可權。 專案還會調用此介面,以便在完成已批准的添加、刪除或重命名操作時通知環境。 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>服務訪問它。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|由註冊在專案添加、重新命名或刪除檔或目錄時收到通知的任何實體實現。 要註冊事件通知,請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|被專案調用以註冊原始程式碼管理包並獲取有關原始程式碼管理狀態的資訊。 使用此<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>服務訪問此介面。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|由項目實現,以回應源控制請求,以獲取有關文件的資訊,並獲取專案檔所需的原始程式碼管理設置。|

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
