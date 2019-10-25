---
title: 屬性視窗按鈕 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2a41917a58a6fc5780b62c2c9e3db8aa52d407
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725263"
---
# <a name="properties-window-buttons"></a>屬性視窗的按鈕
根據 [開發語言] 和 [產品類型] 而定，預設會在 [**屬性**] 視窗的工具列上顯示特定按鈕。 在所有情況下，會顯示 [**分類**]、[**字母順序**]、[**屬性**] 和 [**屬性頁**] 按鈕。 在  C#視覺效果 和 Visual Basic 中，也會顯示 **事件** 按鈕。 在某些視覺C++專案中，會顯示 [ **Vc + + 訊息**] 和 [ **vc 覆寫**] 按鈕。 其他專案類型可能會顯示其他按鈕。 如需有關 [**屬性**] 視窗中按鈕的詳細資訊，請參閱[屬性視窗](../../ide/reference/properties-window.md)。

## <a name="implementation-of-properties-window-buttons"></a>[屬性] 視窗按鈕的執行
 當您按一下 [**分類**] 按鈕時，Visual Studio 會在物件上呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 介面，而焦點是依類別目錄排序其屬性。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 會在呈現給 [**屬性**] 視窗的 `IDispatch` 物件上執行。

 有11個預先定義的屬性類別，其具有負值。 您可以定義自訂類別，但我們建議您指派正值來區別它們與預先定義的類別。

 @No__t_0 方法會針對指定的屬性傳回適當的屬性類別目錄值。 @No__t_0 方法會傳回包含類別目錄名稱的字串。 您只需要提供自訂類別值的支援，因為 Visual Studio 知道標準屬性類別目錄值。

 當您按一下按**字母**順序排列的按鈕時，屬性會依名稱以字母順序顯示。 根據當地語系化的排序演算法，`IDispatch` 會抓取名稱。

 當 [**屬性**] 視窗開啟時，[**屬性**] 按鈕會自動顯示為 [已選取]。 在環境的其他部分中，會顯示相同的按鈕，您可以按一下它來顯示 [**屬性**] 視窗。

 如果未針對選取的物件執行 `ISpecifyPropertyPages`，就無法使用 [**屬性頁**] 按鈕。 屬性頁會顯示與方案和專案相關的設定相依屬性，但它們也可以與專案專案相關聯（例如，在 Visual C++中）。

> [!NOTE]
> 您不能使用未受管理的程式碼，將工具列按鈕加入 [**屬性**] 視窗中。 若要加入工具列按鈕，您必須建立衍生自 <xref:System.Windows.Forms.Design.PropertyTab> 的 managed 物件。

## <a name="see-also"></a>請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)