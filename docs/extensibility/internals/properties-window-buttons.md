---
title: 屬性視窗按鈕 |Microsoft Docs
description: 針對屬性視窗的工具列上預設顯示的按鈕，以及如何執行按鈕的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 601e40762adc665f6241bb00a4b683b81e7fbd80
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970019"
---
# <a name="properties-window-buttons"></a>屬性視窗的按鈕
依開發語言和產品類型而定，預設會在 [ **屬性** ] 視窗的工具列上顯示特定按鈕。 在所有情況下，會顯示 [ **分類**]、[ **字母順序**]、[ **屬性**] 和 [ **屬性頁** ] 按鈕。 在 Visual c # 和 Visual Basic 中，也會顯示 [ **事件** ] 按鈕。 在某些 Visual C++ 專案中，會顯示 [ **vc + + 訊息** ] 和 [ **vc 覆寫** ] 按鈕。 其他專案類型可能會顯示其他按鈕。 如需 [ **屬性** ] 視窗中之按鈕的詳細資訊，請參閱 [屬性視窗](../../ide/reference/properties-window.md)。

## <a name="implementation-of-properties-window-buttons"></a>[屬性] 視窗按鈕的實作為
 當您按一下 [ **分類** ] 按鈕時，Visual Studio 會在 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 具有焦點的物件上呼叫介面，依類別排序其屬性。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 會在 `IDispatch` 呈現給 [ **屬性** ] 視窗的物件上執行。

 有11個預先定義的屬性類別，其具有負數值。 您可以定義自訂類別，但建議您將它們指派為正值，以便與預先定義的類別區別。

 方法會傳回 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> 指定之屬性的適當屬性類別目錄值。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>方法會傳回包含類別目錄名稱的字串。 因為 Visual Studio 知道標準屬性類別目錄值，所以您只需要提供自訂分類值的支援。

 當您按一下 [ **依字母** 順序排列] 按鈕時，屬性會依名稱以字母順序顯示。 系統會 `IDispatch` 根據當地語系化的排序演算法來抓取名稱。

 當 [ **屬性** ] 視窗開啟時，[ **屬性** ] 按鈕會自動顯示為已選取。 在環境的其他部分中，會顯示相同的按鈕，您可以按一下它來顯示 [ **屬性** ] 視窗。

 如果未針對選取的物件執行，則 [ **屬性頁** ] 按鈕 `ISpecifyPropertyPages` 無法使用。 屬性頁會顯示通常與方案和專案相關聯的設定相依屬性，但它們也可以與專案專案相關聯 (例如 Visual C++) 。

> [!NOTE]
> 您無法使用非受控碼將工具列按鈕新增至 [ **屬性** ] 視窗。 若要加入工具列按鈕，您必須建立一個衍生自的 managed 物件 <xref:System.Windows.Forms.Design.PropertyTab> 。

## <a name="see-also"></a>另請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)
