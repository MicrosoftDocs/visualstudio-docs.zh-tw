---
title: 模型的原始檔控制套件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa0dcdd930412e4e53c59509848f0b7c1503c47b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129439"
---
# <a name="model-for-source-control-packages"></a>原始檔控制套件的模型
下列模型代表來源控制項實作的範例。 在模型中，您會看到您必須實作的介面和環境服務，您必須呼叫。 如同所有的服務，您實際上會呼叫您透過服務所取得的特定介面的方法。 若要更輕鬆地查看原始檔控制會實行識別的類別名稱。  
  
 ![SCC&#95;TUP 範例](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
範例原始檔控制專案  
  
## <a name="interfaces"></a>介面  
 您可以針對您新的專案類型，在 Visual Studio 中使用下表所示的介面清單實作原始檔控制。  
  
|介面|使用|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|專案和編輯器儲存它們或變更 (dirty) 檔案之前呼叫。 這個介面使用存取<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|呼叫要求權限，才能新增、 移除或重新命名檔案或目錄的專案。 此介面也會呼叫以通知環境已核准的新增、 移除或重新命名動作時已完成的專案。 使用存取<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|藉由加入、 重新命名或移除檔案或目錄的專案時收到通知註冊的任何實體。 若要註冊事件通知，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|呼叫專案與原始檔控制封裝註冊並取得原始檔控制狀態的詳細資訊。 這個介面使用存取<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>服務。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|藉由專案，以回應檔案的相關資訊的來源控制要求，並取得原始檔控制專案檔案所需的設定。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)