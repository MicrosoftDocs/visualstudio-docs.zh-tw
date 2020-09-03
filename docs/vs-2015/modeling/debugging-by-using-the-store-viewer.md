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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654882"
---
# <a name="debugging-by-using-the-store-viewer"></a>使用存放區檢視進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用存放區檢視器時，您可以檢查所使用之 *存放區* 的狀態 [!INCLUDE[dsl](../includes/dsl-md.md)] 。 存放區檢視器會顯示特定存放區中的所有網域模型專案，以及元素屬性和專案之間的連結。

## <a name="opening-store-viewer"></a>開啟存放區檢視器
 當您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實驗組建中時，請在存放區實例包含模型資訊的中斷點處停止您的程式碼。 然後 **，在 [即時運算] 視窗** 中輸入下列命令，以開啟存放區檢視器：

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> 您必須 `mystore` 以您的存放區實例名稱取代。 此外，如果您將命名空間加入至您的程式碼，您可以輸入命令，以顯示沒有完整命名空間的存放區檢視器：
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 `Show`方法有數個多載。 您可以指定存放區的實例或資料分割做為參數。

 或者，您可以將程式程式碼放在程式碼中的任何位置，而您傳遞給方法的參數 `Show` 在範圍內。 當程式程式碼執行為存放區內容的快照集時，此動作會顯示商店檢視器。

### <a name="using-store-viewer"></a>使用存放區檢視器
 當儲存區檢視器開啟時，不會出現非模式 Windows Forms 視窗，如下圖所示。

 ![](../modeling/media/storeviewer2.png "storeviewer2") 存放區檢視器

 存放區檢視器有三個窗格：左窗格、右上角窗格和右下角窗格。 左窗格是存放區成員中類型的樹狀檢視 `DomainDataDirectory` 。 如果您展開 [分割區] 節點並按一下專案，則專案的屬性會出現在右上方的窗格中。 如果專案連結到其他專案，則其他專案會出現在右下方的窗格中。 如果您按兩下右下方窗格中的元素，則會在左窗格中反白顯示專案。

## <a name="see-also"></a>另請參閱
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
