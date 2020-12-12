---
title: 通訊埠圖案的屬性
description: 深入瞭解埠圖形，以及如何在產生的設計工具中使用埠圖形來代表網域類別。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c51d770392fd219478b3e8f8aa428cdcbab6ef3e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362817"
---
# <a name="properties-of-port-shapes"></a>通訊埠圖案的屬性
您可以使用埠圖形，在產生的設計工具中代表網域類別。

 如需詳細資訊，請參閱 [如何定義 Domain-Specific 語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂和擴充 Domain-Specific 語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 埠圖形具有下表所列的屬性。

|屬性|描述|預設|
|-|-|-|
|填滿色彩|此圖形的填滿色彩。|白色|
|填滿漸層模式|此圖形的填滿漸層模式。|水平|
|幾何|此圖形的幾何 (矩形、圓角矩形、橢圓形或圓形) 。|矩形|
|具有預設連接點|如果為 `True` ，則圖形將在產生的設計工具中使用頂端、底部、左方和右邊的連接點。|否|
|外框色彩|此圖形的外框色彩。|黑色|
|空心虛線樣式|此圖形的外框虛線樣式 (實線、虛線、點、點、DashDotDot 或自訂) 。|實線|
|外框粗細|此圖形的外框粗細。|0.03125|
|文字色彩|與此圖形相關聯的文字裝飾專案所使用的色彩。|黑色|
|存取修飾詞| (或) 類別的存取層級 `public` `internal` 。|公用|
|自訂屬性|用來將屬性新增至由此圖形產生的原始程式碼類別。|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別 (，以支援透過覆寫進行自訂) 。 如需詳細資訊，請參閱覆[寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|否|
|具有自訂的函式|如果為 `True` ，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|否|
|繼承修飾詞|描述從埠 (或) 產生之原始程式碼類別的繼承類型 `none` `abstract` `sealed` 。|無|
|基底埠|此圖形的基類。|(無)|
|名稱|此圖形的名稱。|目前的名稱|
|命名空間|與這個圖形關聯的命名空間。|目前的命名空間|
|工具提示類型|工具提示的定義方式 (固定、變數或無) 。 如果已修正，則 `Fixed Tooltip Text` 會使用屬性的值做為工具提示; 如果是變數，則會在自訂程式碼中定義工具提示。|無|
|附註|與此圖形相關聯的非正式附注。|\<none>|
|初始高度|此圖形的初始高度（以英寸為單位）。|1|
|初始寬度|此形狀的初始寬度（以英寸為單位）。|1.5|
|公開填滿色彩作為屬性<br /><br /> 公開填滿漸層模式<br /><br /> 公開大綱色彩作為屬性<br /><br /> 公開大綱樣式為屬性<br /><br /> 公開框線粗細作為屬性<br /><br /> 公開文字色彩|如果為 `True` ，則使用者可以設定圖形的 [已陳述] 屬性。 若要設定此設定，請以滑鼠右鍵按一下圖形定義，然後按一下 [ **新增公開**]。|否|
|說明|用來記錄產生的設計工具。|\<none>|
|顯示名稱|將在此圖形產生的設計工具中顯示的名稱。|\<none>|
|修正的工具提示文字|用於固定工具提示的文字。|\<none>|
|說明關鍵字|用來為此圖形的 F1 說明編制索引的關鍵字。|\<none>|

## <a name="see-also"></a>請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)