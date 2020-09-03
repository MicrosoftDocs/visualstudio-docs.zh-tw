---
title: 如何：建立基本 3D 模型 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b4db5b54f39a0be6de184b609e672b1f0173890
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664600"
---
# <a name="how-to-create-a-basic-3-d-model"></a>如何：建立基本 3D 模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件將示範如何使用模型編輯器來建立基本 3D 模型。

 本文件示範下列活動︰

- 將物件加入場景

- 選取表面和邊緣

- 轉譯選取項目

- 使用 [細分表面]**** 和 [使表面立體化]**** 工具

- 使用 [分成三角形]**** 命令

## <a name="creating-a-basic-3-d-model"></a>建立基本 3D 模型
 您可以使用模型編輯器來建立和修改遊戲或應用程式的 3D 模型和場景。 下列步驟示範如何使用模型編輯器來建立房屋的簡化 3D 模型。 簡化模型可當做仍在建立的最終藝術資產替身、當做網格用於衝突偵測，或當做低解析度模型，在所代表物件還不能受益於更高解析度的轉譯時使用。

 當您完成時，結果應該像這樣：

 ![精簡化房屋完成後的模型](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")

 開始之前，請確定已顯示 [屬性]**** 視窗和 [工具箱]****。

#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>建立簡化房屋的 3D 模型

1. 建立要使用 3D 模型。 如需有關如何將模型加到專案的詳細資訊，請參閱[模型編輯器](../designers/model-editor.md)中的＜使用者入門＞一節。

2. 將立方體加入場景。 在 [工具箱]**** 視窗的 [圖形]**** 下，選取 [立方體]****，然後將其移至設計介面。

3. 切換至表面選取模式。 在 [模型編輯器] 工具列上，選擇 [選取表面]****。

4. 細分立方體頂端。 在表面選取模式中，選擇立方體一次，啟動選擇功能，然後選擇立方體頂端以選取最上層表面。 在 [模型編輯器] 工具列上，選擇 [細分表面]****。 這樣會在立方體頂端加入新的頂點，分割成大小均一的四個部分。

    ![細分立方體的頂端](../designers/media/gfx-model-demo-house-subdiv.png "gfx_model_demo_house_subdiv")

5. 使立方體的兩個相鄰面立體化，例如立方體的前面與右邊。 在表面選取模式中，選擇立方體一次，啟動選擇功能，然後選擇立方體的某一面。 按住 Control 鍵，在立方體選擇和您最先選取的面相鄰的另一面，然後在 [模型編輯器] 工具列上，選擇 [使表面立體化]****。

    ![將立方體的側邊立體化](../designers/media/gfx-model-demo-house-extrude.png "gfx_model_demo_house_extrude")

6. 擴充立體化的其中一面。 選擇剛才已立體化的其中一面，然後在 [模型編輯器] 工具列上，選擇 [平移]**** 工具，並向相同的立體化方向移動平移操作工具。

    ![進一步將立方體的其中一邊立體化。](../designers/media/gfx-model-demo-house-extend.png "gfx_model_demo_house_extend")

7. 將模型分成三角形。 在 [模型編輯器] 工具列上，選擇 [進階]****、[工具]****、[分成三角形]****。

8. 建立房屋的屋頂。 在 [模型編輯器] 工具列上，選擇 [選取邊緣]****，然後選取立方體來加以啟動，切換至邊緣選取模式。 按住 Control 鍵，並選取如下所示的邊緣︰

    ![即將成為屋頂頂端的邊緣](../designers/media/gfx-model-demo-house-edges.png "gfx_model_demo_house_edges")

    選取邊緣後，在 [模型編輯器] 工具列上，選擇 [平移]**** 工具，然後向上移動平移操作工具來建立屋脊。

   完成簡化的房屋模型。 以下顯示套用平面網底的最終模型︰

   ![精簡化房屋完成後的模型](../designers/media/gfx-model-demo-house-final.png "gfx_model_demo_house_final")

   下一步可以將著色器套用至這個 3D 模型。 如需詳細資訊，請參閱 [如何：將著色器套用至3D 模型](../designers/how-to-apply-a-shader-to-a-3-d-model.md)。

## <a name="see-also"></a>另請參閱
 [如何：模型立體地形](../designers/how-to-model-3-d-terrain.md)[模型編輯器](../designers/model-editor.md)[著色器設計](../designers/shader-designer.md)工具
