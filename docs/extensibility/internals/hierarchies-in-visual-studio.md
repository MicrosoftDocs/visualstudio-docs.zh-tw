---
title: Visual Studio 中的階層 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08005b69a1af16b07212cb29547875fad89e1d6a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848945"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio 中的階層
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 的整合式開發環境（IDE）會將專案顯示為*階層。* 在 IDE 中，階層是節點的樹狀結構，其中每個節點都有一組相關聯的屬性。 *專案*階層是一個容器，其中包含專案的專案、專案的關聯性，以及專案的相關聯屬性和命令。

 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中，您可以使用階層介面來管理專案階層，<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 介面會將您從專案專案叫用的命令重新導向至適當的階層視窗，而不是標準的命令處理常式。

## <a name="project-hierarchies"></a>專案階層
 每個專案階層都包含可供您查看和編輯的專案。 這些專案會視專案類型而有所不同。 例如，資料庫專案可能包含預存程式、資料庫檢視和資料庫資料表。 另一方面，程式設計語言專案可能會包含點陣圖和對話方塊的原始程式檔和資源檔。 階層可以進行嵌套，讓您在建立專案階層時有一些額外的彈性。

 當您建立新的專案類型時，專案類型會控制可以在其中編輯的一組完整專案。 不過，專案可以包含他們沒有編輯支援的專案。 例如，即使視覺C++效果C++並未提供 html 檔案類型的任何自訂編輯器，visual 專案仍可以包含 html 檔案。

 階層會管理其所包含之專案的持續性。 階層的實體系必須控制任何會影響階層內專案持續性的特殊屬性。 例如，如果專案代表存放庫中的物件，而不是檔案，則階層執行必須控制這些物件的持續性。 IDE 本身會指示階層儲存符合使用者輸入的專案，但 IDE 不會控制儲存這些專案所需的任何動作。 相反地，專案是由控制項所控制。

 當使用者在編輯器中開啟專案時，會選取控制該專案的階層，並成為作用中的階層。 選取的階層會決定可用來對專案採取動作的命令集。 以這種方式追蹤使用者焦點，可以讓階層反映使用者目前的內容。

## <a name="see-also"></a>請參閱
- [專案類型](../../extensibility/internals/project-types.md)
- [IDE 中的選取專案和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
