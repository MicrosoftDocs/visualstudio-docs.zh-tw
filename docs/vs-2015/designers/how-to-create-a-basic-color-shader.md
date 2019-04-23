---
title: HOW TO：建立基本色彩著色器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d6c3410468a53b978165dfcae228b71985fcbe51
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117755"
---
# <a name="how-to-create-a-basic-color-shader"></a>HOW TO：建立基本色彩著色器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件將示範如何使用著色器設計工具和有向圖形著色器語言 (DGSL)，來建立一般色彩著色器。 這個著色器會將完稿色彩設定為 RGB 色彩常數值。  
  
 本文件示範下列活動︰  
  
- 移除圖形中的節點  
  
- 將節點加入圖形  
  
- 設定節點屬性  
  
- 連接節點  
  
## <a name="creating-a-flat-color-shader"></a>建立一般色彩著色器  
 您可以將 RGB 色彩常數的色彩值寫入完稿輸出色彩，來實作一般色彩著色器。  
  
 開始之前，請確定已顯示 [屬性] 視窗和 [工具箱]。  
  
#### <a name="to-create-a-flat-color-shader"></a>建立一般色彩著色器  
  
1. 建立要使用的 DGSL 著色器。 如需有關如何將 DGSL 著色器加到專案的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)中的＜使用者入門＞一節。  
  
2. 刪除 [點色彩] 節點。 使用 [選取] 工具，選取 [點色彩] 節點，然後在功能表列上，選取 [編輯]、[刪除]。  
  
3. 將 [色彩常數] 節點加入圖形。 在 [工具箱] 的 [常數] 下，選取 [色彩常數]，然後將其移至設計介面。  
  
4. 指定 [色彩常數] 節點的色彩值。 使用 [選取] 工具，選取 [色彩常數] 節點，然後在 [屬性] 視窗的 [輸出] 屬性中，指定色彩值。 如需指定橘色，其值為 (1.0, 0.5, 0.2, 1.0)。  
  
5. 將色彩常數連接到完稿色彩。 將 [色彩常數] 節點的 [RGB] 端點移至 [完稿色彩] 節點的 [RGB] 端點，然後將 [色彩常數] 節點的 [Alpha] 端點移至 [完稿色彩] 節點的 [Alpha] 端點，即可建立連接。 這些連接會將完稿色彩設定為上個步驟中所定義的色彩常數。  
  
   下圖顯示完成的著色器圖形和套用至立方體的著色器預覽。  
  
> [!NOTE]
>  在此圖中，指定橘色以更適當展現著色器的效果。  
  
 ![3D 模型上的著色器圖形及其結果](../designers/media/digit-flat-color-effect.png "Digit-Flat-Color-Effect")  
  
 某些圖形可對一些著色器提供更佳的預覽。 如需如何在著色器設計工具中預覽著色器的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：將著色器套用至 3d 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [如何：匯出著色器](../designers/how-to-export-a-shader.md)   
 [著色器設計工具](../designers/shader-designer.md)   
 [著色器設計工具節點](../designers/shader-designer-nodes.md)
