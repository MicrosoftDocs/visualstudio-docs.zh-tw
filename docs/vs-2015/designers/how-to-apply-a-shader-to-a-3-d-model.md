---
title: HOW TO：將著色器套用至 3d 模型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a55c1e71242e59c04066c09efa2375c4bafc485b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156334"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>HOW TO：將著色器套用至 3D 模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本文件將示範如何使用模型編輯器將有向圖形著色器語言 (DGSL) 著色器套用至 3D 模型。  
  
 本文件示範下列活動︰  
  
- 將著色器套用至 3D 模型  
  
## <a name="applying-a-shader-to-a-3-d-model"></a>將著色器套用至 3D 模型  
 您可以將著色器效果套用至 3D 模型，賦予其有趣的外觀。  
  
 開始之前，請確定已顯示 [屬性]  視窗。  
  
#### <a name="to-apply-a-shader-to-a-3-d-model"></a>將著色器套用至 3D 模型  
  
1. 開始使用包含一或多個模型的 3D 場景。 如果您沒有適當的 3d 場景，請在中所述建立一個[How to:建立基本 3d 模型](../designers/how-to-create-a-basic-3-d-model.md)。 您也必須要有可套用至模型的 DGSL 著色器。 如果您沒有適當的著色器，請如下列文章所述建立一個著色器：[如何：建立基本色彩著色器](../designers/how-to-create-a-basic-color-shader.md)，並確定，您已將其儲存至檔案才能繼續。  
  
2. 在 [選取]  模式中，選取您要套用著色器的模型，然後在 [屬性]  視窗中，於 [效果]  屬性群組的 [檔名]  屬性中，指定您想要套用至模型的 DGSL 著色器。  
  
   以下是本身已套用基本色彩效果的模型︰  
  
   ![展示基本色彩效果的 3D 場景](../designers/media/digit-3d-model-effect.png "Digit-3D-Model-Effect")  
  
   在將著色器套用至模型之後，您可以選取該模型，然後在 [屬性]  視窗中，於 [效果]  屬性群組的 [(進階)]  屬性中，選擇省略符號( **...** ) 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立基本 3d 模型](../designers/how-to-create-a-basic-3-d-model.md)   
 [如何：建立基本色彩著色器](../designers/how-to-create-a-basic-color-shader.md)   
 [模型編輯器](../designers/model-editor.md)   
 [著色器設計工具](../designers/shader-designer.md)
