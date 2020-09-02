---
title: 如何：使用 WPF 樹狀架構視覺化 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 381dc45351ae03e615afbdd31239869e3dba8e4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825440"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>如何：使用 WPF 樹狀架構視覺化檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 [WPF 樹狀架構視覺化檢視] 瀏覽 WPF 物件的視覺化樹狀結構，以及檢視該樹狀結構內含物件的 WPF 相依性屬性。 如需視覺化樹狀結構的詳細資訊，請參閱 [WPF 中的樹狀](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)結構。 如需相依性屬性的詳細資訊，請參閱相依性 [屬性總覽](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)。  
  
 當您開啟 WPF 樹狀結構視覺效果時，您會看到兩個窗格：左邊的**視覺化樹狀結構**和右邊的 [_名稱_**：**_類型_的**屬性**] 窗格。 在**視覺化樹狀結構**窗格中選取任何物件，[ **Properties of** _名稱_**：**_類型_] 窗格的屬性會自動更新，以顯示該物件的屬性。  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>若要開啟 WPF 樹狀架構視覺化檢閱  
  
1. 在 DataTip [監看式]**** 視窗、[自動變數]**** 視窗或 [區域變數]**** 視窗中，在 WPF 物件名稱旁，按一下放大鏡圖示旁邊的箭號。  
  
     視覺化檢視的清單隨即顯示。  
  
2. 按一下 [WPF 樹狀架構視覺化檢閱]****。  
  
### <a name="to-search-the-visual-tree"></a>若要搜尋視覺化樹狀結構  
  
- 在 [視覺化樹狀]**** 窗格的 [搜尋]**** 方塊中，鍵入要搜尋的字串。  
  
  [WPF 樹狀架構視覺化檢視] 會立即在視覺化樹狀結構中，尋找第一個符合您輸入之字串的物件。 輸入越多字元，尋找的相符項目越精確。  

  - 若要移至視覺化樹狀中的下一個相符項目，請按 [下一個]****。  

  - 若要移至上一個符合項目，則按一下 [上一個]****。  

  - 若要清除搜尋準則，請按一下 [清除]****。  

### <a name="to-search-the-properties-list"></a>若要搜尋屬性清單  
  
- 在 [ **Properties of** _名稱_**：**_類型_的屬性] 窗格的 [**篩選**] 方塊中，輸入您想要搜尋的字串。  
  
  [WPF 樹狀架構視覺化檢視] 會立即尋找符合您輸入之字串的屬性；現在，清單只會顯示符合您所輸入字串的屬性。 輸入越多字元，尋找的相符項目越精確。  

  - 若要清除搜尋準則，請按一下 [清除]****。  
  
### <a name="to-close-the-visualizer"></a>若要關閉視覺化檢視  
  
- 按一下對話方塊右上角中的 [關閉]**** 圖示。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用視覺化檢視](../misc/how-to-use-a-visualizer.md)   
 [建立自訂的視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [WPF 中的樹狀結構](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [相依性屬性總覽](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)
