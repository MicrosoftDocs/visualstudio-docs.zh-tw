---
title: " (c # ) 解壓縮方法重構 |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667548"
---
# <a name="extract-method-refactoring-c"></a>擷取方法重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「**解壓縮」方法**是一種重構作業，可讓您輕鬆地從現有成員的程式碼片段建立新的方法。

 您可以使用 [ **解壓縮方法**]，從現有成員的程式碼區塊中解壓縮選取的程式碼，以建立新的方法。 新的解壓縮方法包含選取的程式碼，而現有成員中選取的程式碼則會取代為新方法的呼叫。 將程式碼片段轉換成它自己的方法，可讓您快速且正確地重新組織程式碼，以更有效率地重複使用和可讀性。

 「**解壓縮」方法**具有下列優點：

- 藉由強調離散、可重複使用的方法，鼓勵最佳編碼做法。

- 透過良好的組織鼓勵自我記錄程式碼。

     使用描述性名稱時，高階方法可以讀取更像一連串的批註。

- 鼓勵建立更精細的方法來簡化覆寫。

- 減少程式碼重複。

### <a name="to-use-extract-method"></a>使用解壓縮方法

1. 建立名為 `ExtractMethod` 的主控台應用程式，再以下列程式碼取代 `Program`。

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

2. 選取您要解壓縮的程式碼片段：

    ```csharp
    double area = PI * radius * radius;
    ```

3. 在 [ **重構** ] 功能表上，按一下 [ **解壓縮方法**]。

     [ **解壓縮方法** ] 對話方塊隨即出現。

     或者，您也可以輸入鍵盤快速鍵 CTRL + R、M，以顯示 [ **解壓縮方法** ] 對話方塊。

     您也可以用滑鼠右鍵按一下選取的程式碼，指向 [ **重構**]，然後按一下 [ **解壓縮方法** ]，以顯示 [ **解壓縮方法** ] 對話方塊。

4. `CircleArea`在 [**新方法名稱**] 方塊中指定新方法的名稱，例如。

     新方法簽章的預覽會顯示在 [ **預覽方法**簽章] 下。

5. 按一下 [確定]  。

## <a name="remarks"></a>備註
 當您使用 [ **解壓縮方法** ] 命令時，會在相同類別中的來源成員後面插入新的方法。

## <a name="partial-types"></a>部分型別
 如果類別是部分類型，則 [ **解壓縮方法** ] 會在來源成員之後立即產生新的方法。 如果新方法中的程式碼未參考任何實例資料，則 [**解壓縮] 方法**會決定新方法的簽章，並建立靜態方法。

## <a name="generic-type-parameters"></a>泛型類型參數
 當您解壓縮具有未受限制泛型型別參數的方法時，產生的程式碼將不會將修飾詞加入 `ref` 至該參數，除非已指派值給該參數。 如果已解壓縮的方法將支援參考型別作為泛型型別引數，則您應該手動將修飾詞加入 `ref` 至方法簽章中的參數。

## <a name="anonymous-methods"></a>匿名方法
 如果您嘗試解壓縮部分匿名方法，其中包含在匿名方法外宣告或參考之區域變數的參考，則 Visual Studio 會警告您可能發生的語義變更。

 當匿名方法使用本機變數的值時，就會在執行匿名方法時取得該值。 將匿名方法解壓縮至另一個方法時，會在呼叫解壓縮方法時取得區域變數的值。

 下列範例說明此語義變更。 如果執行此程式碼，則會將 **11** 列印到主控台。 如果您使用 [ **解壓縮方法** ]，將程式碼註解標記的程式碼區域解壓縮至它自己的方法，然後執行重構的程式碼，則會將 **10** 列印到主控台。

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

 若要解決這種情況，請在類別的 [匿名方法] 欄位中，使用本機變數。

## <a name="see-also"></a>另請參閱
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)