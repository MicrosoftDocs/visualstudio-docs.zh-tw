---
title: 如何：在項目上設定 CLR 屬性
description: 瞭解如何新增任何繼承自 System.object 類別的屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8e566eafce9b5763830c00659a860e6329671bcd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922662"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>如何：在項目上設定 CLR 屬性
自訂屬性是可以加入至網域元素、圖形、連接器和圖表的特殊屬性。 您可以新增任何繼承自類別的屬性 `System.Attribute` 。

### <a name="to-add-a-custom-attribute"></a>若要加入自訂屬性

1. 在 [ **DSL Explorer**] 中，選取您要新增自訂屬性的元素。

2. 在 [ **屬性** ] 視窗中，按一下 [ **自訂屬性** ] 屬性旁的 [流覽 (**...**) 圖示。

     [ **編輯屬性** ] 對話方塊隨即開啟。

3. 在 [ **名稱** ] 欄中，按一下， **\<add attribute>** 然後輸入屬性的名稱。 按 ENTER 鍵。

4. 屬性名稱底下的行會顯示括弧。 在這一行輸入屬性的參數類型 (例如 `string`) ，然後按 enter。

5. 在 [ **名稱] 屬性** 欄中，輸入適當的名稱，例如 `MyString` 。

6. 按一下 [確定]  。

     [ **自訂屬性** ] 屬性現在會以下列格式顯示內容：

     `[`*AttributeName* `(`*ParameterName* `=`*類型*`)]`

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)