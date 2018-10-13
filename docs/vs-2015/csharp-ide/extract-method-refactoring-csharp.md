---
title: 擷取方法重構 (C#) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cc05da79676beed5fa698f11843a6b7485280e71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228055"
---
# <a name="extract-method-refactoring-c"></a>擷取方法重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extrahovat Metodu**是重構作業，提供簡單的方法來建立新的方法，從現有成員的程式碼片段。  
  
 使用**擷取方法**，您可以擷取選取的 從現有成員的程式碼區塊內的程式碼來建立新的方法。 新的擷取方法包含選取的程式碼，並呼叫新方法會取代現有的成員中選取的程式碼。 將程式碼片段轉換成它自己的方法可讓您快速和精確地重新組織程式碼更好的重複使用和可讀性。  
  
 **Extrahovat Metodu**具有下列優點：  
  
-   強調離散、 可重複使用的方法，建議採用最佳編碼作法。  
  
-   可促進程式碼透過極佳的組織可以自我記錄。  
  
     當具描述性的名稱時使用的高階方法讀的起來就像一系列的註解。  
  
-   可建立更細微的方法，以簡化覆寫。  
  
-   減少程式碼重複。  
  
### <a name="to-use-extract-method"></a>若要使用 擷取方法  
  
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
  
3.  在 **重構**功能表上，按一下**擷取方法**。  
  
     **擷取方法** 對話方塊隨即出現。  
  
     或者，您也可以輸入鍵盤快速鍵 CTRL + R、 M 可顯示**擷取方法** 對話方塊。  
  
     您可以也以滑鼠右鍵按一下所選程式碼中，指向**重構**，然後按一下**擷取方法**以顯示**擷取方法**對話方塊。  
  
4.  指定名稱，以針對新的方法，例如`CircleArea`，請在**新的方法名稱** 方塊中。  
  
     底下會顯示新的方法簽章的預覽**預覽方法簽章**。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="remarks"></a>備註  
 當您使用**擷取方法**命令時，新的方法會插入下列來源類別中的成員相同。  
  
## <a name="partial-types"></a>部分型別  
 如果類別是部分的型別，則**擷取方法**會產生來源成員的正後方的新方法。 **Extrahovat Metodu**決定新的方法，任何執行個體資料不參考中的新方法的程式碼時建立的靜態方法的簽章。  
  
## <a name="generic-type-parameters"></a>泛型型別參數  
 當您擷取具有不受限制的泛型類型參數的方法時，不會加入產生的程式碼`ref`至該參數的修飾詞除非將值指派給它。 如果擷取的方法將會支援參考型別作為泛型型別引數，則您應該手動加入`ref`方法簽章中參數的修飾詞。  
  
## <a name="anonymous-methods"></a>匿名方法  
 如果您嘗試擷取屬於匿名方法，其中包含區域變數宣告或匿名方法外部參考的參考，然後 Visual Studio 會警告您潛在的語意變更。  
  
 當匿名方法使用本機變數的值時，會取得值，目前執行匿名方法。 當匿名方法會擷取至另一種方法中時，本機變數的值被取得在擷取的方法呼叫的時間。  
  
 下列範例會說明這個語意的變更。 如果執行的這段程式碼，然後**11**會列印到主控台。 如果您使用**擷取方法**擷取的程式碼註解標示構成它自己的程式碼區域，並接著執行重構的程式碼，然後**10**會列印到主控台。  
  
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
  
 若要解決這種情況下，讓本機變數所使用的匿名方法類別的欄位。  
  
## <a name="see-also"></a>另請參閱  
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)