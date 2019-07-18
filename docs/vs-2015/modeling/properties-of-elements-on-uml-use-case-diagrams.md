---
title: 使用案例圖中的 UML 項目屬性 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b52afab80bc22c03dc5ff980b937cad53869f5db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444408"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>UML 使用案例圖上的項目屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 UML 使用案例圖中，圖表上的每個項目都會有屬性。 若要查看項目的屬性，以滑鼠右鍵按一下的項目在圖表上或在**UML 模型總管**，然後按一下**屬性**。 屬性會出現在**屬性**視窗。  
  
> [!NOTE]
> 本主題是關於 UML 使用案例圖中的項目屬性。 如需如何讀取 UML 活動圖表的詳細資訊，請參閱[UML 使用案例圖：參考資料](../modeling/uml-use-case-diagrams-reference.md)。 如需如何繪製 UML 活動圖表的詳細資訊，請參閱[UML 使用案例圖：指導方針](../modeling/uml-use-case-diagrams-guidelines.md)。  
  
## <a name="properties-of-elements"></a>項目屬性  
  
|屬性|預設|項目|描述|  
|--------------|-------------|-------------|-----------------|  
|**名稱**|預設名稱|All|識別項目。|  
|**限定的名稱**|封裝::名稱|All|唯一識別該項目。 前面加上含有該項目之套件的合格名稱。|  
|**工作項目**|0 associated|All|與此項目相關聯的工作項目數。 若要關聯工作項目，請參閱[連結模型項目和工作項目](../modeling/link-model-elements-and-work-items.md)。|  
|**描述**|(無)|All|您可以在這裡設定項目的一般注意事項。|  
|**Color**|(預設值)|All|圖案的色彩。 不像其他屬性，這不是圖形顯示的項目屬性。|  
|**影像路徑**|(無)|行動|應該要用來取代預設執行者圖示的影像檔案路徑。 此圖示應為 Visual Studio 專案內的資源檔。|  
|**Subjects**|(無)|使用案例|擁有使用案例的子系統或其他類型。<br /><br /> 將使用案例放置在圖表的子系統上，即可設定它。|  
|**可見度**|Public|使用案例、執行者、子系統|**公用**-全域可見。<br /><br /> **封裝**-在套件內可見。|  
|**IsAbstract**|False|使用案例、執行者、子系統|如果為 true，類型無法具現化，並會被其他定義當做特製化的基底。|  
|**間接具現化**|True|子系統|子系統只以設計成品方式存在。 在執行階段，只有其組件存在。|  
|**超連結**|(無)|成品|成品提供連結之圖表或文件的 URL 或檔案路徑。|  
  
 如需關聯屬性的清單，請參閱 <<c0> [ 屬性的關聯性，在 UML 類別圖](../modeling/properties-of-associations-on-uml-class-diagrams.md)。  
  
## <a name="see-also"></a>另請參閱  
 [UML 使用案例圖表：參考](../modeling/uml-use-case-diagrams-reference.md)   
 [UML 使用案例圖表：方針](../modeling/uml-use-case-diagrams-guidelines.md)
