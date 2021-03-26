---
title: 原始檔控制套件的模型 |Microsoft Docs
description: 此模型代表原始檔控制執行。 本文會顯示類別的名稱，讓您更輕鬆地查看如何執行原始檔控制。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4e437afdfa0d3de03da6814e221840cbd0763fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063197"
---
# <a name="model-for-source-control-packages"></a>原始檔控制套件的模型
下列模型代表原始檔控制執行的範例。 在模型中，您會看到必須執行的介面，以及您必須呼叫的環境服務。 就像所有的服務一樣，您實際上會呼叫透過服務所取得之特定介面的方法。 系統會識別類別的名稱，讓您更輕鬆地查看如何執行原始檔控制。

 ![SCC&#95;設定範例](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") 範例原始檔控制專案

## <a name="interfaces"></a>介面
 您可以使用下表所示的介面清單，在 Visual Studio 中為新的專案類型執行原始檔控制。

|介面|使用|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|由專案和編輯器呼叫，然後再儲存或變更 (的變更) 檔。 您可以使用服務來存取這個介面 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|由專案呼叫，以要求新增、移除或重新命名檔案或目錄的許可權。 專案也會呼叫這個介面，以在已核准的新增、移除或重新命名動作完成時通知環境。 您可以使用服務來存取它 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|由註冊要在專案新增、重新命名或移除檔案或目錄時收到通知的任何實體所執行。 若要註冊事件通知，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|由專案呼叫，以向原始檔控制封裝註冊，以及取得原始檔控制狀態的資訊。 您可以使用服務來存取這個介面 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|由專案執行以回應原始檔控制要求，以取得檔案的相關資訊，並取得專案檔所需的原始檔控制設定。|

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
