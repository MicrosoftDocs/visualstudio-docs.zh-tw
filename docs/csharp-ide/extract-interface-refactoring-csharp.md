---
title: "Extract Interface Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.extractinterface"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Extract Interface"
  - "Extract Interface refactoring operation [C#]"
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extract Interface Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[擷取介面\] 是一項重構作業，提供了建立新介面的簡易方式，且新介面中會包含從現有類別、結構或介面產生的成員。  
  
 當數個用戶端使用某個類別、結構或介面的相同成員子集，或多個類別、結構或介面擁有相同的成員子集時，這項作業對於在介面中納入該成員子集來說相當實用。  如需使用介面的詳細資訊，請參閱[介面](/dotnet/csharp/programming-guide/interfaces/index)。  
  
 \[擷取介面\] 會在新檔案中產生一個介面，並將游標放置在新檔案的開頭。  您可以使用 **Extract Interface** 對話方塊指定要擷取到新介面中的成員、新介面的名稱，以及所產生檔案的名稱。  
  
### 若要使用擷取介面  
  
1.  建立名為 `ExtractInterface`的主控台應用程式，再以下列程式碼取代 `Program`。  
  
    ```c#  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  將游標位置停在 `MethodB` 中，然後按一下 \[**重構**\] 功能表上的 \[**擷取介面**\]。  
  
     \[**擷取介面**\] 對話方塊便會出現。  
  
     您也可以輸入鍵盤快速鍵 CTRL\+R、I，以顯示 \[**擷取介面**\] 對話方塊。  
  
     您也可以按一下滑鼠右鍵，指向 \[**重構**\]，然後按一下 \[**擷取介面**\] 顯示 \[**擷取介面**\] 對話方塊。  
  
3.  按一下 \[**全選**\]。  
  
4.  按一下 \[**確定**\]。  
  
     您會看見新檔案、IProtoA.cs 和下列程式碼：  
  
    ```c#  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## 備註  
 只有當游標位於包含要擷取之成員的類別、結構或介面中時，才能使用這項功能。  當游標位於這個位置時，請叫用 \[擷取介面\] 重構作業。  
  
 當您在類別或結構上叫用擷取介面時，會修改基底和介面清單以加入新介面的名稱。  當您在介面上叫用擷取介面時，並不會修改基底和介面清單。  
  
## 請參閱  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)