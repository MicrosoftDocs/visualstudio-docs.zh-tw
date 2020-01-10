---
title: 如何：建立類型之間的關聯 (類別設計工具)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61b598505ad465ec9086102b9e16e96cb7aa8275
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590380"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>如何：在類別設計工具中建立類型之間的關聯

[類別設計工具] 中的關聯線會顯示圖表中類別的關聯性。 關聯線表示某類別為專案中其他類別的屬性或欄位的類型。 關聯線通常是用來說明專案中類別之間最重要的關係。

雖然您可以將所有欄位或屬性顯示為關聯，但是針對要在圖表上突顯的部分而只將重要成員顯示為關聯才更具意義 (您可以隱藏次要成員或將其顯示為一般成員)。

> [!NOTE]
> [類別設計工具] 只支援單向關聯。

## <a name="to-define-an-association-line-in-the-class-diagram"></a>若要在類別圖中定義關聯線

1. 在 [類別設計工具] 下方的 [工具箱] 選取 [關聯]。

2. 在您要以關聯連結的兩個圖案之間繪製一條線。

     第一個類別中就會建立新的屬性。 這個屬性會以預設名稱顯示為關聯線 (而不是圖案區間中的屬性)。 關聯線所指的圖案即為其類型。

## <a name="to-change-the-name-of-an-association"></a>若要變更關聯名稱

在圖表介面上按一下關聯線的標籤，然後加以編輯。

或遵循下列步驟：

1. 選取其內含屬性顯示為關聯的圖形。

   該圖形會得到焦點，而且其成員會顯示於 [類別細節] 和 [屬性] 視窗中。

2. 在 [類別細節] 或 [屬性] 視窗中編輯該屬性的名稱欄位，然後按 **Enter 鍵**。

   [類別細節] 視窗、關聯線、[屬性] 視窗和程式碼中的名稱會隨之變更。

## <a name="see-also"></a>請參閱

- [如何：在成員標記法和關聯標記法之間變更](how-to-change-between-member-notation-and-association-notation.md)
