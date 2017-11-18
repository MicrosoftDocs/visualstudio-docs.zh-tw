---
title: "將延伸加入至 DSL 定義 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f335db9f22392c4d0293a51111efff88c25c3145
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="adding-extensions-to-dsl-definitions"></a>在 DSL 定義中加入擴充功能
DSL 定義延伸模組可讓您建立擴充功能的網域特定定義域語言 (DSL) 來封裝。 DSL 擴充功能，包含在 Visual Studio 整合擴充功能 (VSIX)，可以在使用者的電腦上安裝在 DSL 相同的方式。 額外的功能可以動態啟用和停用在執行階段。 Dsl 不必明確地針對延伸模組，設計和延伸模組可以設計之後，或由協力廠商而不會變更延伸的 DSL。  
  
 其他功能包括：  
  
-   模型和呈現項目的屬性  
  
-   裝飾項目圖形和連接器  
  
-   類別、 關聯性、 圖形和連接器  
  
-   驗證條件約束  
  
-   工具箱項目和索引標籤  
  
 擴充的 DSL 的使用者可以建立及儲存模型，其中包含執行個體的其他功能，和其他已安裝適當的延伸模組的使用者可以讀取這些。 尚未安裝擴充功能的使用者無法使用額外的功能，但也可以更新儲存模型，而不會遺失的其他功能。  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另請參閱  
 [相關部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
