---
title: 使用存放區檢視器進行偵錯工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654882"
---
# <a name="debugging-by-using-the-store-viewer"></a>使用存放區檢視進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用存放區檢視器，您可以檢查 [!INCLUDE[dsl](../includes/dsl-md.md)] 所使用之*存放區*的狀態。 [存放區檢視器] 會顯示特定存放區中的所有領域模型專案，以及專案屬性和元素之間的連結。

## <a name="opening-store-viewer"></a>開啟存放區檢視器
 當您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實驗性組建中時，請在存放區實例包含模型資訊的中斷點上停止您的程式碼。 然後，在 [即時運算] 視窗中輸入下列命令，以開啟 [存放區查看**器]：**

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> 您必須以您的存放區實例名稱取代 `mystore`。 此外，如果您將命名空間新增至程式碼，您可以輸入命令來顯示存放區檢視器，而不需要完整的命名空間：
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 @No__t_0 方法有數個多載。 您可以將存放區或資料分割的實例指定為參數。

 或者，您可以將顯示存放區檢視器的程式程式碼放在程式碼中的任何位置，而您傳遞給 `Show` 方法的參數會在範圍中。 當程式程式碼以存放區內容的快照集執行時，此動作會顯示 [存放區檢視器]。

### <a name="using-store-viewer"></a>使用存放區檢視器
 當 [存放區檢視器] 開啟時，會出現非模式 Windows Forms 視窗，如下圖所示。

 ![](../modeling/media/storeviewer2.png "storeviewer2")儲存區檢視器

 存放區檢視器有三個窗格：左窗格、右上角窗格和右下方的窗格。 左窗格是存放區 `DomainDataDirectory` 成員中類型的樹狀檢視。 如果您展開分割區節點，然後按一下某個元素，則專案的屬性會出現在右上方的窗格中。 如果專案已連結至其他專案，則其他元素會出現在右下方的窗格中。 如果您按兩下右下方窗格中的元素，則會在左窗格中反白顯示元素。

## <a name="see-also"></a>請參閱
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
