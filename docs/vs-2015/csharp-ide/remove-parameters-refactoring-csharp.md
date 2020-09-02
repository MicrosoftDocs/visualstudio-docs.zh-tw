---
title: '移除參數重構 (c # ) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667497"
---
# <a name="remove-parameters-refactoring-c"></a>移除參數重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` 是一種重構作業，可讓您輕鬆地從方法、索引子或委派中移除參數。 移除參數會變更宣告;在呼叫成員的任何位置，會移除參數以反映新的宣告。

 您可以先將游標放在方法、索引子或委派上，以執行「移除參數」作業。 當游標位於位置時，若要叫用移除作業 `Parameters` ，請按一下 [ **重構** ] 功能表，按下鍵盤快速鍵，或從快捷方式功能表中選取命令。

> [!NOTE]
> 您無法移除擴充方法中的第一個參數。

### <a name="to-remove-parameters"></a>移除參數

1. 建立名為的主控台應用程式 `RemoveParameters` ，然後 `Program` 以下列程式碼取代。

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

2. 將游標放在方法上 `A` ，方法是在方法宣告或方法呼叫中。

3. 從 [ **重構** ] 功能表選取 [ **移除參數** ]，以顯示 [ **移除參數** ] 對話方塊。

     您也可以輸入鍵盤快速鍵 CTRL + R、V 來顯示 [ **移除參數** ] 對話方塊。

     您也可以用滑鼠右鍵按一下游標，指向 [ **重構**]，然後按一下 [ **移除參數** ]，以顯示 [ **移除參數** ] 對話方塊。

4. 使用 [ **參數** ] 欄位，將游標放在上 `int i` ，然後按一下 [ **移除**]。

5. 按一下 [確定]  。

6. 在 [ **預覽變更-移除參數** ] 對話方塊中， **按一下 [** 套用]。

## <a name="remarks"></a>備註
 您可以從方法宣告或方法呼叫中移除參數。 將游標放在方法宣告或委派名稱中，並叫用移除參數。

> [!CAUTION]
> Remove 參數可讓您移除成員主體中參考的參數，但不會移除方法主體中該參數的參考。 這可能會在您的程式碼中引進組建錯誤。 不過，您可以使用 [ **預覽變更** ] 對話方塊來檢查程式碼，然後再執行重構作業。

 如果在呼叫方法期間修改了要移除的參數，則移除參數也會移除修改。 例如，如果方法呼叫變更自

```csharp
MyMethod(param1++, param2);
```

 至

```csharp
MyMethod(param2);
```

 重構作業 `param1` 將不會遞增。

## <a name="see-also"></a>另請參閱
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)