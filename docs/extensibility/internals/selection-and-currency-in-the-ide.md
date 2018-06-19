---
title: 選取項目及在 IDE 中的貨幣 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8c58cb08f82b10970424600843b0fedcf477fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131261"
---
# <a name="selection-and-currency-in-the-ide"></a>選取項目及在 IDE 中的貨幣
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 可讓您維護使用者的資訊目前選取物件，使用選取*內容*。 與選取項目內容中，Vspackage 可以參與貨幣追蹤有兩種：  
  
-   傳播 ide Vspackage 的貨幣資訊。  
  
-   藉由監視使用者在 IDE 中的目前作用中選取項目。  
  
## <a name="selection-context"></a>選取項目內容  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 全域追蹤的 IDE 貨幣，在它自己的全域選取範圍內容物件。 下表顯示組成的選取項目內容的項目。  
  
|項目|描述|  
|-------------|-----------------|  
|目前的階層|通常是目前的專案。NULL 目前的階層表示整個方案是最新。|  
|目前的項目識別碼|選取的項目內目前的階層。[專案] 視窗中的多個選取項目時，可以有多個目前的項目。|  
|目前的 `SelectionContainer`|保留 [屬性] 視窗應該顯示屬性的一或多個物件。|  
  
 此外，環境會維護兩個全域清單：  
  
-   使用 UI 命令識別碼的清單  
  
-   目前作用中的項目類型的清單。  
  
### <a name="window-types-and-selection"></a>視窗類型和選取範圍  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 會組織成兩種一般的 windows:  
  
-   階層類型 windows  
  
-   框架視窗，例如工具和文件視窗  
  
 IDE 以不同的方式追蹤貨幣的每個視窗類型。  
  
 最常見的 [專案類型] 視窗是 [方案總管]，以控制 IDE。 專案類型視窗追蹤通用的階層和項目識別碼的全域範圍內容，並在視窗依賴使用者的選取項目，來判斷目前的階層。 適用於專案類型 windows 環境提供全域服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>，到哪一個 Vspackage 可以監視目前開啟的項目值。 瀏覽在環境中的屬性是此全域服務所驅動。  
  
 框架視窗，相反地，使用 DocObject 框架視窗內發送 SelectionContext 值 （階層/ItemID/SelectionContainer 三）。 。 框架視窗會使用服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>針對此目的。 DocObject 可以只將值推入選取的容器，離開階層本地的值和項目識別碼不變，是典型的 MDI 子文件。  
  
### <a name="events-and-currency"></a>事件和貨幣  
 兩種類型的事件可能會影響貨幣環境的概念：  
  
-   會傳播到全域層級而變更視窗框架的選取項目內容的事件。 這種事件的範例包括 MDI 子視窗開啟，通用工具視窗開啟或開啟一個專案類型的工具視窗。  
  
-   變更項目追蹤的視窗框架選取項目內容中的事件。 範例包括變更選取範圍內 DocObject 或變更在專案類型 視窗中的選取範圍。  
  
## <a name="see-also"></a>另請參閱  
 [選擇內容物件](../../extensibility/internals/selection-context-objects.md)   
 [使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)