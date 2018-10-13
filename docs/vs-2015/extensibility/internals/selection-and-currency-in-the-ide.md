---
title: 選取項目及在 IDE 中的貨幣 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fe6d5cb678cade67ef9e46e9b3c113c988bf879
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270919"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE 中的選取項目和貨幣
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]整合式的開發環境 (IDE) 會維護使用選取之使用者的相關資訊目前選取的物件*內容*。 使用選取項目內容中，Vspackage 可以參與貨幣追蹤有兩種：  
  
-   傳播 ide Vspackage 的貨幣資訊。  
  
-   藉由監視使用者在 IDE 中的目前作用中選取項目。  
  
## <a name="selection-context"></a>選取項目內容  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 全域追蹤的 IDE 貨幣，在它自己的全域選擇內容物件。 下表顯示的項目組成的選取項目內容。  
  
|元素|描述|  
|-------------|-----------------|  
|目前的階層|通常是目前的專案;NULL 目前的階層表示整個方案是最新。|  
|目前的項目識別碼|在目前的階層架構中，選取的項目在 [專案] 視窗中的多個選取項目時，可以有多個目前的項目。|  
|目前 `SelectionContainer`|保留為其 [屬性] 視窗應顯示屬性的一或多個物件。|  
  
 此外，環境會維護兩個全域清單：  
  
-   使用 UI 命令識別碼的清單  
  
-   目前使用中的項目型別的清單。  
  
### <a name="window-types-and-selection"></a>視窗類型和選取範圍  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 會將 windows 組織成兩種一般類型：  
  
-   階層類型 windows  
  
-   框架視窗，例如工具和文件視窗  
  
 IDE 追蹤的每個視窗類型不同貨幣。  
  
 最常見的 [專案類型] 視窗是方案總管中，IDE 會控制。 專案類型 視窗會追蹤項目識別碼的全域的選取項目內容中，與全域階層，視窗仰賴使用者的選取項目，來判斷目前的階層。 適用於專案類型 windows 環境提供 「 全域服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>，透過的 Vspackage 可以監視目前開啟的項目值。 瀏覽環境中的屬性是此全域服務所驅動。  
  
 框架視窗，相反地，會使用在框架視窗內 DocObject 推送 SelectionContext 值 （階層/ItemID/SelectionContainer 事）。 。 框架視窗使用服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>針對此目的。 DocObject 可以推送只有值選取項目容器，讓階層的本機值和項目識別碼不變，如同典型的 MDI 子文件。  
  
### <a name="events-and-currency"></a>事件和貨幣  
 兩種類型的事件可能會發生影響環境的概念的貨幣：  
  
-   會傳播到全域層級，而變更視窗框架的選取項目內容的事件。 這類事件的範例包括開啟，全域工具視窗開啟或開啟一個專案類型的工具視窗的 MDI 子視窗。  
  
-   追蹤視窗框架的選取項目內容中的項目進行變更的事件。 範例包括變更選取項目內 DocObject 或變更專案類型 視窗中的選取項目。  
  
## <a name="see-also"></a>另請參閱  
 [選取內容物件](../../extensibility/internals/selection-context-objects.md)   
 [使用者的意見反應](../../extensibility/internals/feedback-to-the-user.md)

