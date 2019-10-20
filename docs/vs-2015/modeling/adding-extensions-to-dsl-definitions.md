---
title: 新增 DSL 定義的擴充功能 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 447001a8aefa22fe15bce9158eddeb0cdb26e4e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654713"
---
# <a name="adding-extensions-to-dsl-definitions"></a>在 DSL 定義中加入擴充功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 定義延伸模組可讓您建立特定領域語言（DSL）的延伸套件。 DSL 延伸模組（包含在 Visual Studio 整合擴充功能（VSIX）中）可以使用與 DSL 相同的方式安裝在使用者的電腦上。 這些額外功能可以在執行時間動態啟用及停用。 Dsl 不一定要針對延伸模組進行明確設計，而且延伸模組可以在稍後或由協力廠商設計，而不需要改變擴充的 DSL。

 其他功能可以包含下列各項：

- Model 和 presentation 元素的屬性

- 圖形和連接器的裝飾專案

- 類別、關聯性、圖形和連接器

- 驗證條件約束

- 工具箱專案和索引標籤

  延伸 DSL 的使用者可以建立和儲存包含額外功能實例的模型，而且這些物件可以由已安裝適當延伸模組的其他使用者讀取。 尚未安裝延伸模組的使用者無法使用其他功能，但可以更新並儲存模型，而不會遺失其他功能。

  如需有關此功能的範例程式碼和詳細資訊，請參閱[Visual Studio 視覺效果和模型化 SDK](http://go.microsoft.com/fwlink/?LinkID=186128)網站。

## <a name="see-also"></a>請參閱
 [Visual Studio 視覺效果和模型 SDK](http://go.microsoft.com/fwlink/?LinkID=186128)
