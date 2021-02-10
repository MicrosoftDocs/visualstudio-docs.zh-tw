---
title: Domain-Specific 語言工具 UI 總覽
description: 概要說明 Visual Studio 中特定領域語言工具解決方案的使用者介面。
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: fa47b10edc3804468f6ca0766872849ae9e8a949
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959125"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Domain-Specific Language Tools 使用者介面概觀
當您第一次在 Visual Studio 中開啟 Domain-Specific 語言工具 (DSL 工具) 解決方案時，使用者介面會如下圖所示。

 ![dsl 設計工具](../modeling/media/dsl_designer.png)

 下表說明如何使用 UI 的每個組件。

|**Element**|**定義**|
|-|-|
|圖表|圖表顯示領域模型。<br /><br /> 圖表可分成兩側。 一側定義您模型中的項目類型。 另一側定義如何在畫面上顯示您的模型。|
|工具箱|從 [工具箱] 拖曳工具，以將領域類別和圖形類型新增至圖表。 若要新增關聯、連接線和圖形對應，請按一下工具，然後依序按一下圖表上的來源節點和目標節點。|
|DSL 總管|當 DSL 定義是使用中視窗時，[DSL 總管] 會隨即出現。 它會將 DSL 顯示為樹狀。 [DSL 總管] 可讓您編輯圖表上未顯示的模型功能。 例如，您可以使用 [DSL 總管] 來新增 [工具箱] 項目和開啟驗證程序。|
|[DSL 詳細資料] 視窗|[DSL 詳細資料] 視窗會顯示領域模型的項目屬性，可讓您控制如何顯示項目，以及如何複製和刪除項目。<br /><br /> -   根據預設，[DSL 詳細資料] 視窗會出現在 [錯誤清單] 和 [輸出] 視窗旁。|

## <a name="the-domain-model-diagram"></a>領域模型圖表
 領域模型圖表可分成兩個部分。 圖表的一側顯示模型中的項目和關聯。 另一側示範要如何顯示模型，並包含用來顯示模型圖表項目和屬性的圖形。 下圖顯示圖表的項目。

 ![具有泳道的 dsl 設計工具](../modeling/media/dsl_desinger.png)

 下表說明領域模型圖表的一些項目。

|**字詞**|**[定義]**|
|-|-|
|領域類別|領域類別是您模型中的項目類型。<br /><br /> 如果領域類別是多個關聯的目標，則可能在圖表中出現多次。<br /><br /> 若要新增領域類別，請將領域類別工具從 [工具箱] 拖曳到圖表的 [類別和關係] 一側。|
|領域關聯|領域關聯是您模型中項目之間的連結類型。<br /><br /> 「內嵌關係」表示來源項目擁有或包含目標項目，並會顯示為實線。 模型中每個項目都應該是內嵌關係的目標，模型才能形成樹狀。 「參考關聯性」表示模型項目之間的一般連結，並顯示為虛線。 所有項目都可以有任意數目的參考連結。<br /><br /> 若要建立關聯，請在 [工具箱] 中按一下工具，然後依序按一下來源領域類別和目標類別。|
|圖形與連接器|圖形指定模型項目應該如何在 DSL 圖表上顯示。連接線指定 DSL 圖表上可用來顯示關聯的線條。<br /><br /> 若要建立圖形或連接線，請將工具拖曳到圖表的 [圖表項目] 一側。|
|圖形對應|圖形對應會顯示為領域模型圖表中的線條，將圖形連結到其所顯示的領域類別，或將連接線連結到其所顯示的領域關聯。|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools 概觀](../modeling/overview-of-domain-specific-language-tools.md)
- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)
- [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)