---
title: HOW TO：修改 3d 模型的樞紐分析點 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a89e06fad1e47e3c2fd7be565acab9d94e3f29d5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434436"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>HOW TO：修改 3d 模型的樞紐點
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件將示範如何使用模型編輯器來修改 3D 模型的「樞紐分析點」。 樞紐分析點是空間中的點，定義物件在旋轉和縮放時的數學中心。  
  
 本文件示範下列活動︰  
  
- 修改物件的樞紐分析點  
  
## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>修改 3D 模型的樞紐分析點  
 您可以修改 3D 模型的樞紐分析點，以重新定義其原點。  
  
 請確定已顯示 [屬性] 視窗和 [工具箱]。  
  
#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>修改 3D 模型的樞紐分析點  
  
1. 開始使用的現有 3d 模型，例如中所述[How to:建立基本 3d 模型](../designers/how-to-create-a-basic-3-d-model.md)。  
  
2. 進入樞紐分析模式。 在 [模型編輯器模式] 工具列上，選擇 [樞紐分析表模式] 按鈕以啟動樞紐分析表模式。 出現在 [樞紐分析表模式] 按鈕附近的方塊，指出 [模型編輯器] 現在處於樞紐分析表模式。 在樞紐分析表模式中，像是平移的作業會影響物件的樞紐分析點，而不是世界空間中的物件結構。  
  
3. 修改物件的樞紐分析點。 在 [選取] 模式中，選取該物件，然後在 [模型檢視器] 工具列上，選擇 [平移] 工具。 設計介面上隨即出現代表樞紐分析點的方塊。 移動該方塊以修改物件的樞紐分析點。  
  
    您可以透過移動方塊，在 3D 空間中移動樞紐分析點。 若要沿著某一座標軸平移樞紐分析點，請移動對應至該軸的箭頭。 方塊和箭頭會變成黃色，指出受到平移影響的座標軸。  
  
    您也可以使用 [屬性] 視窗中的 [ 在空間中移動樞紐位置] 屬性，來指定樞紐分析點。  
  
   > [!TIP]
   > 您可以旋轉物件來檢視新樞紐分析點的效果。 若要加以旋轉，請使用 [旋轉] 工具或修改 [旋轉] 屬性。  
  
   以下模型具有已修改的樞紐點：  
  
   ![具有已修改樞紐點的房屋模型](../designers/media/digit-modified-model.png "Digit-Modified-Model")  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立基本 3d 模型](../designers/how-to-create-a-basic-3-d-model.md)   
 [模型編輯器](../designers/model-editor.md)
