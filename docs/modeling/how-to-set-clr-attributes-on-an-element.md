---
title: "如何： 設定項目上的 CLR 屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1eedf41931c7f9476691e507ab0afcd9e2a4c4ee
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>如何：在項目上設定 CLR 屬性
自訂屬性是特殊的屬性，可以加入至定義域項目、 圖形、 連接器及圖表。 您可以新增任何屬性繼承自`System.Attribute`類別。  
  
### <a name="to-add-a-custom-attribute"></a>若要加入自訂屬性  
  
1.  在**DSL 總管**，選取您要新增自訂屬性的項目。  
  
2.  在**屬性**視窗中下, 一步**自訂屬性**屬性中，按一下瀏覽 (**...**) 圖示。  
  
     **編輯屬性**對話方塊隨即開啟。  
  
3.  在**名稱**資料行中，按一下  **\<加入屬性 >**輸入屬性的名稱。 請按 ENTER 鍵。  
  
4.  屬性名稱下的那一行顯示括號。 在這一行輸入屬性參數類型 (例如， `string`)，然後按 ENTER 鍵。  
  
5.  在**Name 屬性**資料行中，輸入適當的名稱，例如`MyString`。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
     **自訂屬性**屬性現在顯示的屬性，以下列格式：  
  
     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`  
  
## <a name="see-also"></a>請參閱  
 [特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)