---
title: UML 使用案例圖上元素的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671407"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>UML 使用案例圖上的項目屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 使用案例圖中，圖表上的每個項目都會有屬性。 若要查看元素的屬性，請以滑鼠右鍵按一下圖表上的專案或 [ **UML 模型瀏覽器**]，然後按一下 [**屬性**]。 屬性會出現在 [**屬性**] 視窗中。

> [!NOTE]
> 本主題是關於 UML 使用案例圖中的項目屬性。 如需如何讀取 UML 活動圖的詳細資訊，請參閱[Uml 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md)。 如需如何繪製 UML 活動圖的詳細資訊，請參閱[Uml 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)。

## <a name="properties-of-elements"></a>項目屬性

|屬性|Default|項目|描述|
|--------------|-------------|-------------|-----------------|
|**名稱**|預設名稱|All|識別項目。|
|**限定名稱**|套件 :: 名稱|All|唯一識別該項目。 前面加上含有該項目之套件的合格名稱。|
|**工作專案**|0 associated|All|與此項目相關聯的工作項目數。 若要建立工作專案的關聯，請參閱[連結模型元素和工作專案](../modeling/link-model-elements-and-work-items.md)。|
|**說明**|(無)|All|您可以在這裡設定項目的一般注意事項。|
|**顏色**|(預設值)|All|圖案的色彩。 不像其他屬性，這不是圖形顯示的項目屬性。|
|**影像路徑**|(無)|行動|應該要用來取代預設執行者圖示的影像檔案路徑。 此圖示應為 Visual Studio 專案內的資源檔。|
|**接受**|(無)|使用案例|擁有使用案例的子系統或其他類型。<br /><br /> 將使用案例放置在圖表的子系統上，即可設定它。|
|**可見度**|Public|使用案例、執行者、子系統|**Public** -全域可見。<br /><br /> **Package** -在套件內可見。|
|**IsAbstract**|False|使用案例、執行者、子系統|如果為 true，類型無法具現化，並會被其他定義當做特製化的基底。|
|**已間接具現化**|True|子系統|子系統只以設計成品方式存在。 在執行階段，只有其組件存在。|
|**超連結**|(無)|成品|成品提供連結之圖表或文件的 URL 或檔案路徑。|

 如需關聯屬性的清單，請參閱[UML 類別圖上的關聯屬性](../modeling/properties-of-associations-on-uml-class-diagrams.md)。

## <a name="see-also"></a>請參閱
 [Uml 使用案例圖：參考](../modeling/uml-use-case-diagrams-reference.md) [Uml 使用案例圖：方針](../modeling/uml-use-case-diagrams-guidelines.md)
