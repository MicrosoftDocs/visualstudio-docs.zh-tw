---
title: Decorator 的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14965f829530ba5a2f6a7797291e9d1cfab0ae2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810050"
---
# <a name="properties-of-decorators"></a>Decorator 的屬性
裝飾專案是圖示、文字或展開/折迭的燕，可出現在圖表上的圖形或接點上。 下表顯示三種裝飾專案的屬性。 某些屬性只會出現在 [圖形] 裝飾專案上，或只出現在 [連接器裝飾專案] 上。

 如需詳細資訊，請參閱 [如何定義網域指定的語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需有關如何使用這些屬性的詳細資訊，請參閱 [自訂和擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

## <a name="expandcollapse-decorator"></a>展開/折迭裝飾專案

|屬性|描述|預設|
|-|-|-|
|DisplayName|將在產生的設計工具中顯示的裝飾專案名稱。|展開折迭裝飾專案|
|[屬性]|裝飾專案的名稱。|ExpandCollapseDecorator|
|備註|與此裝飾專案相關聯的非正式附注。|\<none>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案預設位置的水準位移（以英寸為單位）。 僅針對圖形 (。 ) |0|
|System.windows.controls.primitives.popup.verticaloffset|相對於裝飾專案預設位置的垂直位移（以英寸為單位）。 僅針對圖形 (。 ) |0|
|OffsetFromLine|來自線條的裝飾專案相對於其預設位置（以英寸為單位）的位移。 僅 (連接器。 ) |0|
|OffsetFromShape|圖形中的裝飾專案相對於其預設位置（以英寸為單位）的位移。 僅 (連接器。 ) |0|
|位置|裝飾專案的預設位置。|SourceTop|

## <a name="icon-decorator"></a>圖示裝飾專案

|屬性|描述|預設|
|-|-|-|
|DefaultIcon|要顯示之圖示或影像檔案的路徑。|\<none>|
|DisplayName|要在產生的設計工具中顯示的裝飾專案名稱。|圖示裝飾專案|
|[屬性]|裝飾專案的名稱。|IconDecorator|
|備註|與裝飾專案相關聯的非正式附注。|\<none>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案預設位置的水準位移（以英寸為單位）。 僅針對圖形 (。 ) |0|
|System.windows.controls.primitives.popup.verticaloffset|相對於裝飾專案預設位置的垂直位移（以英寸為單位）。 僅針對圖形 (。 ) |0|
|OffsetFromLine|來自線條的裝飾專案相對於其預設位置（以英寸為單位）的位移。 僅 (連接器。 ) |0|
|OffsetFromShape|圖形中的裝飾專案相對於其預設位置（以英寸為單位）的位移。 僅 (連接器。 ) |0|
|位置|裝飾專案的預設位置。|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|屬性|描述|預設|
|-|-|-|
|DefaultText|要顯示的預設文字。|標籤|
|DisplayName|要在產生的設計工具中顯示的裝飾專案名稱。|標籤|
|FontSize|裝飾專案中顯示之文字的字型大小。|8|
|FontStyle|裝飾專案中顯示之文字的字型樣式。|定期|
|[屬性]|裝飾專案的名稱。|標籤|
|備註|與裝飾專案相關聯的非正式附注。|\<none>|
|System.windows.controls.primitives.popup.horizontaloffset|相對於裝飾專案預設位置的水準位移（以英寸為單位）。 僅針對圖形 (。 ) |0|
|System.windows.controls.primitives.popup.verticaloffset|相對於裝飾專案預設位置的垂直位移（以英寸為單位）。 僅針對圖形 (。 ) |0|
|OffsetFromLine|來自線條的裝飾專案相對於其預設位置（以英寸為單位）的位移。 僅 (連接器。 ) |0|
|OffsetFromShape|圖形中的裝飾專案相對於其預設位置（以英寸為單位）的位移。 僅 (連接器。 ) |0|
|位置|裝飾專案的預設位置。|TargetBottom|

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)