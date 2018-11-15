---
title: 如何：實作介面 (類別設計工具) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a196f49765623966a48b07eef3abe3f8ca7e5a1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900536"
---
# <a name="how-to-implement-an-interface-class-designer"></a>如何：實作介面 (類別設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在類別設計工具中，您可以將介面連線至替介面方法提供程式碼的類別，以在類別圖表上實作介面。 類別設計工具會產生介面實作，並將介面和類別之間的關聯性顯示為繼承關聯性。 您可以在介面與類別之間繪製繼承線，或從 [類別檢視] 中拖曳介面，來實作介面。  
  
> [!TIP]
>  您可以像建立其他類型一樣建立介面。 如果介面存在，但未出現在類別圖表上，請先顯示它。 如需詳細資訊，請參閱[如何：使用類別設計工具建立類型](../ide/how-to-create-types-by-using-class-designer.md)和[如何：檢視現有類型 (類別設計工具)](../ide/how-to-view-existing-types-class-designer.md)。  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>繪製繼承線來實作介面  
  
1. 在類別圖表上，顯示介面和將實作介面的類別。  
  
2. 從類別和介面繪製繼承線。  
  
    會顯示棒棒糖符號，附加至類別，並且具有介面名稱的標籤會識別繼承關聯性。 Visual Studio 會為所有介面成員產生虛設常式。  
  
   如需詳細資訊，請參閱[如何：建立類型之間的繼承 (類別設計工具)](../ide/how-to-create-inheritance-between-types-class-designer.md)。  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>從 [類別檢視] 視窗實作介面  
  
1.  在類別圖表上，顯示您要實作介面的類別。  
  
2.  開啟 [類別檢視]，並找出此介面。  
  
    > [!TIP]
    >  如果未開啟 [類別檢視]，請從 [檢視] 功能表將其開啟。 如需類別檢視的詳細資訊，請參閱[檢視類別和其成員](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333)。  
  
3.  將介面節點拖曳到圖表上的類別圖形。  
  
     會顯示棒棒糖符號，附加至類別，並且具有介面名稱的標籤會識別繼承關聯性。 Visual Studio 會為所有介面成員產生虛設常式。此時，即已實作介面。  
  
## <a name="see-also"></a>另請參閱  
 [如何：使用類別設計工具建立類型](../ide/how-to-create-types-by-using-class-designer.md)   
 [如何：檢視現有類型 (類別設計工具)](../ide/how-to-view-existing-types-class-designer.md)   
 [如何：建立類型之間的繼承 (類別設計工具)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [重構類別和類型 (類別設計工具)](../ide/refactoring-classes-and-types-class-designer.md)



