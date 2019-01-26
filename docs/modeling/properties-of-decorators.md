---
title: Decorator 的屬性
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9cc30e43ea10a0b206351df9722d813b565b78a6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942174"
---
# <a name="properties-of-decorators"></a>Decorator 的屬性
裝飾項目是圖示、 文字或圖形或圖表上的連接器上可出現的展開/摺疊形箭號。 下表顯示裝飾項目的三種類型的屬性。 某些屬性會出現只在圖形的裝飾項目或只在接點的裝飾項目。

 如需詳細資訊，請參閱 <<c0> [ 如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。

## <a name="expandcollapse-decorator"></a>展開/摺疊裝飾項目

|屬性|描述|預設|
|-|-|-|
|DisplayName|將會顯示在產生的設計工具的裝飾項目的名稱。|展開摺疊裝飾項目|
|名稱|裝飾項目的名稱。|ExpandCollapseDecorator|
|注意|此裝飾項目相關聯的非正式附註。|\<無>|
|HorizontalOffset|水平位移，相對於裝飾項目，預設位置，以英吋為單位。 （在圖形上只有。）|0|
|VerticalOffset|垂直位移，相對於裝飾項目，預設位置，以英吋為單位。 （在圖形上只有。）|0|
|OffsetFromLine|從相對於其預設位置，以英吋列裝飾項目的位移。 （連接器上只有。）|0|
|OffsetFromShape|從圖形，相對於其預設位置，以英吋為裝飾項目的位移。 （連接器上只有。）|0|
|位置|裝飾項目預設位置。|SourceTop|

## <a name="icon-decorator"></a>圖示裝飾項目

|屬性|描述|預設|
|-|-|-|
|DefaultIcon|要顯示的圖示或影像檔案的路徑。|\<無>|
|DisplayName|要在產生的設計工具中顯示裝飾項目的名稱。|圖示裝飾項目|
|名稱|裝飾項目的名稱。|IconDecorator|
|注意|裝飾項目相關聯的非正式附註。|\<無>|
|HorizontalOffset|水平位移，相對於裝飾項目，預設位置，以英吋為單位。 （在圖形上只有。）|0|
|VerticalOffset|垂直位移，相對於裝飾項目，預設位置，以英吋為單位。 （在圖形上只有。）|0|
|OffsetFromLine|從相對於其預設位置，以英吋列裝飾項目的位移。 （連接器上只有。）|0|
|OffsetFromShape|從圖形，相對於其預設位置，以英吋為裝飾項目的位移。 （連接器上只有。）|0|
|位置|裝飾項目預設位置。|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|屬性|描述|預設|
|-|-|-|
|DefaultText|要顯示的預設文字。|ThisAddIn|
|DisplayName|要在產生的設計工具中顯示裝飾項目的名稱。|ThisAddIn|
|FontSize|裝飾項目中所顯示的文字字型大小。|8|
|FontStyle|裝飾項目中所顯示的文字字型樣式。|Regular|
|名稱|裝飾項目的名稱。|ThisAddIn|
|注意|裝飾項目相關聯的非正式附註。|\<無>|
|HorizontalOffset|水平位移，相對於裝飾項目，預設位置，以英吋為單位。 （在圖形上只有。）|0|
|VerticalOffset|垂直位移，相對於裝飾項目，預設位置，以英吋為單位。 （在圖形上只有。）|0|
|OffsetFromLine|從相對於其預設位置，以英吋列裝飾項目的位移。 （連接器上只有。）|0|
|OffsetFromShape|從圖形，相對於其預設位置，以英吋為裝飾項目的位移。 （連接器上只有。）|0|
|位置|裝飾項目預設位置。|TargetBottom|

## <a name="see-also"></a>另請參閱

- [特定領域語言工具字彙](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)