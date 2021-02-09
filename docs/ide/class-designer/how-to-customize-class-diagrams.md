---
title: 如何：自訂類別圖表 (類別設計工具)
description: 瞭解如何變更類別圖表顯示資訊的方式，以及如何自訂整個圖表或設計介面上的個別類型。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 768c61ab525d03a7b9a1a80481b84b492d6bd0c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919645"
---
# <a name="how-to-customize-class-diagrams"></a>如何：自訂類別圖表

您可以變更類別圖顯示資訊的方式， 也可以在設計介面上自訂整個圖表或個別類型。

例如，您可以調整整個類別圖的縮放比例、變更個別類型成員的群組和排序方式、隱藏或顯示關聯性，以及將個別或多組類型移至圖表的任何位置。

> [!NOTE]
> 自訂圖形出現在圖表中的方式不會改變圖表呈現類型的基礎程式碼。

包含類型成員的區段（例如類別中的 **Properties** 區段）稱為區間。 您可以隱藏或顯示個別區間和類型成員。

## <a name="zoom-in-and-out-of-the-class-diagram"></a>放大或縮小類別圖

1. 在 **類別設計工具** 中，開啟並選取類別圖表檔案。

2. 在 [ **類別設計工具** ] 工具列上，按一下 [ **放大** ] 或 [ **縮小** ] 按鈕，以變更設計工具介面的縮放層級。

     或

     指定特定的縮放值。 您可以使用 [縮放] 下拉式清單，或鍵入有效的縮放比例 (有效範圍介於 10% 到 400% 之間)。

    > [!NOTE]
    > 變更縮放比例不會影響類別圖列印成品的比例。

## <a name="customize-grouping-and-sorting-of-type-members"></a>自訂類型成員的群組和排序方式

1. 在 **類別設計工具** 中，開啟並選取類別圖表檔案。

2. 以滑鼠右鍵按一下設計介面的空白區域，再指向 [群組成員]。

3. 選取下列其中一個可用選項：

    - **依種類分組**：將個別類型成員分到 [屬性]、[方法]、[事件] 和 [欄位] 的群組清單中。 個別群組相依於實體定義。例如，如果還沒有定義類別的事件，該類別就不會顯示任何事件群組。

    - **依存取權分組**：依據成員的存取修飾詞，將個別類型成員分到群組清單中。 例如，公用和私用。

    - **依字母順序排序**：以一份依字母順序排列的清單顯示構成實體的項目。 清單以遞增方式排序。

## <a name="hide-compartments-on-a-type"></a>隱藏類型上的區間

1. 在 **類別設計工具** 中，開啟並選取類別圖表檔案。

2. 以滑鼠右鍵按一下類型中要自訂的成員分類 (例如，選取類別中的 [方法] 節點)。

3. 按一下 [隱藏區間]。

     選取的區間隨即從類型容器消失。

## <a name="hide-individual-members-on-a-type"></a>隱藏類型上的個別成員

1. 在 **類別設計工具** 中，開啟並選取類別圖表檔案。

2. 以滑鼠右鍵按一下您要隱藏的類型成員。

3. 按一下 [隱藏]。

     選取的成員隨即從類型容器消失。

## <a name="show-hidden-compartments-and-members-on-a-type"></a>在類型上顯示隱藏的區間和成員

1. 在 **類別設計工具** 中，開啟並選取類別圖表檔案。

2. 以滑鼠右鍵按一下含有隱藏區間的類型名稱。

3. 按一下 [顯示所有成員]。

     所有隱藏的區間和成員隨即都出現在類型容器中。

## <a name="hide-relationships"></a>隱藏關聯性

1. 在 **類別設計工具** 中，開啟並選取類別圖表檔案。

2. 以滑鼠右鍵按一下您要隱藏的關聯線或繼承線。

3. 對關聯線按一下 [隱藏]，對繼承線則按一下 [隱藏繼承線]。

4. 按一下 [顯示所有成員]。

     所有隱藏的區間和成員隨即都出現在類型容器中。

## <a name="show-hidden-relationships"></a>顯示隱藏的關聯性

1. 在 **類別設計工具** 中，開啟並選取類別圖表檔案。

2. 以滑鼠右鍵按一下含有關聯線或繼承線的類型。

   對關聯線按一下 [顯示所有成員]，對繼承線則按一下 [顯示基底類別] 或 [顯示衍生類別]。

## <a name="remove-a-shape-from-a-class-diagram"></a>從類別圖移除圖形
您可以從類別圖移除類型圖形，而不會影響類型的基礎程式碼。 從類別圖移除類型圖案只會影響該圖表：定義類型的基礎程式碼以及顯示類型的其他圖表不受影響。

1. 在類別圖上，選取要從圖表移除的類型圖案。

2. 從 [編輯] 功能表中選擇 [從圖表移除]。

     圖表上就不會再出現該類型圖案以及連接至圖案的關聯線或繼承關聯線。

## <a name="delete-a-type-shape-and-its-underlying-code"></a>刪除類型圖案及其基礎程式碼

1. 在設計介面的圖案上按一下滑鼠右鍵。

2. 從操作功能表選取 [刪除程式碼]。

     圖案隨即從圖表移除，其基礎程式碼也會從專案刪除。

## <a name="see-also"></a>另請參閱

- [如何：在成員標記法和關聯標記法之間變更](how-to-change-between-member-notation-and-association-notation.md)
- [如何：檢視現有類型](how-to-view-existing-types.md)
- [檢視類型和關聯性](designing-and-viewing-classes-and-types.md)
