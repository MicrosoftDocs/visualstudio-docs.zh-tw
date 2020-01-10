---
title: 圖表的屬性
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 762c2acb6774d7eb4949087fdd91e85c86acd6bb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595419"
---
# <a name="properties-of-diagrams"></a>圖表的屬性
您可以設定屬性，以指定圖表會在產生的設計工具中出現的方式。 例如，您可以在圖表中指定文字的預設色彩。

 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 下表列出圖表的屬性。

|屬性|描述|預設值|
|-|-|-|
|填滿色彩|圖表的填滿色彩。|白色|
|文字色彩|圖表上顯示的文字色彩。|0：黑色|
|存取修飾詞|類別的存取修飾詞（公用或內部）。|公用|
|自訂屬性|用來將屬性新增至產生的程式碼類別。|\<無>|
|產生雙重衍生|如果 `True`，則會產生基類和部分類別（以支援透過覆寫的自訂）。 如需詳細資訊，請參閱覆[寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|有自訂的函數|如果 `True`，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆[寫及擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|False|
|繼承修飾詞|描述從圖表產生之原始程式碼類別的繼承類型（`none`、`abstract`或 `sealed`）。|None|
|基底圖表|此圖表的基類。|(無)|
|Name|此圖表的名稱。|目前名稱|
|命名空間|與此圖表關聯的命名空間。|目前的命名空間|
|類別表示|此圖表所代表的根域類別。|目前的根類別（如果適用）|
|注意事項|與此元素相關聯的非正式附注。|\<無>|
|將填滿色彩公開為屬性|如果 `True`，使用者可以設定所產生之設計工具圖表的填滿色彩。 若要設定此屬性，請以滑鼠右鍵按一下圖表圖形，然後按一下 [新增] [**公開**]。|False|
|將文字色彩公開為屬性|如果 `True`，則使用者可以在產生的設計工具中設定圖表的文字色彩。 若要設定此屬性，請以滑鼠右鍵按一下圖表圖形，然後按一下 [新增] [**公開**]。|False|
|描述|用來記錄產生的設計工具的描述。|\<無>|
|顯示名稱|將在此圖表產生的設計工具中顯示的名稱。|\<無>|
|說明關鍵字|用來為此圖表的 F1 說明編制索引的關鍵字。|\<無>|

## <a name="see-also"></a>請參閱

[特定領域語言工具詞彙](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
