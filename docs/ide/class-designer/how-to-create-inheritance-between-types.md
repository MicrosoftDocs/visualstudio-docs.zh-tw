---
title: 如何：建立類型之間的繼承 (類別設計工具)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbf540056318e092db13521dc80478cc7eb91948
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590367"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>如何：在類別設計工具中建立類型之間的繼承

要使用**類設計器**在類別圖表上創建兩種類型之間的繼承關係，請將基類型與其派生類型或類型連接。 您可以建立兩個類別之間的繼承關係、一個類別和一個介面之間的繼承關係，或兩個介面之間的繼承關係。

## <a name="to-create-an-inheritance-between-types"></a>建立兩個類型之間的繼承

1. 從**解決方案資源管理器**中的專案中，打開類圖 （.cd） 檔。

     如果您還沒有類別圖，請先建立類別圖。 請參閱[如何：將類別圖新增至專案](how-to-add-class-diagrams-to-projects.md)。

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

- [繼承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [繼承基本概念](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [如何：檢視類型之間的繼承](how-to-view-inheritance-between-types.md)
- [類別設計工具中的 Visual C++ 類別](visual-cpp-classes.md)
