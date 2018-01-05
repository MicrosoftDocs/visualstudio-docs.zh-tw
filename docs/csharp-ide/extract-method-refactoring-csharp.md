---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-method
title: "擷取方法重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 18fc4c20b39341f884fb23b51822ce7f6e427007
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="extract-method-refactoring-c"></a>擷取方法重構 (C#)
**擷取方法**是重構作業，提供簡單的方法來建立新的方法，從現有成員的程式碼片段。  
  
 使用**擷取方法**，您可以建立一個新方法，擷取選取的 從現有成員的程式碼區塊內的程式碼。 新的擷取方法包含所選的程式碼，並在現有的成員中選取的程式碼取代新方法的呼叫。 開啟的程式碼片段至它自己的方法可讓您快速和精確地重新組織程式碼更佳的重複使用並提升可讀性。  
  
 **擷取方法**具有下列優點：  
  
-   強調離散、 可重複使用的方法，也採用最佳編碼作法。  
  
-   可促使組織程式碼可以自我記錄。  
  
     當具描述性的名稱時使用的高階方法讀的起來就像一系列的註解。  
  
-   可建立更精細的方法，以簡化覆寫。  
  
-   減少程式碼重複。  
  
### <a name="to-use-extract-method"></a>若要使用擷取方法  
  
1.  建立名為 `ExtractMethod` 的主控台應用程式，再以下列程式碼取代 `Program`。  
  
    ```csharp  
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
  
    ```csharp  
    double area = PI * radius * radius;  
    ```  
  
3.  在**重構**功能表上，按一下 **擷取方法**。  
  
     **擷取方法** 對話方塊隨即出現。  
  
     或者，您也可以輸入鍵盤快速鍵 CTRL + R、 M，顯示**擷取方法** 對話方塊。  
  
     您可以也以滑鼠右鍵按一下所選程式碼中，指向 **重構**，然後按一下 **擷取方法**顯示**擷取方法** 對話方塊。  
  
4.  指定新方法的名稱，例如`CircleArea`，請在**新方法名稱**方塊。  
  
     底下會顯示新的方法簽章的預覽**預覽方法簽章**。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="remarks"></a>備註  
 當您使用**擷取方法**命令時，新的方法就會插入下列來源中的成員相同的類別。  
  
## <a name="partial-types"></a>部分型別  
 如果類別是部分的型別，則**擷取方法**會產生新的後置節點來源成員的方法。 **擷取方法**決定新方法，新的方法中的程式碼不參考任何執行個體資料時，建立靜態方法的簽章。  
  
## <a name="generic-type-parameters"></a>泛型型別參數  
 當您擷取具有受條件約束的泛型型別參數的方法時，就不會新增產生的程式碼`ref`至該參數修飾詞除非將值指派給它。 如果擷取的方法將支援參考型別作為泛型型別引數，則您應手動將`ref`修飾詞加入方法簽章中的參數。  
  
## <a name="anonymous-methods"></a>匿名方法  
 如果您嘗試解壓縮包含區域變數宣告或匿名方法之外參考了參考的匿名方法的一部分，然後 Visual Studio 會警告您有關潛在語意的變更。  
  
 當匿名方法使用本機變數的值時，會取得值，此時執行匿名方法。 另一個方法擷取匿名方法時，本機變數的值被取得時的解壓縮方法的呼叫。  
  
 下列範例說明這個語意的變更。 如果執行的這段程式碼，然後**11**會列印到主控台。 如果您使用**擷取方法**擷取的程式碼註解標示成自己的方法的程式碼區域，並接著執行重構的程式碼，然後**10**會列印到主控台。  
  
```csharp  
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
  
 若要解決這種情況，請在匿名方法欄位之類別中可用的本機變數。  
  
## <a name="see-also"></a>請參閱  
 [重構 (C#)](refactoring-csharp.md)