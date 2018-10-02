---
title: 如何：使用類別設計工具建立類型 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f7671b1336b0b722f02cc100c7055fef817cb582
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499113"
---
# <a name="how-to-create-types-by-using-class-designer"></a>如何：使用類別設計工具建立類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 使用類別設計工具建立類型](https://docs.microsoft.com/visualstudio/ide/how-to-create-types-by-using-class-designer)。  
  
若要為 Visual C# .NET 和 Visual Basic .NET 專案設計新的類型，請在類別圖上建立這些類型。 若要查看現有的類型，請參閱[如何：檢視現有類型 (類別設計工具)](../ide/how-to-view-existing-types-class-designer.md)。  
  
-   [建立新的類型](#CreateType)  
  
-   [將自訂屬性套用至類型](#CustAttributeType)  
  
-   [將自訂屬性套用至類型成員](#CustAttributeMember)  
  
##  <a name="CreateType"></a>建立新的類型  
  
1.  在 [工具箱] 的 [類別設計工具] 下方，拖曳其中一個項目至類別圖上：  
  
    -   [類別] 或 [抽象類別]  
  
    -   **Enum**  
  
    -   **Interface**  
  
    -   [結構] (VB) 或 [結構] (C#)  
  
    -   **Delegate**  
  
    -   [模組] (僅限 VB)  
  
2.  為類型命名。 然後選取其存取層級。  
  
3.  選取您要為類型加入之初始程式碼的檔案：  
  
    -   若要建立新的檔案並將它新增至目前專案，請選取 [建立新檔案] 並為檔案命名。  
  
    -   若要將程式碼新增至現有檔案，請選取 [新增至現有檔案]。  
  
         如果方案中有跨多個應用程式共用程式碼的專案，您可以將新的類型加入至應用程式專案中的類別圖，但是，只有相同應用程式專案或共用專案中有對應的類別檔案時才能這樣做。  
  
4.  現在請加入其他項目以定義類型：  
  
    |||  
    |-|-|  
    |**針對**|**[新增]**|  
    |Class、Abstract Class、Structure 或 Struct|定義類別的方法、屬性、欄位、事件、建構函式 (方法)、解構函式 (方法) 和常數。|  
    |列舉|構成列舉的欄位值|  
    |介面|構成介面的方法、屬性和事件|  
    |委派|定義委派的參數|  
    |Module|定義模組的方法、屬性、欄位、事件、建構函式 (方法) 和常數|  
  
     請參閱[建立成員](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)。  
  
##  <a name="CustAttributeType"></a> 將自訂屬性套用類型  
  
1.  在類別圖上按一下類型的圖案。  
  
2.  在 [屬性] 視窗中，旁邊**自訂屬性**型別的屬性，按一下省略符號 （...） 按鈕。  
  
3.  每一行加入一個或多個自訂屬性。 不要使用括號將屬性括起來。  
  
     當您完成時，所輸入的自訂屬性就會套用至類型。  
  
##  <a name="CustAttributeMember"></a> 將自訂屬性套用至類型成員  
  
1.  在類別圖上的成員類型圖案中按一下成員名稱，或是在 [類別細節] 視窗的成員列上按一下成員名稱。  
  
2.  在 [屬性] 視窗中，尋找成員的 [自訂屬性] 屬性。  
  
3.  每一行加入一個或多個自訂屬性。 不要使用括號將屬性括起來。  
  
     當您完成時，所輸入的自訂屬性就會套用至類型。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立類型之間的繼承 (類別設計工具)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [如何：建立類型之間的關聯 (類別設計工具)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [建立和設定類型成員 (類別設計工具)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [使用類別圖表 (類別設計工具)](../ide/working-with-class-diagrams-class-designer.md)   
 [設計類別和類型 (類別設計工具)](../ide/designing-classes-and-types-class-designer.md)



