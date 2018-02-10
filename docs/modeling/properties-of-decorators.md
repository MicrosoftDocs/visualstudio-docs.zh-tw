---
title: "裝飾項目屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 95338b26019a2faf2afc2eb6be019ac33d6ece3c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-decorators"></a>Decorator 的屬性
裝飾項目是圖示、 文字或圖形或圖表上的連接器上可出現的展開/摺疊形箭號。 下表顯示裝飾項目的三種類型的屬性。 某些屬性會出現只在圖形裝飾項目或只在連接器裝飾項目。  
  
 如需詳細資訊，請參閱[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)。 如需如何使用這些屬性的詳細資訊，請參閱[自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)。  
  
## <a name="expandcollapse-decorator"></a>展開/摺疊裝飾項目  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|DisplayName|將會顯示在設計工具中產生的裝飾項目的名稱。|展開摺疊裝飾項目|  
|名稱|裝飾項目的名稱。|ExpandCollapseDecorator|  
|注意|此裝飾項目相關聯的非正式附註。|\<none>|  
|HorizontalOffset|預設的相對位置裝飾項目，以英吋水平位移。 （在圖形上只有。）|0|  
|VerticalOffset|預設的相對位置裝飾項目，以英吋之垂直位移。 （在圖形上只有。）|0|  
|OffsetFromLine|從相對於其預設位置，以英吋列裝飾項目的位移。 （連接器上只有。）|0|  
|OffsetFromShape|從圖形，相對於其預設位置，以英吋裝飾項目的位移。 （連接器上只有。）|0|  
|位置|裝飾項目的預設位置。|SourceTop|  
  
## <a name="icon-decorator"></a>圖示裝飾項目  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|DefaultIcon|若要顯示的圖示或影像檔案路徑。|\<none>|  
|DisplayName|要在產生的設計工具中顯示裝飾項目的名稱。|圖示裝飾項目|  
|名稱|裝飾項目的名稱。|IconDecorator|  
|注意|裝飾項目相關聯的非正式附註。|\<none>|  
|HorizontalOffset|預設的相對位置裝飾項目，以英吋水平位移。 （在圖形上只有。）|0|  
|VerticalOffset|預設的相對位置裝飾項目，以英吋之垂直位移。 （在圖形上只有。）|0|  
|OffsetFromLine|從相對於其預設位置，以英吋列裝飾項目的位移。 （連接器上只有。）|0|  
|OffsetFromShape|從圖形，相對於其預設位置，以英吋裝飾項目的位移。 （連接器上只有。）|0|  
|位置|裝飾項目的預設位置。|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|屬性|描述|預設|  
|--------------|-----------------|-------------|  
|DefaultText|要顯示的預設文字。|ThisAddIn|  
|DisplayName|要在產生的設計工具中顯示裝飾項目的名稱。|ThisAddIn|  
|FontSize|裝飾項目中所顯示的文字字型大小。|8|  
|FontStyle|裝飾項目中所顯示的文字字型樣式。|Regular|  
|名稱|裝飾項目的名稱。|ThisAddIn|  
|注意|裝飾項目相關聯的非正式附註。|\<none>|  
|HorizontalOffset|預設的相對位置裝飾項目，以英吋水平位移。 （在圖形上只有。）|0|  
|VerticalOffset|預設的相對位置裝飾項目，以英吋之垂直位移。 （在圖形上只有。）|0|  
|OffsetFromLine|從相對於其預設位置，以英吋列裝飾項目的位移。 （連接器上只有。）|0|  
|OffsetFromShape|從圖形，相對於其預設位置，以英吋裝飾項目的位移。 （連接器上只有。）|0|  
|位置|裝飾項目的預設位置。|TargetBottom|  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)