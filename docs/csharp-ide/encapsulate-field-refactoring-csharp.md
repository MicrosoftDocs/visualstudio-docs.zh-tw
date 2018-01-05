---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: "封裝欄位重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: d587edebcea443e0bfff52004b128c70923470d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="encapsulate-field-refactoring-c"></a>封裝欄位重構 (C#)
**封裝欄位**重構作業，可讓您快速地從現有的欄位，建立屬性，然後以新屬性的參考順暢地更新您的程式碼。  
  
 當[欄位](/dotnet/csharp/programming-guide/classes-and-structs/fields)是[公用](/dotnet/csharp/language-reference/keywords/public)，其他物件的直接存取該欄位後可以修改它，未偵測到由擁有該欄位的物件。 使用[屬性](/dotnet/csharp/programming-guide/classes-and-structs/properties)封裝該欄位，您可以不允許直接存取欄位。  
  
 若要建立新的屬性，**封裝欄位**作業會變更您想要將封裝到欄位的存取修飾詞[私人](/dotnet/csharp/language-reference/keywords/private)，然後產生[取得](/dotnet/csharp/language-reference/keywords/get)和[設定](/dotnet/csharp/language-reference/keywords/set)該欄位的存取子。 在某些情況下，例如當欄位宣告為唯讀時，只會產生 `get` 存取子。  
  
 重構引擎使用新的屬性中指定的區域中的參考更新程式碼**更新參考**區段**封裝欄位** 對話方塊。  
  
### <a name="to-create-a-property-from-a-field"></a>從欄位建立屬性  
  
1.  建立名為 `EncapsulateFieldExample` 的主控台應用程式，再以下列程式碼取代 `Program`。  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  在[程式碼編輯器](../ide/writing-code-in-the-code-and-text-editor.md)，將游標放在宣告中，您想要將封裝的欄位名稱。 在下面的範例中，將游標放在 `width` 這個字上：  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  在**重構**功能表上，按一下 **封裝欄位**。  
  
     **封裝欄位** 對話方塊隨即出現。  
  
     您也可以輸入鍵盤快速鍵 CTRL + R、 E，以顯示**封裝欄位** 對話方塊。  
  
     您也可以以滑鼠右鍵按一下資料指標，指向 **重構**，然後按一下 **封裝欄位**顯示**封裝欄位** 對話方塊。  
  
4.  指定設定。  
  
5.  按下 ENTER，或按一下**確定** 按鈕。  
  
6.  如果您選取**預覽參考變更**選項，然後在**預覽參考變更**視窗隨即開啟。 按一下**套用** 按鈕。  
  
     您的原始程式檔中會顯示下列 `get` 和 `set` 存取子程式碼：  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     `Main` 方法中的程式碼也會更新為新的 `Width` 屬性名稱。  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## <a name="remarks"></a>備註  
 **封裝欄位**作業時才是可能的資料指標定位欄位宣告的同一行。  
  
 宣告多個欄位的宣告**封裝欄位**使用逗號做為欄位之間的界限，並啟始重構為最接近的資料指標的欄位和資料指標的同一行上。 您也可以在宣告中選取欄位名稱，藉此指定要進行封裝的欄位。  
  
 封裝欄位程式碼片段功能會將重構作業所產生的程式碼模型化。 程式碼片段是可以修改的。 如需詳細資訊，請參閱[程式碼片段](../ide/visual-csharp-code-snippets.md)。  
  
## <a name="see-also"></a>請參閱  
 [重構 (C#)](refactoring-csharp.md)   
 [Visual C# 程式碼片段](../ide/visual-csharp-code-snippets.md)