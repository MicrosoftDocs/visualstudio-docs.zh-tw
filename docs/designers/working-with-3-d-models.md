---
title: "使用 3D 模型 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa035091-1354-4d1c-be44-4fb83860466f
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 372a1efccbfa211167930710418905d95411760c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-3-d-models"></a>使用 3D 模型
您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的模型編輯器建立 3D 模型。 您可以在 DirectX 型遊戲或應用程式中使用這些模型。  
  
## <a name="3-d-models"></a>立體模型  
 3D 模型會定義物件存在於 3D 場景中的圖形。 模型可以是基本的單獨物件、從基本物件階層所構成的複雜物件，或甚至是整個 3D 場景。 3D 物件是由下列項目所組成：3D 空間中的點 (稱為「頂點」)、索引 (其定義三角形、線條或由這些頂點所組成的其他圖形基元)，以及可能針對每個頂點或每個圖形基元所套用的屬性 (例如曲面法線)。 此外，某些資訊可能適用於每個物件；比方說，哪種著色器和紋理會給予物件獨特的外觀。  
  
 若想建立基本 3D 模型，您唯一需要的工具就是模型編輯器，其可提供用於遊戲或應用程式的完整材質屬性、紋理及像素著色器。 或者，您可以先建立預留位置模型以設計原型和進行測試，再請創作者完成模型。  
  
 您也可以使用模型編輯器，檢視已使用完整工具建立的現有 3D 模型，並在觀察到藝術資產問題時加以修改。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[模型編輯器](../designers/model-editor.md)|說明如何使用模型編輯器來處理 3D 模型。|  
|[模型編輯器範例](../designers/model-editor-examples.md)|提供示範如何使用模型編輯器來執行一般 3D 模型工作的主題連結。|