---
title: 屬性視窗按鈕 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 950b9f0a7b0f38689042877a42499e23253e6486
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-buttons"></a>屬性視窗 按鈕
根據開發語言和產品類型，某些按鈕預設會顯示的工具列上的**屬性**視窗。 在所有情況下，**分類**， **Alphabetized**，**屬性**，和**屬性頁**顯示按鈕。 在 Visual C# 和 Visual Basic**事件**按鈕也會顯示。 在特定 Visual c + + 專案中， **VC + + 訊息**和**VC 會覆寫**顯示按鈕。 其他專案類型，可能會顯示其他按鈕。 如需中的按鈕**屬性**視窗中，請參閱[屬性 視窗](../../ide/reference/properties-window.md)。  
  
## <a name="implementation-of-properties-window-buttons"></a>屬性視窗按鈕的實作  
 當您按一下**分類**按鈕，Visual Studio 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>具有焦點，若要依分類排序其屬性的物件上的介面。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>實作上`IDispatch`物件呈現給**屬性**視窗。  
  
 有 11 有負數值的預先定義的屬性類別。 您可以定義自訂分類，但我們建議，您將它們指派來區別預先定義的類別目錄的正數值。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>方法會傳回適當的屬性類別目錄值，指定的屬性。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>方法會傳回包含類別目錄名稱的字串。 您只需要為自訂類別值提供支援，因為 Visual Studio 知道標準屬性類別目錄值。  
  
 當您按一下**Alphabetized**  按鈕，屬性會依字母順序顯示名稱。 名稱藉由擷取`IDispatch`根據當地語系化的排序演算法。  
  
 當**屬性**視窗已開啟，**屬性**按鈕會自動顯示為選取狀態。 環境的其他組件，會顯示相同的按鈕，以及您可以按一下來顯示**屬性**視窗。  
  
 **屬性頁**按鈕便無法使用如果`ISpecifyPropertyPages`針對選取的物件未實作。 屬性頁顯示通常與方案和專案，相關聯的組態相關屬性，但它們也可以與專案項目 （例如，在 Visual c + +） 相關聯。  
  
> [!NOTE]
>  您無法加入工具列按鈕，**屬性**程式使用 unmanaged 程式碼視窗。 若要新增工具列按鈕，您必須建立衍生自的 managed 的物件<xref:System.Windows.Forms.Design.PropertyTab>。  
  
## <a name="see-also"></a>請參閱  
 [擴充屬性](../../extensibility/internals/extending-properties.md)