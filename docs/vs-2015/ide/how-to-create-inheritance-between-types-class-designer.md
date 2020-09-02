---
title: 如何：建立類型之間的繼承 (類別設計工具) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba27b32cc322da2e14cec86b878a7dd42dae0039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668098"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>如何：建立類型之間的繼承 (類別設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

若要使用 [類別設計工具] 在類別圖上建立兩個類型之間的繼承關係，請將基底類型連接至其衍生類型或其他類型。 您可以建立兩個類別之間的繼承關係、一個類別和一個介面之間的繼承關係，或兩個介面之間的繼承關係。

### <a name="to-create-an-inheritance-between-types"></a>建立兩個類型之間的繼承

1. 從 [方案總管] 的專案中開啟類別圖 (.cd) 檔。

     如果您還沒有類別圖，請先建立類別圖。 請參閱[如何：將類別圖表新增至專案 (類別設計工具)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。

2. 在 [工具箱]**** 的 [類別設計工具]**** 下，按一下 [繼承]****。

3. 在類別圖上，繪製所需類型之間的繼承線，從下列各項開始：

    - 衍生類別到基底類別

    - 實作中的類別到已實作的介面

    - 擴充中的介面到已擴充的介面

4. (選擇性) 如果您有泛型類型的衍生類型，請按一下繼承線。 在 [屬性]**** 視窗中，將**型別引數**屬性設定為符合泛型型別所需的類型。

    > [!NOTE]
    > 如果父抽象類別至少包含一個抽象成員，則所有抽象成員都會實作為非抽象繼承類別。
    >
    >  雖然您可以視覺化現有的泛型類型，不過無法建立新的泛型類型。 您也無法變更現有泛型類型的型別參數。

## <a name="see-also"></a>另請參閱
 [繼承](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)[繼承基本概念](https://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5)[如何： (類別設計工具) ](../ide/how-to-view-inheritance-between-types-class-designer.md) [Visual C++ 類別之間的繼承類別設計工具](../ide/visual-cpp-classes-in-class-designer.md)
