---
title: 使用 DSL 定義圖表
description: 瞭解 DSL 工具定義的圖表是定義網域特定語言的重要工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f401fe0509fc425fff873a7dc224c69359156861
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388070"
---
# <a name="working-with-the-dsl-definition-diagram"></a>使用 DSL 定義圖表
定義的圖表 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 是定義網域特定語言的重要工具。 您可以將項目加入至網域模型，並定義圖表上的關聯性；也可以修改圖表配置，讓圖表更容易讀取。

## <a name="the-layout-of-the-diagram"></a>圖表配置
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]定義圖表有兩個數據分割：**類別和關聯** 性分割，以及 **圖表元素** 分割。 **類別和關聯** 性分割區會顯示網域類別、網域關聯性，以及繼承。 [ **圖表元素** ] 分割區會顯示圖形類別、連接器類別、泳道類別，以及產生的設計工具圖表。

 網域類別可以出現在 **類別和關聯** 性分割區的多個位置中。 如果網域類別不是其他網域類別的基底類別，網域類別定義會顯示繼承樹狀結構；如果網域類別是內嵌關聯性或參考關聯性的來源，網域類別定義會顯示關聯性樹狀結構。 網域類別預留位置會顯示為內嵌關聯性或參考關聯性的目標。 依預設，會顯示 [ **網域屬性** ] 區間折迭的預留位置元素。 這些項目不會顯示繼承，也不會顯示內嵌關聯性或參考關聯性。

 當您加入網域類別時，它會出現在 **類別和關聯** 性分割區的下半部。 當您加入內嵌關聯性或參考關聯性時，會在來源網域類別右下方繪製此關聯性。

 當您加入網域類別和關聯性時，會變得很難尋找特定網域類別。 在 [ **DSL Explorer** ] 中以滑鼠右鍵按一下網域類別，然後按一下 [ **在圖表中找** 出]，即可找到網域類別。

 下列各節說明如何變更圖表的外觀，讓圖表更容易讀取。

## <a name="copying-elements"></a>複製項目
 您可以在 DSL 定義圖表中，複製、剪下及貼上項目。

## <a name="zooming-in-or-out-on-the-diagram"></a>放大或縮小圖表
 您可以使用 [ **DSL 設計工具** ] 工具列來設定縮放層級，以放大或縮小圖表。

## <a name="hiding-map-lines"></a>隱藏對應線
 對應線是在網域類別或網域關聯性與其所對應的圖形或連接線之間繪製的線條。 您可以按一下 [ **DSL 設計工具**] 工具列上的 [**顯示地圖線條**] 按鈕來隱藏地圖行。 若要顯示線條，請再按一次按鈕。

## <a name="changing-the-diagram-layout"></a>變更圖表配置
 您可以變更 **類別和關聯** 性分割區的配置，如下所示。

### <a name="expandcollapse"></a>展開/摺疊
 您可以用滑鼠右鍵按一下，然後按一下 [折迭]，以縮減代表網域類別或圖形的區間圖形元素的 **大小。** 這會隱藏圖形的 [ **網域屬性** ] 區間。 若要再次顯示 [ **網域屬性** ] 區間，請以滑鼠右鍵按一下圖形，然後按一下 [ **展開**]。

### <a name="move-updown"></a>上移/下移
 您可以用滑鼠右鍵按一下專案，然後按一下 [ **上移** ] 或 [ **下移**]，在分割區中向上或向下移動網域類別或圖表元素。 如果您移動顯示為內嵌關聯性或參考關聯性目標的預留位置項目，關聯性會隨之移動。

### <a name="expandcollapse-relationships-tree"></a>展開/摺疊關聯性樹狀結構
 如果網域類別在內嵌或參考與其他網域類別的關聯性中扮演來源角色，您可以用滑鼠右鍵按一下網域類別定義，然後按一下 [折迭 **關聯性樹狀結構**]，來隱藏關聯性。 若要顯示關聯性，請以滑鼠右鍵按一下 [定義] 元素，然後按一下 [ **展開關聯性樹狀結構**]。

### <a name="expandcollapse-inheritance-tree"></a>展開/摺疊繼承樹狀結構
 如果網域類別是其他網域類別的基類，您可以用滑鼠右鍵按一下網域類別定義，然後按一下 [折迭 **繼承樹狀結構**]，以隱藏繼承樹狀結構。 若要顯示繼承樹狀結構，請以滑鼠右鍵按一下 [定義] 元素，然後按一下 [ **展開繼承樹狀結構**]。

### <a name="bring-tree-here"></a>Bring Tree Here
 您可以用滑鼠右鍵按一下預留位置網域類別，然後按一下 [將 **樹狀結構移到這裡**]，來合併圖表。 預留位置網域類別會成為定義項目，並顯示繼承和關聯性樹狀結構。 如果先前的定義項目是關聯性目標或繼承關聯性中的子項，該項目會成為預留位置項目；否則該項目不會出現。

### <a name="split-tree"></a>分割樹狀結構
 您可以用滑鼠右鍵按一下顯示繼承或關聯性樹狀結構的網域類別定義，然後按一下 [ **分割樹狀結構**]。 定義項目會成為預留位置項目，而定義網域類別現在會與其繼承和關聯性樹狀結構一起顯示在分割區底部。

### <a name="show-as-class"></a>Show As Class
 如果網域關聯性具有衍生的關聯性，或它具有與其他網域關聯性的內嵌或參考關聯性，您可以用滑鼠右鍵按一下關聯性，然後按一下 [ **顯示為類別**]，將關聯性顯示為類別。 關聯性會以 **定義域屬性** 區間顯示，並且會顯示繼承和關聯性樹狀結構。

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)