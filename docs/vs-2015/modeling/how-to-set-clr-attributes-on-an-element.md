---
title: 如何：在元素上設定 CLR 屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662546"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>如何：在項目上設定 CLR 屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
