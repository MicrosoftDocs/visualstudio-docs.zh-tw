---
title: 使用 DSL 定義圖 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0874d5eff99b7e37807daee7115e66740d2661d8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488546"
---
# <a name="working-with-the-dsl-definition-diagram"></a>使用 DSL 定義圖表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[使用 DSL 定義圖表](https://docs.microsoft.com/visualstudio/modeling/working-with-the-dsl-definition-diagram)。  
  
圖表[!INCLUDE[dsl](../includes/dsl-md.md)]定義是定義特定領域語言的重要工具。 您可以將項目加入至網域模型，並定義圖表上的關聯性；也可以修改圖表配置，讓圖表更容易讀取。  
  
## <a name="the-layout-of-the-diagram"></a>圖表配置  
 [!INCLUDE[dsl](../includes/dsl-md.md)]定義圖表包含兩個資料分割**類別和關聯性**分割區和**圖表項目**資料分割。 **類別和關聯性**分割區顯示網域類別、 網域關聯性和繼承。 **圖表項目**分割區顯示圖形類別、 連接線類別、 區隔線類別和產生的設計工具圖表。  
  
 網域類別會在多個位置中出現**類別和關聯性**資料分割。 如果網域類別不是其他網域類別的基底類別，網域類別定義會顯示繼承樹狀結構；如果網域類別是內嵌關聯性或參考關聯性的來源，網域類別定義會顯示關聯性樹狀結構。 網域類別預留位置會顯示為內嵌關聯性或參考關聯性的目標。 根據預設，預留位置項目會顯示與**定義域屬性**摺疊的區間。 這些項目不會顯示繼承，也不會顯示內嵌關聯性或參考關聯性。  
  
 當您新增網域類別時，它會出現在下半部**類別和關聯性**資料分割。 當您加入內嵌關聯性或參考關聯性時，會在來源網域類別右下方繪製此關聯性。  
  
 當您加入網域類別和關聯性時，會變得很難尋找特定網域類別。 您可以找到網域類別，以滑鼠右鍵按一下它**DSL Explorer** ，然後按一下**在圖表中的尋找**。  
  
 下列各節說明如何變更圖表的外觀，讓圖表更容易讀取。  
  
## <a name="copying-elements"></a>複製項目  
 您可以在 DSL 定義圖表中，複製、剪下及貼上項目。  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>放大或縮小圖表  
 您可以使用放大或縮小圖表**DSL 設計工具**工具列設定縮放層級。  
  
## <a name="hiding-map-lines"></a>隱藏對應線  
 對應線是在網域類別或網域關聯性與其所對應的圖形或連接線之間繪製的線條。 您可以按一下隱藏對應線**顯示對應線**按鈕**DSL 設計工具**工具列。 若要顯示線條，請再按一次按鈕。  
  
## <a name="changing-the-diagram-layout"></a>變更圖表配置  
 您可以變更版面配置**類別和關聯性**資料分割，如下所示。  
  
### <a name="expandcollapse"></a>展開/摺疊  
 您可以用滑鼠右鍵按一下它，然後按一下代表網域類別或圖形的區間圖形項目大小的縮減**摺疊**。 這可能會隱藏**定義域屬性**圖形的區間。 若要顯示**定義域屬性**區間一次，以滑鼠右鍵按一下圖形，然後按一下**展開**。  
  
### <a name="move-updown"></a>上移/下移  
 您可以移動網域類別或圖表項目向上或向下資料分割中項目上按一下滑鼠右鍵，然後按一下**下移**或是**下移**。 如果您移動顯示為內嵌關聯性或參考關聯性目標的預留位置項目，關聯性會隨之移動。  
  
### <a name="expandcollapse-relationships-tree"></a>展開/摺疊關聯性樹狀結構  
 如果網域類別與其他網域類別的內嵌或參考關聯性中扮演來源角色，您可以隱藏關聯性，以滑鼠右鍵按一下網域類別定義，然後按一下**摺疊關聯性樹狀結構**。 若要顯示關聯性，以滑鼠右鍵按一下定義項目，然後按一下 **展開關聯性樹狀結構**。  
  
### <a name="expandcollapse-inheritance-tree"></a>展開/摺疊繼承樹狀結構  
 如果網域類別是其他網域類別的基底類別，您可以隱藏繼承樹狀結構，以滑鼠右鍵按一下網域類別定義，然後按一下**摺疊繼承樹狀結構**。 若要顯示繼承樹狀結構，以滑鼠右鍵按一下定義項目，然後按一下**展開繼承樹狀結構**。  
  
### <a name="bring-tree-here"></a>Bring Tree Here  
 您可以合併圖表，以滑鼠右鍵按一下預留位置網域類別，然後按一下**此處將樹狀結構**。 預留位置網域類別會成為定義項目，並顯示繼承和關聯性樹狀結構。 如果先前的定義項目是關聯性目標或繼承關聯性中的子項，該項目會成為預留位置項目；否則該項目不會出現。  
  
### <a name="split-tree"></a>Split Tree  
 您可以中斷 out 繼承或關聯性樹狀結構顯示網域類別定義上按一下滑鼠右鍵，然後按一下**分割樹狀結構**。 定義項目會成為預留位置項目，而定義網域類別現在會與其繼承和關聯性樹狀結構一起顯示在分割區底部。  
  
### <a name="show-as-class"></a>Show As Class  
 如果網域關聯性已衍生關聯性，或如果是內嵌或參考關聯性，與其他網域關聯性，您可以用滑鼠右鍵按一下 關聯性，然後按一下做為類別顯示關聯性**顯示為類別**. 會顯示關聯性**定義域屬性**區間，而且會顯示繼承和關聯性樹狀結構。  
  
## <a name="see-also"></a>另請參閱  
 [特定領域語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



