---
title: 檢視類型之間的繼承
description: 瞭解如何在類別設計工具中的類別圖上，尋找基底類型與其衍生類型之間的繼承關係。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7ea00767912b934891780e440016ea8bd0268e78
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951780"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>如何：在類別設計工具中檢視類型之間的繼承

您可以在 [類別設計工具] 中，尋找類別圖表上基底類型及其衍生類型之間的繼承關聯性 (如果存在的話)。 若要建立繼承關聯性，如果不存在，請在兩個型別之間參閱 [如何：建立類型之間的繼承](how-to-create-inheritance-between-types.md)。

## <a name="to-find-the-base-type"></a>尋找基底類型

1. 在類別圖上，按一下要查看基底類別或介面的類型。

2. 在 [類別圖] 功能表上，選擇 [顯示基底類別] 或 [顯示基底介面]。

     隨即會在圖表上將該類型的基底類別或介面顯示為選取項目。 兩個圖案之間現在會顯示所有隱藏的繼承線。

您也可以使用滑鼠右鍵按一下要顯示其基底類型的類型，然後選擇 [顯示基底類別] 或 [顯示基底介面]。

## <a name="to-find-the-derived-types"></a>尋找衍生類型

1. 在類別圖上，按一下要查看衍生類別或介面的類型。

2. 在 [類別圖] 功能表上，選擇 [顯示衍生類別] 或 [顯示衍生介面]。

     隨即會在圖表上顯示該類型的衍生類別或介面。 各個圖案之間現在會顯示所有隱藏的繼承線。

您也可以使用滑鼠右鍵按一下要查看其衍生類型的類型，然後選擇 [顯示衍生類別] 或 [顯示衍生介面]。

## <a name="see-also"></a>另請參閱

- [如何：建立類型之間的關聯](how-to-create-associations-between-types.md)
- [檢視類型和關聯性](designing-and-viewing-classes-and-types.md)
