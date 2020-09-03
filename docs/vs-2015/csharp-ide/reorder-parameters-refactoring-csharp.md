---
title: '重新排列參數重構 (c # ) |Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673138"
---
# <a name="reorder-parameters-refactoring-c"></a>重新排列參數重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` 是一種 Visual c # 重構作業，可提供簡單的方法來變更方法、索引子和委派的參數順序。 `Reorder Parameters` 變更宣告，並且在呼叫該成員的任何位置，將參數重新排列以反映新的順序。

 若要執行此作業 `Reorder Parameters` ，請將游標放在方法、索引子或委派的旁邊或旁邊。 當游標在位置時，請 `Reorder Parameters` 按鍵盤快速鍵叫用作業，或從快捷方式功能表中按一下命令。

> [!NOTE]
> 您無法在擴充方法中重新排列第一個參數。

### <a name="to-reorder-parameters"></a>重新排列參數

1. 建立名為的類別庫 `ReorderParameters` ，然後 `Class1` 以下列範例程式碼取代。

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

2. 將游標放在 `MethodB` 方法宣告或方法呼叫中。

3. 在 [ **重構** ] 功能表上，按一下 [ **重新排列參數**]。

     [ **重新排列參數** ] 對話方塊隨即出現。

4. 在 [ **重新排列參數** ] 對話方塊中，選取 `int i` [ **參數** ] 清單中的，然後按一下 [向下] 按鈕。

     或者，您可以 `int i` `bool b` 在 [ **參數** ] 清單中拖曳之後。

5. 在 [ **重新排列參數** ] 對話方塊中，按一下 **[確定]**。

     如果選取 [**重新排列參數**] 對話方塊中的 [**預覽參考變更**] 選項，將會出現 [**預覽變更-重新排列參數**] 對話方塊。 它會針對簽章和方法呼叫中的參數清單，提供這些變更的預覽 `MethodB` 。

    1. 如果出現 [ **預覽變更-重新排列參數** ] 對話方塊， **請按一下 [** 套用]。

         在此範例中，會更新方法宣告和的所有方法呼叫網站 `MethodB` 。

## <a name="remarks"></a>備註
 您可以從方法宣告或方法呼叫重新排列參數。 將游標放在方法或委派宣告的旁邊或旁邊，但不在主體中。

## <a name="see-also"></a>另請參閱
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)