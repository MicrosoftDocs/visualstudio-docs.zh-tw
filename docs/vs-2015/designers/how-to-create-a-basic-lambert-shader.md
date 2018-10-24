---
title: 如何：建立基本 Lambert 著色器 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1f4fbf209e970367ded8e019087287d429bad8fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929721"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>如何：建立基本 Lambert 著色器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件將示範如何使用著色器設計工具和有向圖著色器語言 (DGSL) 來建立光源的著色器，實作傳統的 Lambert 光源模型。  
  
 本文件示範下列活動︰  
  
-   將節點加入著色器圖形  
  
-   中斷和節點的連接  
  
-   連接節點  
  
## <a name="the-lambert-lighting-model"></a>Lambert 光源模型  
 Lambert 光源模型結合環境與定向光源來為 3D 場景中的物件加陰影。 環境元件提供 3D 場景中的基本照明度。 方向元件提供來自定向 (遠處) 光源的額外照明。 環境照明對場景中的所有表面有同樣的影響，不論其方向為何。 對於指定的表面，其是表面的環境色彩和場景中環境光源色彩與濃度的產物。 定向光源對場景中的每個表面會有不同影響，根據相對於光源方向的表面方向而定。 其為表面的擴散色彩和方向以及光源的色彩、濃度和方向的產物。 正對著光源的表面會得到最大比重，而背對光源的表面則不會得到任何比重。 在 Lambert 光源模型下，可結合環境元件和一或多個方向元件，來決定物件上各點的總擴散色彩比重。  
  
 開始之前，請確定已顯示 [屬性] 視窗和 [工具箱]。  
  
#### <a name="to-create-a-lambert-shader"></a>建立 Lambert 著色器  
  
1. 建立要使用的 DGSL 著色器。 如需有關如何將 DGSL 著色器加到專案的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)中的＜使用者入門＞一節。  
  
2. 中斷 [點色彩]節點和 [完稿色彩]節點的連接。 選擇 [點色彩] 節點的 [RGB] 端點，然後選擇 [中斷連結]。 保持連接 [Alpha] 端點。  
  
3. 將 [Lambert] 節點加入圖形。 在 [工具箱] 的 [工用程式] 下，選取 [Lambert]，並將其移至設計介面。 Lambert 節點會根據環境和擴散光源參數，來計算像素的總擴散色彩比重。  
  
4. 將 [點色彩] 節點連接到 [Lambert] 節點。 在 [選取] 模式中，將 [點色彩] 節點的 [RGB] 端點移至 [Lambert] 節點的 [擴散色彩] 端點。 此連接會將像素的插入擴散色彩提供給 Lambert 節點。  
  
5. 將計算後的色彩值連接到完稿色彩。 將 [Lambert] 節點的 [輸出] 端點移至 [完稿色彩] 節點的 [RGB] 端點。  
  
   下圖顯示完成的著色器圖形和套用至茶壺模型的著色器預覽。  
  
> [!NOTE]
>  為了更適當展現此圖中的著色器效果，已使用著色器的 **MaterialDiffuse** 參數來指定橘色。 遊戲或應用程式可以使用這個參數為每個物件提供獨特的色彩值。 如需材質參數的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)中的＜預覽著色器＞一節。  
  
 ![著色器圖形和其效果預覽。](../designers/media/digit-lambert-effect-graph.png "Digit-Lambert-Effect-Graph")  
  
 某些圖形可對一些著色器提供更佳的預覽。 如需如何在著色器設計工具中預覽著色器的詳細資訊，請參閱[著色器設計工具](../designers/shader-designer.md)中的＜預覽著色器＞一節。  
  
 下圖顯示本文件中所述的著色器，套用至 3D 模型。  
  
 ![已套用至模型的 Lambert 光源。](../designers/media/digit-lambert-effect-result.png "Digit-Lambert-Effect-Result")  
  
 如需如何將著色器套用至 3D 模型的詳細資訊，請參閱[如何：將著色器套用至 3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：將著色器套用至 3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [如何：匯出著色器](../designers/how-to-export-a-shader.md)   
 [如何：建立基本 Phong 著色器](../designers/how-to-create-a-basic-phong-shader.md)   
 [著色器設計工具](../designers/shader-designer.md)   
 [著色器設計工具節點](../designers/shader-designer-nodes.md)



