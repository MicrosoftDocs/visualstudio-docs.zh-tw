---
title: 使用存放區檢視進行偵錯
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 79e995393c02f96561d3283f4181b3a7159f0832
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856440"
---
# <a name="debugging-by-using-the-store-viewer"></a>使用存放區檢視進行偵錯
使用儲存的檢視器 中，您可以檢查的狀態*儲存*供[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]。 儲存的檢視器會顯示所有的網域模型項目處於為特定的存放區，以及項目屬性和項目之間的連結。

## <a name="opening-store-viewer"></a>開啟存放區檢視器
 當您在 Visual Studio 的實驗組建中，停止於中斷點的程式碼存放區的執行個體包含模型資訊的位置。 然後，輸入下列命令中的，開啟存放區檢視**Immediate**視窗：

```csharp
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
>  您必須取代`mystore`存放區執行個體的名稱。 此外，如果您的命名空間新增至您的程式碼時，您可以輸入命令來顯示存放區檢視，而不需要完整的命名空間：
>
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
>  `...`
>
>  `StoreViewer.Show(mystore);`

 `Show`方法有數個多載。 您可以指定存放區或分割區的執行個體做為參數。

 或者，您可以放入存放區檢視顯示程式碼中的任何位置的程式碼行，您傳遞給參數`Show`方法是在範圍內。 下的一行程式碼會執行的內容存放區的快照集時，此動作就會顯示儲存的檢視器。

### <a name="using-store-viewer"></a>使用存放區檢視
 當存放區檢視器開啟時，則非強制回應的 Windows Form 視窗隨即出現，如下圖所示。

 ![](../modeling/media/storeviewer2.png) 存放區檢視

 存放區檢視有三個窗格︰ 左的窗格中，右上方窗格中和右下方的窗格。 左的窗格是樹狀檢視中的型別`DomainDataDirectory`存放區的成員。 如果您展開 [資料分割] 節點，然後按一下項目，則會在右上方窗格中顯示項目的屬性。 如果項目連結至其他項目，則會在右下方窗格中顯示的其他項目。 如果您按兩下右下方窗格中的項目，項目會在左窗格中反白顯示。

## <a name="see-also"></a>另請參閱

- [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)