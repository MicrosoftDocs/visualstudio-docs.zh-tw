---
title: 使用 DSL 定義圖 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 14e365d6bbe99634135bfad133d840b98e22e3b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663043"
---
# <a name="working-with-the-dsl-definition-diagram"></a>使用 DSL 定義圖表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 定義的圖表是定義網域特定語言的重要工具。 您可以將項目加入至網域模型，並定義圖表上的關聯性；也可以修改圖表配置，讓圖表更容易讀取。

## <a name="the-layout-of-the-diagram"></a>圖表配置
 @No__t_0 定義圖表有兩個分割區： [**類別] 和 [關聯**性] 分割區，以及 [**圖表元素**]。 [**類別和關聯**性] 分割區會顯示網域類別、網域關聯性和繼承。 [**圖表**專案] 分割區會顯示圖形類別、連接器類別、泳道類別，以及產生的設計工具圖表。

 網域類別可以出現在 [**類別] 和 [關聯**性] 分割區中的多個位置。 如果網域類別不是其他網域類別的基底類別，網域類別定義會顯示繼承樹狀結構；如果網域類別是內嵌關聯性或參考關聯性的來源，網域類別定義會顯示關聯性樹狀結構。 網域類別預留位置會顯示為內嵌關聯性或參考關聯性的目標。 根據預設，會顯示預留位置專案，並折迭 [**定義域屬性**] 區間。 這些項目不會顯示繼承，也不會顯示內嵌關聯性或參考關聯性。

 當您加入網域類別時，它會出現在 [**類別和關聯**性] 分割區的下半部。 當您加入內嵌關聯性或參考關聯性時，會在來源網域類別右下方繪製此關聯性。

 當您加入網域類別和關聯性時，會變得很難尋找特定網域類別。 您可以在 [ **DSL Explorer** ] 中以滑鼠右鍵按一下網域類別，然後按一下 [**在圖表中尋找**] 來尋找它。

 下列各節說明如何變更圖表的外觀，讓圖表更容易讀取。

## <a name="copying-elements"></a>複製項目
 您可以在 DSL 定義圖表中，複製、剪下及貼上項目。

## <a name="zooming-in-or-out-on-the-diagram"></a>放大或縮小圖表
 您可以使用 [ **DSL 設計工具**] 工具列來設定縮放層級，以放大或縮小圖表。

## <a name="hiding-map-lines"></a>隱藏對應線
 對應線是在網域類別或網域關聯性與其所對應的圖形或連接線之間繪製的線條。 按一下 [ **DSL 設計工具**] 工具列上的 [**顯示地圖線條**] 按鈕，即可隱藏地圖線條。 若要顯示線條，請再按一次按鈕。

## <a name="changing-the-diagram-layout"></a>變更圖表配置
 您可以如下所示變更 [**類別和關聯**性] 分割區的配置。

### <a name="expandcollapse"></a>展開/摺疊
 您可以用滑鼠右鍵按一下代表網域類別或圖形的區間圖形元素，然後按一下 [折迭]，來減少其**大小。** 這會隱藏圖形的 [**網域屬性**] 區間。 若要再次顯示 [**定義域屬性**] 區間，請以滑鼠右鍵按一下圖形，然後按一下 [**展開**]。

### <a name="move-updown"></a>上移/下移
 以滑鼠右鍵按一下資料分割中的網域類別或圖表元素，然後按一下 [**上移**] 或 **[下移]** ，即可將它上移或下移。 如果您移動顯示為內嵌關聯性或參考關聯性目標的預留位置項目，關聯性會隨之移動。

### <a name="expandcollapse-relationships-tree"></a>展開/摺疊關聯性樹狀結構
 如果網域類別在內嵌或參考與其他網域類別的關聯性中扮演來源角色，您可以用滑鼠右鍵按一下網域類別定義，然後按一下 [折迭**關聯性樹狀結構**]，以隱藏關聯性。 若要顯示關聯性，請以滑鼠右鍵按一下定義元素，然後按一下 [**展開關聯性樹狀結構**]。

### <a name="expandcollapse-inheritance-tree"></a>展開/摺疊繼承樹狀結構
 如果網域類別是其他網域類別的基類，您可以用滑鼠右鍵按一下網域類別定義，然後按一下 [折迭**繼承樹狀結構**]，以隱藏繼承樹狀結構。 若要顯示繼承樹狀結構，請以滑鼠右鍵按一下定義元素，然後按一下 [**展開繼承樹狀結構**]。

### <a name="bring-tree-here"></a>Bring Tree Here
 您可以用滑鼠右鍵按一下預留位置網域類別，然後按一下 [將**樹狀結構放在這裡**]，來合併圖表。 預留位置網域類別會成為定義項目，並顯示繼承和關聯性樹狀結構。 如果先前的定義項目是關聯性目標或繼承關聯性中的子項，該項目會成為預留位置項目；否則該項目不會出現。

### <a name="split-tree"></a>分割樹狀結構
 您可以用滑鼠右鍵按一下顯示 [繼承] 或 [關聯性] 樹狀目錄的網域類別定義，然後按一下 [**分割樹狀結構**]，來將其中斷。 定義項目會成為預留位置項目，而定義網域類別現在會與其繼承和關聯性樹狀結構一起顯示在分割區底部。

### <a name="show-as-class"></a>Show As Class
 如果網域關聯性具有衍生關聯性，或者它與其他網域關聯性有內嵌或參考關聯性，您可以在關聯性上按一下滑鼠右鍵，然後按一下 [**顯示為類別**]，將關聯性顯示為類別。 關聯性會以 [**定義域屬性**] 區間顯示，並顯示 [繼承] 和 [關聯性] 樹狀結構。

## <a name="see-also"></a>請參閱
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
