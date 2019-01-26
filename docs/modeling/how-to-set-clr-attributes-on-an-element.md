---
title: HOW TO：在項目上設定 CLR 屬性
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 54b4340fe72552f3287a5c6ebec55c9c9d326ac1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932268"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>HOW TO：在項目上設定 CLR 屬性
自訂屬性是可以加入至定義域項目、 圖形、 連接器和圖表的特殊屬性。 您可以新增任何屬性繼承自`System.Attribute`類別。

### <a name="to-add-a-custom-attribute"></a>若要新增自訂屬性

1.  在 [ **DSL explorer]**，選取您要新增自訂屬性的項目。

2.  在 [**屬性**視窗中下, 一步]**自訂屬性**屬性，按一下瀏覽 (**...**) 圖示。

     **編輯屬性**對話方塊隨即開啟。

3.  在**名稱**資料行中，按一下**\<加入屬性 >** 輸入屬性的名稱。 請按 ENTER 鍵。

4.  屬性名稱下的那一行顯示括號。 這一行上鍵入屬性的參數類型 (例如`string`)，然後按 ENTER 鍵。

5.  在 **名稱屬性**資料行中，輸入適當的名稱，例如`MyString`。

6.  按一下 [確定 **Deploying Office Solutions**]。

     **自訂屬性**屬性現在顯示的屬性，以下列格式：

     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`

## <a name="see-also"></a>另請參閱

- [特定領域語言工具字彙](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)