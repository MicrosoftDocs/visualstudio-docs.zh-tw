---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "移除參數重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.remove
dev_langs: CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5e53d813d9b2dcefd2b2d19da2a76b6c0d1f989
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="remove-parameters-refactoring-c"></a>移除參數重構 (C#)
`Remove Parameters`是提供簡單的方式，從方法、 索引子或委派移除參數重構作業。 移除參數變更宣告;在呼叫成員的任何位置，以反映新的宣告被移除的參數。  
  
 您可以先將定位資料指標在方法、 索引子或委派執行移除參數作業。 位置，來叫用 移除資料指標時`Parameters`作業中，按一下 **重構**功能表上，按下鍵盤快速鍵，或從快顯功能表中選取的命令。  
  
> [!NOTE]
>  您無法擴充方法中移除第一個參數。  
  
### <a name="to-remove-parameters"></a>若要移除參數  
  
1.  建立名為主控台應用程式`RemoveParameters`，然後取代`Program`為下列程式碼。  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  將游標放在方法上`A`，有兩種方法宣告或方法呼叫。  
  
3.  從**重構**功能表上，選取**移除參數**顯示**移除參數** 對話方塊。  
  
     您也可以輸入鍵盤快速鍵 CTRL + R、 V 以顯示 [**移除參數**] 對話方塊。  
  
     您也可以以滑鼠右鍵按一下資料指標，指向 **重構**，然後按一下 **移除參數**顯示**移除參數** 對話方塊。  
  
4.  使用**參數**欄位中，將游標放在`int i`，然後按一下 **移除**。  
  
5.  按一下 [確定]。  
  
6.  在**預覽變更 — 移除參數**對話方塊中，按一下 **套用**。  
  
## <a name="remarks"></a>備註  
 您可以移除方法宣告或方法呼叫的參數。 將游標放在方法宣告或委派的名稱，然後叫用移除參數。  
  
> [!CAUTION]
>  移除參數可讓您移除的成員，但其主體中參考的參數不會移除對該參數參考方法主體中。 這樣可能會導致建置錯誤，您的程式碼。 不過，您可以使用**預覽變更**執行重構作業之前，請先檢閱您的程式碼 對話方塊。  
  
 如果要移除的參數修改期間對方法的呼叫，移除參數也會移除所作的修改。 例如，如果方法會呼叫已從  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 設為  
  
```csharp  
MyMethod(param2);  
```  
  
 重構作業，由`param1`也不會遞增。  
  
## <a name="see-also"></a>另請參閱  
 [重構 (C#)](refactoring-csharp.md)