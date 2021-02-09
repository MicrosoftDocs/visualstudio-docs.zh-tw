---
title: 如何：使用類別設計工具建立類型
description: '瞭解如何藉由在類別圖上建立 c # 和 Visual Basic 專案來設計新的類型。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6102d5252564834f1de7c533e763d7b08a8f9fb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880537"
---
# <a name="how-to-create-types-by-using-class-designer"></a>如何：使用類別設計工具建立類型

若要為 C# 和 Visual Basic 專案設計新的類型，請在類別圖上建立這些類型。 若要查看現有的類型，請參閱[如何：檢視現有類型](how-to-view-existing-types.md)。

## <a name="create-a-new-type"></a><a name="CreateType"></a> 建立新的類型

1. 在 [ **工具箱**] 的 [ **類別設計工具**] 下，將下列其中一個拖曳至類別圖：

    - [類別] 或 [抽象類別]

    - **列舉**

    - **介面**

    - [結構]\(VB) 或 [結構]\(C#)

    - **代理人**

    - [模組]\(僅限 VB)

2. 為類型命名。 然後選取其存取層級。

3. 選取您要為類型加入之初始程式碼的檔案：

    - 若要建立新的檔案並將它新增至目前專案，請選取 [建立新檔案] 並為檔案命名。

    - 若要將程式碼新增至現有檔案，請選取 [新增至現有檔案]。

         如果方案中有跨多個應用程式共用程式碼的專案，您可以將新的類型加入至應用程式專案中的類別圖，但是，只有相同應用程式專案或共用專案中有對應的類別檔案時才能這樣做。

4. 現在請加入其他項目以定義類型：

    |**出於**|**加入**|
    |-|-|
    |Class、Abstract Class、Structure 或 Struct|定義類別的方法、屬性、欄位、事件、建構函式 (方法)、解構函式 (方法) 和常數。|
    |列舉|構成列舉的欄位值|
    |介面|構成介面的方法、屬性和事件|
    |代理人|定義委派的參數|
    |模組|定義模組的方法、屬性、欄位、事件、建構函式 (方法) 和常數|

     請參閱[建立成員](creating-and-configuring-type-members.md#create-members)。

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> 將自訂屬性套用類型

1. 在類別圖上按一下類型的圖案。

2. 在 [屬性] 視窗中，按一下類型的 [自訂屬性] 旁邊的省略符號 (…) 按鈕。

3. 每一行加入一個或多個自訂屬性。 不要使用括號將屬性括起來。

   自訂屬性會套用至類型。

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> 將自訂屬性套用至類型成員

1. 在類別圖上的成員類型圖案中按一下成員名稱，或是在 [類別細節] 視窗的成員列上按一下成員名稱。

2. 在 [屬性] 視窗中，尋找成員的 [自訂屬性] 屬性。

3. 每一行加入一個或多個自訂屬性。 不要使用括號將屬性括起來。

   自訂屬性會套用至類型。

## <a name="see-also"></a>另請參閱

- [如何：建立類型之間的繼承](how-to-create-inheritance-between-types.md)
- [如何：建立類型之間的關聯](how-to-create-associations-between-types.md)
- [建立及設定類型成員](creating-and-configuring-type-members.md)
- [設計類別和類型](designing-and-viewing-classes-and-types.md)
