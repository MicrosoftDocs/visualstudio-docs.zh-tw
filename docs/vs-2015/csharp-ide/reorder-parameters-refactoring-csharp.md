---
title: 重新排列參數重構C#（） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673138"
---
# <a name="reorder-parameters-refactoring-c"></a>重新排列參數重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` 是一種C#視覺化重構作業，可讓您輕鬆地變更方法、索引子和委派的參數順序。 `Reorder Parameters` 變更宣告，而且在呼叫該成員的任何位置，會重新排列參數以反映新的順序。

 若要執行 `Reorder Parameters` 作業，請將游標放在方法、索引子或委派的上或旁邊。 當游標位於 [位置] 時，請按下鍵盤快速鍵，或從快捷方式功能表按一下命令，以叫用 `Reorder Parameters` 作業。

> [!NOTE]
> 您無法重新排序擴充方法中的第一個參數。

### <a name="to-reorder-parameters"></a>若要重新排列參數

1. 建立名為 `ReorderParameters` 的類別庫，然後使用下列範例程式碼取代 `Class1`。

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. 將游標放在 `MethodB` 上，不論是在方法宣告或方法呼叫中。

3. 在 [**重構**] 功能表上，按一下 [**重新排列參數**]。

     [**重新排列參數**] 對話方塊隨即出現。

4. 在 [**重新排列參數**] 對話方塊中，選取 [**參數**] 清單中的 [`int i`]，然後按一下 [向下] 按鈕。

     或者，您也可以在 [**參數**] 清單中 `bool b` 後拖曳 `int i`。

5. 在 [**重新排列參數**] 對話方塊中，按一下 **[確定]** 。

     如果已在 [**重新排列參數**] 對話方塊中選取 [**預覽參考變更**] 選項，將會出現 [**預覽變更-重新排列參數**] 對話方塊。 它針對簽章和方法呼叫中的 `MethodB`，提供參數清單變更的預覽。

    1. 如果出現 [**預覽變更-重新排列參數**] 對話方塊，**請按一下 [** 套用]。

         在此範例中，會更新方法宣告和 `MethodB` 的所有方法呼叫網站。

## <a name="remarks"></a>備註
 您可以重新排列方法宣告或方法呼叫中的參數。 將游標放在方法或委派宣告的或旁邊，而不是在主體中。

## <a name="see-also"></a>請參閱
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)