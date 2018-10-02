---
title: 移除參數重構 (C#) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 529950d72ac11ebfd443a85db597adfcbc89bba1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497518"
---
# <a name="remove-parameters-refactoring-c"></a>移除參數重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` 是的重整作業，提供簡單的方法來移除方法、 索引子或委派的參數。 移除參數變更宣告;呼叫成員之任何位置，會移除參數，以反映新的宣告。  
  
 您第一遊標定位在方法、 索引子或委派執行移除參數的作業。 在位置，叫用 移除資料指標時`Parameters`作業中，按一下**重構**功能表上，按下鍵盤快速鍵，或從快顯功能表選取命令。  
  
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
  
2.  將游標放在方法上`A`，方法宣告或方法呼叫。  
  
3.  從**重構**功能表上，選取**移除參數**以顯示**移除參數** 對話方塊。  
  
     您也可以輸入鍵盤快速鍵 CTRL + R、 V 以顯示**移除參數** 對話方塊。  
  
     您也可以以滑鼠右鍵按一下資料指標，指向**重構**，然後按一下**移除參數**以顯示**移除參數** 對話方塊。  
  
4.  使用**參數**欄位中，將游標放在`int i`，然後按一下**移除**。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
6.  在 [**預覽變更--移除參數**] 對話方塊中，按一下**套用**。  
  
## <a name="remarks"></a>備註  
 您可以從方法宣告或方法呼叫，以移除參數。 將游標放在方法宣告或委派的名稱，然後叫用移除參數。  
  
> [!CAUTION]
>  移除參數可讓您移除參考的參數內的成員，但它不會移除對該參數參考方法主體中。 這可能會發生建置錯誤導入您的程式碼。 不過，您可以使用**預覽變更**對話方塊，即可檢閱您的程式碼，然後再執行重構作業。  
  
 如果要移除的參數已修改的方法呼叫期間，移除參數也會移除所作的修改。 例如，如果呼叫的方法已從  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 設為  
  
```csharp  
MyMethod(param2);  
```  
  
 重構作業，`param1`也不會遞增。  
  
## <a name="see-also"></a>另請參閱  
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)