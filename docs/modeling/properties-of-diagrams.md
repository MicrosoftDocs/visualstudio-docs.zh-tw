---
title: 圖表的屬性
description: 瞭解圖表以及如何設定屬性，以指定在產生的設計工具中會顯示圖表的方式。
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 943b634114c28f6f914926c74861a902c663523e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956161"
---
# <a name="properties-of-diagrams"></a>圖表的屬性
您可以設定屬性，以指定要在產生的設計工具中顯示圖表的方式。 例如，您可以在圖表中指定文字的預設色彩。

 如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

 下表列出圖表的屬性。

|屬性|描述|預設|
|-|-|-|
|填滿色彩|圖表的填滿色彩。|白色|
|文字色彩|顯示在圖表上的文字色彩。|黑色|
|存取修飾詞|類別的存取修飾詞 (公用或內部) 。|公用|
|自訂屬性|用來將屬性新增至產生的程式碼類別。|\<none>|
|產生雙重衍生|如果為 `True` ，則會產生基類和部分類別 (，以支援透過覆寫進行自訂) 。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|否|
|具有自訂的函式|如果為 `True` ，則會在原始程式碼中提供自訂的函式。 如需詳細資訊，請參閱覆 [寫和擴充產生的類別](../modeling/overriding-and-extending-the-generated-classes.md)。|否|
|繼承修飾詞|描述從圖表產生之原始程式碼類別的繼承類型 (`none` 、 `abstract` 或 `sealed`) 。|無|
|基底圖表|此圖表的基底類別。|(無)|
|名稱|此圖表的名稱。|目前的名稱|
|命名空間|與此圖表關聯的命名空間。|目前的命名空間|
|表示的類別|此圖表所代表的根域類別。|目前的根類別（如果適用）|
|備註|與此元素相關聯的非正式附注。|\<none>|
|將填滿色彩公開為屬性|如果為 `True` ，則使用者可以設定產生之設計工具的圖表填滿色彩。 若要設定此屬性，請以滑鼠右鍵按一下 [圖表] 圖形，然後按一下 [ **新增公開**]。|否|
|將文字色彩公開為屬性|如果為 `True` ，則使用者可以在產生的設計工具中設定圖表的文字色彩。 若要設定此屬性，請以滑鼠右鍵按一下 [圖表] 圖形，然後按一下 [ **新增公開**]。|否|
|Description|用來記錄所產生之設計工具的描述。|\<none>|
|顯示名稱|將在此圖表產生的設計工具中顯示的名稱。|\<none>|
|說明關鍵字|用來為此圖表的 F1 說明編制索引的關鍵字。|\<none>|

## <a name="see-also"></a>另請參閱

[特定領域語言工具詞彙](/previous-versions/bb126564(v=vs.100))