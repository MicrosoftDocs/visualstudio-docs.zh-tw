---
title: "如何： 使用 WPF 樹狀架構視覺化檢閱 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78806b2ace7872db06ff403bcae28bb6eff21cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>如何：使用 WPF 樹狀架構視覺化檢閱
您可以使用 [WPF 樹狀架構視覺化檢閱] 瀏覽 WPF 物件的視覺化樹狀，以及檢閱該樹狀內含物件的 WPF 相依性屬性。 如需視覺化樹狀結構的詳細資訊，請參閱[中 WPF 樹狀架構](/dotnet/framework/wpf/advanced/trees-in-wpf)。 如需相依性屬性的詳細資訊，請參閱[相依性屬性概觀](/dotnet/framework/wpf/advanced/dependency-properties-overview)。  
  
 當您開啟 WPF 樹狀架構視覺化檢視時，您會看到兩個窗格：**視覺化樹狀結構**左側和**屬性***名稱***:** *型別*右邊的窗格。 選取中的任何物件**視覺化樹狀結構** 窗格中，而**屬性***名稱***:***類型*窗格自動更新以顯示該物件的內容。  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>若要開啟 WPF 樹狀架構視覺化檢閱  
  
1.  在資料提示方塊中，**監看式**視窗中，**自動變數**視窗中，或**區域變數**視窗中的，WPF 物件名稱旁邊按一下放大鏡圖示旁邊的箭號。  
  
     視覺化檢視的清單隨即顯示。  
  
2.  按一下**WPF 樹狀架構視覺化檢閱**。  
  
### <a name="to-search-the-visual-tree"></a>若要搜尋視覺化樹狀  
  
-   在**視覺化樹狀結構** 窗格中，輸入您想要搜尋的字串**搜尋**方塊。  
  
     [WPF 樹狀架構視覺化檢閱] 會立即在視覺化樹狀中，尋找第一個符合您輸入之字串的物件。 輸入越多字元，尋找的相符項目越精確。  
  
    -   若要移至下一個相符的視覺化樹狀結構中，按一下**下一步**。  
  
    -   若要返回上一個比對，請按一下**Prev**。  
  
    -   若要清除搜尋準則，請按一下**清除**。  
  
### <a name="to-search-the-properties-list"></a>若要搜尋屬性清單  
  
-   在**屬性***名稱***:***類型* 窗格中，輸入您想要在搜尋字串**篩選**方塊。  
  
     [WPF 樹狀架構視覺化檢閱] 會立即尋找符合您輸入之字串的屬性；現在，清單只會顯示符合您所輸入字串的屬性。 輸入越多字元，尋找的相符項目越精確。  
  
    -   若要清除搜尋準則，請按一下**清除**。  
  
### <a name="to-close-the-visualizer"></a>若要關閉視覺化檢視  
  
-   按一下**關閉**對話方塊右上角的圖示。  
  
## <a name="see-also"></a>請參閱  
 [建立自訂的視覺化檢視](../debugger/create-custom-visualizers-of-data.md)   
 [WPF 中的樹狀結構](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [相依性屬性概觀](/dotnet/framework/wpf/advanced/dependency-properties-overview)