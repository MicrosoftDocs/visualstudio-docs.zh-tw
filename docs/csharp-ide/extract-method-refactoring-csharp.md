---
title: "擷取方法重構 (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.extractmethod"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "重構 [C#]，擷取方法"
  - "擷取方法重構作業 [C#]"
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 擷取方法重構 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[**擷取方法**\] 是一項重構作業，可讓您輕鬆地從現有成員的程式碼片段建立新方法。  
  
 您可以使用 \[**擷取方法**\] 從現有成員的程式碼區塊內擷取選取的程式碼範圍，藉此建立新的方法。  新的擷取方法會包含選取的程式碼，而在現有成員中的已選定程式碼會取代成新方法的呼叫。  將程式碼片段轉變成自己的方法，能讓您迅速和正確地重新組織程式碼，以便重複使用並提升可讀性。  
  
 \[**擷取方法**\] 具有下列優點：  
  
-   強調獨立且可重複使用的方法，進而採行最佳編碼做法。  
  
-   由於組織完善，可建立自我記錄的程式碼。  
  
     當使用描述性名稱時，高層次的方法讀起來就像一系列註解。  
  
-   可建立更精細的方法，以簡化覆寫。  
  
-   減少程式碼重複。  
  
### 若要使用擷取方法  
  
1.  建立名為 `ExtractMethod`的主控台應用程式，再以下列範例程式碼取代 `Program`。  
  
    ```c#  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  選取您想要擷取的程式碼片段：  
  
    ```c#  
    double area = PI * radius * radius;  
  
    ```  
  
3.  在 \[**重構**\] 功能表上，按一下 \[**擷取方法**\]。  
  
     \[**擷取方法**\] 對話方塊隨即出現。  
  
     或者，您也可以輸入鍵盤快速鍵 CTRL\+R、M，以顯示 \[**擷取方法**\] 對話方塊。  
  
     您也可以用滑鼠右鍵按一下選取的程式碼，指向 \[**重構**\]，然後按一下 \[**擷取方法**\] 顯示 \[**擷取方法**\] 對話方塊。  
  
4.  在 \[**新方法名稱**\] 方塊中指定新方法的名稱，例如 `CircleArea`。  
  
     \[**預覽方法簽章**\] 下會顯示新方法簽章的預覽。  
  
5.  按一下 \[**確定**\]。  
  
## 備註  
 當您使用 \[**擷取方法**\] 命令時，新方法會插入到同一類別中來源成員之後。  
  
## 部分型別  
 如果類別是部分型別，\[**擷取方法**\] 便會產生緊接在來源成員之後的新方法。  \[**擷取方法**\] 會判斷新方法的簽章，同時在新方法中的程式碼沒有參考任何執行個體 \(Instance\) 資料時建立靜態方法。  
  
## 泛型型別參數  
 如果您擷取的方法有不受限制的泛型型別參數，產生的程式碼就不會將 `ref` 修飾詞 \(Modifier\) 加入至參數，除非已指派值給參數。  如果擷取的方法能夠將參考型別當做泛型型別引數，則您應手動將 `ref` 修飾詞加入至方法簽章中的參數。  
  
## 匿名方法  
 如果嘗試擷取匿名方法 \(Anonymous Method\) 的部分，而其中參考了在該匿名方法外部宣告或參考的區域變數，則 Visual Studio 將會警告您可能發生語意變更。  
  
 若匿名方法使用區域變數的值，會在執行匿名方法時取得該值。  將匿名方法擷取至其他方法內時，則會在呼叫擷取方法時取得區域變數的值。  
  
 下列範例將說明這個語意變更。  如果執行這段程式碼，主控台顯示的會是 **11**。  如果您使用 \[**擷取方法**\] 將程式碼註解標記的程式碼區域擷取到自己的方法內，然後執行重構的程式碼，則主控台將會顯示 **10**。  
  
```c#  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 若要解決這種情況，請將匿名方法中使用的區域變數當做類別的欄位。  
  
## 請參閱  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)