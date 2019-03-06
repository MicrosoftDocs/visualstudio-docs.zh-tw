---
title: 在 Visual Studio 中的階層 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 437372a5b88e58c12b7a7d34102d87afce5c086b
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841775"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio 中的階層
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 會顯示與專案*階層*。 在 IDE 中，階層是樹狀結構的節點，其中每個節點都有一組相關聯的屬性。 A*專案階層架構*是保留的專案項目，這些項目的關聯性，和的項目相關聯的屬性和命令的容器。

 在  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您使用階層介面，來管理專案階層<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>介面將重新導向來自專案項目叫用適當的階層架構視窗中，而不是標準的命令處理常式的命令。

## <a name="project-hierarchies"></a>專案階層
 每個專案階層架構包含您可以檢視和編輯的項目。 這些項目需視專案類型而有所不同。 例如，資料庫專案可能包含預存程序、 資料庫檢視和資料庫資料表。 相反地，程式設計語言的專案中，將可能包含原始程式檔和點陣圖和對話方塊的資源檔。 階層可以是巢狀，這讓您新增的彈性當您建立專案階層架構。

 當您建立新的專案類型時，專案類型會控制一組完整的可編輯的項目。 不過，專案可以包含項目，它們並沒有編輯支援。 例如，Visual c + + 專案可以包含 HTML 檔案，即使 Visual c + + 不提供任何自訂的編輯器的 HTML 檔案類型。

 階層管理持續提供其所包含的項目。 階層架構的實作必須控制任何特殊的屬性會影響在階層內的項目持續性。 例如，如果項目代表物件，而不是檔案的存放庫中，階層實作必須控制那些物件的持續性。 IDE 本身會指示儲存符合使用者輸入項目階層，但 IDE 不會控制儲存這些項目時所需的任何動作。 相反地，專案是在控制項中。

 當使用者在編輯器中開啟項目時，該項目會控制階層架構就會被選取，並變成作用中的階層。 選取的階層會決定可用的項目上採取行動的命令集。 追蹤使用者焦點以這種方式可讓以反映使用者的目前內容的階層。

## <a name="see-also"></a>另請參閱
- [專案類型](../../extensibility/internals/project-types.md)
- [選取項目及在 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK 範例](https://aka.ms/vs2015sdksamples)