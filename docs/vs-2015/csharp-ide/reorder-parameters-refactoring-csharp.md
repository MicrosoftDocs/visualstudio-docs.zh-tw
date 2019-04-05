---
title: 重新排列參數重構 (C#) |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9bec38846f7703ff3958aa1c0fcc9a660a5e080d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943279"
---
# <a name="reorder-parameters-refactoring-c"></a>重新排列參數重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` Visual C# 重構作業，提供簡單的方法，若要變更的方法、 索引子和委派參數的順序。 `Reorder Parameters` 變更宣告，並呼叫成員之任何位置，參數就會重新排列以反映新的順序。  
  
 若要執行`Reorder Parameters`作業，將游標放在或旁邊方法、 索引子或委派。 資料指標位置時，叫用`Reorder Parameters`藉由按下鍵盤快速鍵，或按一下快顯功能表命令的作業。  
  
> [!NOTE]
>  您無法重新排列中擴充方法的第一個參數。  
  
### <a name="to-reorder-parameters"></a>若要重新排列參數  
  
1.  建立名為類別庫`ReorderParameters`，然後取代`Class1`取代下列範例程式碼。  
  
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
  
2.  將游標置於`MethodB`，方法宣告或方法呼叫。  
  
3.  在 **重構**功能表上，按一下**重新排列參數**。  
  
     **重排參數** 對話方塊隨即出現。  
  
4.  在 **重排參數**對話方塊中，選取`int i`中**參數**清單，然後再按 的向下按鈕。  
  
     或者，您可以拖曳`int i`之後`bool b`中**參數**清單。  
  
5.  在 [**重排參數**] 對話方塊中，按一下**確定**。  
  
     如果**預覽參考變更**中選取選項**重新排列參數** 對話方塊中，**預覽變更-重新排列參數**對話方塊會隨即出現。 它提供的參數清單中的變更的預覽`MethodB`簽章和方法呼叫中。  
  
    1.  如果**預覽變更-重新排列參數** 對話方塊出現時，按一下**套用**。  
  
         在此範例中，於方法宣告和所有的方法呼叫站台以`MethodB`會更新。  
  
## <a name="remarks"></a>備註  
 您可以重新排列從方法宣告或方法呼叫的參數。 將游標放在或旁邊方法或委派宣告但不是在本文中。  
  
## <a name="see-also"></a>另請參閱  
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)