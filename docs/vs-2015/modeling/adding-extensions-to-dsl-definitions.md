---
title: 將延伸模組新增至 DSL 定義 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fab56a7738ed7b52760cf20a5bfcc8542ee5a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919064"
---
# <a name="adding-extensions-to-dsl-definitions"></a>在 DSL 定義中加入擴充功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 定義延伸模組可讓您建立延伸模組套件，以 (DSL) 的特定領域語言。 DSL 延伸模組（包含在 Visual Studio 整合延伸模組 (VSIX) 中）可以用與 DSL 相同的方式安裝在使用者的電腦上。 您可以在執行時間動態啟用和停用額外的功能。 Dsl 不需要針對擴充功能明確設計，而且擴充功能可以在稍後或由協力廠商設計，而不需要改變擴充的 DSL。

 其他功能可以包含下列各項：

- Model 和 presentation 元素的屬性

- 圖形和連接器的裝飾專案

- 類別、關聯性、圖形和連接器

- 驗證條件約束

- 工具箱專案和索引標籤

  擴充 DSL 的使用者可以建立和儲存包含其他功能實例的模型，而且其他已安裝適當副檔名的使用者可以讀取這些模型。 未安裝此擴充功能的使用者無法使用額外的功能，但可以更新和儲存模型，而不會遺失額外的功能。

  如需這項功能的範例程式碼和詳細資訊，請參閱 [Visual Studio 視覺效果和模型 SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148) 網站。

## <a name="see-also"></a>另請參閱
 [Visual Studio Visualization and Modeling SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148)
