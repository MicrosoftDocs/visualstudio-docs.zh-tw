---
title: HOW TO：項目上設定 CLR 屬性 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9af25934a40c01c6b4cfd48dcd7419bddf322d3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698021"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>HOW TO：在項目上設定 CLR 屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

自訂屬性是可以加入至定義域項目、 圖形、 連接器和圖表的特殊屬性。 您可以新增任何屬性繼承自`System.Attribute`類別。  
  
### <a name="to-add-a-custom-attribute"></a>若要新增自訂屬性  
  
1. 在 [ **DSL explorer]**，選取您要新增自訂屬性的項目。  
  
2. 在 [**屬性**視窗中下, 一步]**自訂屬性**屬性，按一下瀏覽 (**...**) 圖示。  
  
     **編輯屬性**對話方塊隨即開啟。  
  
3. 在**名稱**資料行中，按一下**\<加入屬性 >** 輸入屬性的名稱。 請按 ENTER 鍵。  
  
4. 屬性名稱下的那一行顯示括號。 這一行上鍵入屬性的參數類型 (例如`string`)，然後按 ENTER 鍵。  
  
5. 在 **名稱屬性**資料行中，輸入適當的名稱，例如`MyString`。  
  
6. 按一下 [確定] 。  
  
     **自訂屬性**屬性現在顯示的屬性，以下列格式：  
  
     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`  
  
## <a name="see-also"></a>另請參閱  
 [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
