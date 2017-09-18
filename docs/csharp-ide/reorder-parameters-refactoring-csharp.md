---
title: "Reorder Parameters Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.reorder"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Reorder Parameters"
  - "Reorder Parameters refactoring [C#]"
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Reorder Parameters Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Reorder Parameters` 是一項 Visual C\# 重構作業，提供了變更方法、索引子和委派之參數順序的簡易方式。  `Reorder Parameters` 會變更宣告，且會在任何呼叫成員的位置重新整理參數，以反映新順序。  
  
 若要執行 `Reorder Parameters` 作業，將資料指標放在方法、索引子或委派旁邊或上面。  資料指標就定位時，請按鍵盤快速鍵或按一下捷徑功能表中的命令，以叫用 `Reorder Parameters` 作業。  
  
> [!NOTE]
>  您無法在擴充方法中重新排列第一個參數。  
  
### 若要重新排列參數  
  
1.  建立名為 `ReorderParameters` 的類別庫，再以下列範例程式碼取代 `Class1`。  
  
    ```c#  
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
  
2.  將游標放在 `MethodB` 上，可以放在方法宣告或方法呼叫中。  
  
3.  在 \[**重整**\] 功能表上按一下 \[**重新排列參數**\]。  
  
     隨即出現 \[**重新排列參數**\] 對話方塊。  
  
4.  在 \[**重新排列參數**\] 對話方塊中，選取 \[**參數**\] 清單中的 `int i`，然後按一下向下按鈕。  
  
     或者，您可以將 `int i` 拖曳到 \[**參數**\] 清單中 `bool b` 的後面。  
  
5.  在 \[**重新排列參數**\] 對話方塊中，按一下 \[**確定**\]。  
  
     如果已在 \[**重新排列參數**\] 對話方塊中選取 \[**預覽參考變更**\] 選項，\[**預覽變更 \- 重新排列參數**\] 對話方塊便會出現。  這個對話方塊可讓您預覽 `MethodB` 的參數清單變更，包括簽章和方法呼叫。  
  
    1.  如果出現 \[**預覽變更 \- 重新排列參數**\] 對話方塊，請按一下 \[**套用**\]。  
  
         在此範例中， `MethodB` 之方法宣告和所有的方法呼叫位置都會更新。  
  
## 備註  
 您可以從方法宣告或方法呼叫中重新排列參數。  將游標放置位在方法或委派宣告本身或旁邊，但不是在主體中。  
  
## 請參閱  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)