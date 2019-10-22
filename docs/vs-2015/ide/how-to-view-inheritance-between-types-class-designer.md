---
title: 如何：檢視類型之間的繼承 (類別設計工具) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1e76d45847d0887b47746c60b836c7acf19d03b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670523"
---
# <a name="how-to-view-inheritance-between-types-class-designer"></a>如何：檢視類型之間的繼承 (類別設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在 [類別設計工具] 中，尋找類別圖上基底類型及其衍生類型之間的繼承關係 (如果存在的話)。 若要建立繼承關聯性，如果兩個類型之間沒有任何關聯性存在，請參閱[如何：建立類型之間的繼承 (類別設計工具)](../ide/how-to-create-inheritance-between-types-class-designer.md)。

### <a name="to-find-the-base-type"></a>尋找基底類型

1. 在類別圖上，按一下要查看基底類別或介面的類型。

2. 在 [類別圖] 功能表上，選擇 [顯示基底類別] 或 [顯示基底介面]。

    隨即會在圖表上將該類型的基底類別或介面顯示為選取項目。 兩個圖案之間現在會顯示所有隱藏的繼承線。

   您也可以使用滑鼠右鍵按一下要顯示其基底類型的類型，然後選擇 [顯示基底類別] 或 [顯示基底介面]。

### <a name="to-find-the-derived-types"></a>尋找衍生類型

1. 在類別圖上，按一下要查看衍生類別或介面的類型。

2. 在 [類別圖] 功能表上，選擇 [顯示衍生類別] 或 [顯示衍生介面]。

    隨即會在圖表上顯示該類型的衍生類別或介面。 各個圖案之間現在會顯示所有隱藏的繼承線。

   您也可以使用滑鼠右鍵按一下要查看其衍生類型的類型，然後選擇 [顯示衍生類別] 或 [顯示衍生介面]。

## <a name="see-also"></a>請參閱
 [如何：建立類型之間的關聯（類別設計工具）](../ide/how-to-create-associations-between-types-class-designer.md) [查看類型和關聯性（類別設計工具）](../ide/viewing-types-and-relationships-class-designer.md)
