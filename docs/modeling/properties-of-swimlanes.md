---
title: 泳道的屬性
description: 瞭解泳道如何將圖表分成垂直或水準區域，以及如何定義要在泳道內顯示的其他圖形。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61994a25b5fa862a2014e2dd5b57a0c47130e6ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882982"
---
# <a name="properties-of-swimlanes"></a>泳道的屬性
您可以將泳道新增至圖表。 泳道會將圖表分成垂直或水準區域。 您可以定義要在泳道內顯示的其他圖形。 如需詳細資訊，請參閱 [如何定義 Domain-Specific 語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂和擴充 Domain-Specific 語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 泳道具有下表中列出的屬性。

|屬性|描述|預設|
|-|-|-|
|主體填滿色彩|泳道主體的填滿色彩。|白色|
|頁首填滿色彩|泳道標頭的填滿色彩。|8：深灰色|
|分隔符號色彩|分隔線的色彩。|LightGray|
|分隔線樣式|分隔線的樣式 (、、 `Solid` `Dash` `Dot` 、 `DashDot` 、 `DashDotDot` 或 `Custom`) 。|`Dash`|
|分隔符號粗細|分隔線的寬度（以英寸為單位）。|0.03125|
|文字色彩|與此泳道相關聯的文字裝飾專案所使用的色彩。|黑色|
|存取修飾詞| (或) 類別的存取層級 `public` `internal` 。|公用|
|自訂屬性|用來將屬性新增至由此泳道產生的程式碼類別。|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別 (，以支援透過覆寫進行自訂) 。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|否|
|具有自訂的函式|如果為 `True` ，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|否|
|繼承修飾詞|描述從泳道 (或) 產生之原始程式碼類別的繼承類型 `none` `abstract` `sealed` 。|無|
|基底泳道|此泳道的基底類別。|(無)|
|名稱|此泳道的名稱。|目前的名稱|
|命名空間|與此泳道關聯的命名空間。|目前的命名空間|
|工具提示類型|工具提示的定義方式 (`fixed` 、 `variable` 或 `none`) 。 如果為 `fixed` ，則 `Fixed Tooltip Text` 會使用屬性的值; 如果為 `variable` ，則會在自訂程式碼中定義工具提示。|\<none>|
|備註|與此泳道相關聯的非正式附注。|\<none>|
|對齊|水準或垂直對齊。|Vertical|
|初始高度|此泳道的初始高度（以英寸為單位）。 僅適用于水準泳道。|0|
|初始寬度|此泳道的初始寬度（以英寸為單位）。 僅適用于垂直泳道。|0|
|公開文字色彩|如果為 `True` ，則使用者可以在產生的設計工具中設定泳道的色彩。 若要設定此設定，請以滑鼠右鍵按一下 [泳道] 圖形，然後按一下 [ **新增公開**]。|否|
|Description|用來記錄產生的設計工具。|\<none>|
|顯示名稱|將在產生的設計工具中顯示的名稱，以參考這個泳道類別。|\<none>|
|修正工具提示文字|用於固定工具提示的文字。|\<none>|
|說明關鍵字|用來為此泳道的 F1 說明編制索引的關鍵字。|\<none>|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)