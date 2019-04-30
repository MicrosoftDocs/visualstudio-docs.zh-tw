---
title: HOW TO：切換成員標記法和關聯標記法 （類別設計工具） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c0e691cd162a52dc598f9d3dc4d9a04e0f8f008
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439299"
---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>HOW TO：在成員標記法和關聯標記法之間變更 (類別設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 [類別設計工具] 時，您可以在成員標記法與關聯標記法之間切換，以變更兩種類型在類別圖表中的關聯性代表方式。 將成員顯示為關聯線時，通常可提供類型關聯方式的實用視覺效果。  
  
> [!NOTE]
> 您可以用成員屬性或欄位來代表關聯性。 若要將成員標記法變更為關聯標記法，某種類型必須具有其他類型的成員。 若要將關聯標記法變更為成員標記法，您必須使用關聯線來連接兩種類型。 如需詳細資訊，請參閱[如何：建立類型 （類別設計工具） 之間的關聯](../ide/how-to-create-associations-between-types-class-designer.md)。 如果專案包含多個類別圖表，在您變更某個圖表的關聯性顯示方式時，這些變更只會對該圖表產生影響。 若要變更其他圖表的關聯性顯示方式，請開啟或顯示該圖表，並執行下列步驟。  
  
### <a name="to-change-member-notation-to-association-notation"></a>若要將成員標記法變更為關聯標記法  
  
1. 從方案總管的專案中開啟類別圖表 (.cd) 檔。  
  
2. 在類別圖表的類型圖形中，以滑鼠右鍵按一下代表關聯的成員屬性或欄位，然後選擇 [顯示為關聯]。  
  
    > [!TIP]
    > 如果類型圖形中未顯示任何屬性或欄位，圖形區間可能已摺疊起來。 若要展開類型圖形，請按兩下區間名稱，或以滑鼠右鍵按一下類型圖形，然後選擇 [展開]。  
  
     類型圖形區間的成員隨即消失，並出現連接兩種類型的關聯線。 關聯線會標示屬性或欄位的名稱。  
  
### <a name="to-change-association-notation-to-member-notation"></a>若要將關聯標記法變更為成員標記法  
  
- 在類別圖表中，以滑鼠右鍵按一下關聯線，然後視需要選擇 [顯示為屬性] 或 [顯示為欄位]。  
  
     關聯線隨即消失，而在圖表內該類型圖案的適當區間中會顯示屬性。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立型別 （類別設計工具） 之間的繼承](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [如何：檢視類型 （類別設計工具） 之間的繼承](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [檢視類型和關聯性 (類別設計工具)](../ide/viewing-types-and-relationships-class-designer.md)   
 [如何：將集合關聯視覺化 (類別設計工具)](../ide/how-to-visualize-a-collection-association-class-designer.md)
