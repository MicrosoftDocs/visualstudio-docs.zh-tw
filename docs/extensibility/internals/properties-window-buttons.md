---
title: 屬性視窗的按鈕 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d21e8d13ef8af83b12d30b6c78c253f371a11c30
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973859"
---
# <a name="properties-window-buttons"></a>屬性視窗的按鈕
根據開發語言和產品類型，顯示特定按鈕的工具列上的預設**屬性**視窗。 在所有情況下，**分類**， **Alphabetized**，**屬性**，以及**屬性頁**顯示按鈕。 在 Visual C# 和 Visual Basic**事件**按鈕也會顯示。 在特定 Visual c + + 專案中， **VC + + 訊息**並**VC 會覆寫**顯示按鈕。 其他按鈕可能會顯示其他專案類型。 如需中的按鈕**屬性** 視窗中，請參閱[屬性 視窗](../../ide/reference/properties-window.md)。  
  
## <a name="implementation-of-properties-window-buttons"></a>實作的屬性視窗的按鈕  
 當您按一下 **分類**按鈕，Visual Studio 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>具有焦點，若要依分類排序其屬性的物件上的介面。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 實作，則`IDispatch`物件，會向**屬性**視窗。  
  
 有 11 有負值的預先定義的屬性分類。 您可以定義自訂類別，但我們建議您指派它們以便區別預先定義的類別目錄的正數值。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>方法會傳回指定之屬性的適當的屬性類別目錄值。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>方法會傳回包含分類名稱的字串。 您只需要提供自訂的類別目錄值的支援，因為 Visual Studio 知道標準屬性類別目錄值。  
  
 當您按一下 [ **Alphabetized** ] 按鈕，依名稱依字母順序顯示的屬性。 名稱藉由擷取`IDispatch`根據當地語系化的排序演算法。  
  
 當**屬性**視窗開啟時，**屬性**按鈕時會自動顯示為已選取。 在環境的其他部分，會顯示相同的按鈕，以及您可以按一下來顯示**屬性**視窗。  
  
 **屬性頁**按鈕便無法使用如果`ISpecifyPropertyPages`針對選取的物件未實作。 屬性頁通常與方案和專案，相關聯的顯示組態相依屬性，但它們也可以與專案項目 （例如，在 Visual c + +） 相關聯。  
  
> [!NOTE]
>  您無法加入至工具列按鈕**屬性**使用 unmanaged 程式碼的視窗。 若要加入的工具列按鈕，您必須建立衍生自的 managed 的物件<xref:System.Windows.Forms.Design.PropertyTab>。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)