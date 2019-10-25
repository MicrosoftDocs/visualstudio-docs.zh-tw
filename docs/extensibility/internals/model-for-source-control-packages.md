---
title: 原始檔控制套件的模型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a9ae5f2704d625da2212e92626c33fb384ebbc5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726558"
---
# <a name="model-for-source-control-packages"></a>原始檔控制套件的模型
下列模型代表原始檔控制執行的範例。 在模型中，您會看到必須執行的介面，以及您必須呼叫的環境服務。 就像所有服務一樣，您實際上會呼叫您透過服務取得的特定介面的方法。 系統會識別類別的名稱，讓您更輕鬆地查看原始檔控制的執行方式。

 ![SCC&#95;安裝範例](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")範例原始檔控制專案

## <a name="interfaces"></a>介面
 您可以使用下表所示的介面清單，在 Visual Studio 中為新的專案類型執行原始檔控制。

|介面|請使用|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|專案和編輯器在儲存或變更檔案之前呼叫。 這個介面是使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 服務來存取。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|由專案呼叫，以要求加入、移除或重新命名檔案或目錄的許可權。 專案也會呼叫這個介面，以在已核准的新增、移除或重新命名動作完成時通知環境。 它是使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> 服務來存取。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|由註冊要在專案新增、重新命名或移除檔案或目錄時收到通知的任何實體所執行。 若要註冊事件通知，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|由專案呼叫以向原始檔控制封裝註冊，並取得原始檔控制狀態的資訊。 這個介面是使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 服務來存取。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|由專案所執行，以回應原始檔控制要求，以取得檔案的相關資訊，以及取得專案檔所需的原始檔控制設定。|

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)