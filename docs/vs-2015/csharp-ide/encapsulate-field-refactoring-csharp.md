---
title: 封裝欄位重構 (C#) |Microsoft Docs
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
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35d7e03e30aa5301ee65f15a8591fbccd1de3fcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223537"
---
# <a name="encapsulate-field-refactoring-c"></a>封裝欄位重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**封裝欄位**重構作業可讓您快速建立屬性，從現有的欄位，然後順暢地以參考新的屬性更新您的程式碼。  
  
 當[欄位](http://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7)是[公用](http://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e)，其他物件至該欄位的直接存取，並可以修改它，未偵測到由擁有該欄位的物件。 藉由使用[屬性](http://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8)來封裝該欄位，您可以禁止直接存取的欄位。  
  
 若要建立新的屬性，**封裝欄位**作業會變更您想要封裝為欄位的存取修飾詞[私人](http://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)，然後產生[取得](http://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71)並[設定](http://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619)該欄位的存取子。 在某些情況下，例如當欄位宣告為唯讀時，只會產生 `get` 存取子。  
  
 重構引擎更新您的程式碼中指定的區域中新的屬性參考**更新參考**一節**封裝欄位** 對話方塊。  
  
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
  
2.  在 [程式碼編輯器](../ide/writing-code-in-the-code-and-text-editor.md)，將游標放在宣告中，您想要封裝的欄位名稱。 在下面的範例中，將游標放在 `width` 這個字上：  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  在 **重構**功能表上，按一下**封裝欄位**。  
  
     **封裝欄位** 對話方塊隨即出現。  
  
     您也可以輸入鍵盤快速鍵 CTRL + R、 E，以顯示**封裝欄位** 對話方塊。  
  
     您也可以以滑鼠右鍵按一下資料指標，指向**重構**，然後按一下**封裝欄位**以顯示**封裝欄位** 對話方塊。  
  
4.  指定設定。  
  
5.  按 ENTER 鍵，或按一下**確定** 按鈕。  
  
6.  如果您選取**預覽參考變更**選項，則**預覽參考變更**視窗隨即開啟。 按一下 [**套用**] 按鈕。  
  
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
 **封裝欄位**作業時，才可在游標位於欄位宣告的同一行時。  
  
 宣告會宣告多個欄位，如**封裝欄位**使用逗號做為欄位之間的界限，並啟始重構和與游標同一行上最接近游標的欄位。 您也可以在宣告中選取欄位名稱，藉此指定要進行封裝的欄位。  
  
 封裝欄位程式碼片段功能會將重構作業所產生的程式碼模型化。 程式碼片段是可以修改的。 如需詳細資訊，請參閱[程式碼片段](../ide/code-snippets.md)。  
  
## <a name="see-also"></a>另請參閱  
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)   
 [Visual C# 程式碼片段](../ide/visual-csharp-code-snippets.md)