---
title: 屬性視窗按鈕 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706179"
---
# <a name="properties-window-buttons"></a>屬性視窗的按鈕
根據開發語言和產品類型,某些按鈕預設顯示在 **「屬性」** 視窗的工具列上。 在所有情況下,將顯示 **「分類**、**字母表」****屬性**和**屬性頁**按鈕。 在"視覺 C#"和"可視基本"中,還會顯示 **"事件**"按鈕。 在某些視覺C++專案中,將顯示**VC++ 消息**和**VC 覆蓋**按鈕。 可能顯示其他項目類型的按鈕。 關於 **「屬性」** 視窗中的按鈕的詳細資訊,請參閱[屬性視窗](../../ide/reference/properties-window.md)。

## <a name="implementation-of-properties-window-buttons"></a>屬性視窗按鈕的實作
 按下 **「分類」** 按鈕時,Visual Studio 會<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>呼叫具有焦點的物件上的介面,以便按類別對其屬性進行排序。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>在顯示到`IDispatch`**「屬性」** 視窗的物件上實現。

 有 11 個預定義的屬性類別,這些類別具有負值。 您可以定義自定義類別,但我們建議您為其分配正值,以將其與預定義的類別區分開來。

 該方法<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>返回指定屬性的相應屬性類別值。 該方法<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>傳回包含類別名稱的字串。 您只需要支援自定義類別值,因為 Visual Studio 知道標準屬性類別值。

 按下 **「字母」** 按鈕時,屬性按名稱按字母順序顯示。 根據當地語系化排序演`IDispatch`演算法檢索 名稱。

 當 **「屬性」** 視窗打開時,「**屬性**」 按鈕將自動顯示為所選。 在環境的其他部分,將顯示相同的按鈕,您可以按下它以顯示 **「屬性」** 視窗。

 如果未`ISpecifyPropertyPages`為所選物件實現,則「**屬性頁**」按鈕不可用。 屬性頁顯示通常與解決方案和專案關聯的與配置相關的屬性,但它們也可以與專案項相關聯(例如,在 Visual C++中)。

> [!NOTE]
> 不能使用非託管代碼將工具列按鈕添加到 **「屬性」** 視窗。 要添加工具列按鈕,必須創建派生自<xref:System.Windows.Forms.Design.PropertyTab>的託管物件。

## <a name="see-also"></a>另請參閱
- [擴充屬性](../../extensibility/internals/extending-properties.md)
