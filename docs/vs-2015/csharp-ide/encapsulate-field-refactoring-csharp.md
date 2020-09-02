---
title: '封裝欄位重構 (c # ) |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667564"
---
# <a name="encapsulate-field-refactoring-c"></a>封裝欄位重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**封裝欄位**重構作業可讓您從現有的欄位快速建立屬性，然後使用新屬性的參考來順暢地更新您的程式碼。

 當 [欄位](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) 是 [公用](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e)的時，其他物件可以直接存取該欄位，而且可以修改它，因為擁有該欄位的物件未偵測到此欄位。 藉由使用 [屬性](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) 來封裝該欄位，您可以禁止直接存取欄位。

 若要建立新的屬性， **封裝欄位** 作業會將您要封裝之欄位的存取修飾詞變更為 [私](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)用，然後產生該欄位的 [get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) 和 [set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) 存取子。 在某些情況下，例如當欄位宣告為唯讀時，只會產生 `get` 存取子。

 重構引擎會在 [**封裝欄位**] 對話方塊的 [**更新參考**] 區段中指定的區域中，使用新屬性的參考來更新您的程式碼。

### <a name="to-create-a-property-from-a-field"></a>從欄位建立屬性

1. 建立名為 `EncapsulateFieldExample` 的主控台應用程式，再以下列程式碼取代 `Program`。

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

2. 在 [程式 [代碼編輯器](../ide/writing-code-in-the-code-and-text-editor.md)] 中，將游標放在宣告中，放在您要封裝的功能變數名稱上。 在下面的範例中，將游標放在 `width` 這個字上：

    ```csharp
    public int width, height;
    ```

3. 在 [ **重構** ] 功能表上，按一下 [ **封裝欄位**]。

     [ **封裝欄位** ] 對話方塊隨即出現。

     您也可以輸入鍵盤快速鍵 CTRL + R、E 來顯示 [ **封裝欄位** ] 對話方塊。

     您也可以用滑鼠右鍵按一下游標，指向 [ **重構**]，然後按一下 [ **封裝欄位** ]，以顯示 [ **封裝欄位** ] 對話方塊。

4. 指定設定。

5. 按 ENTER 鍵，或按一下 [ **確定]** 按鈕。

6. 如果您選取 [ **預覽參考變更** ] 選項，則 [ **預覽參考變更** ] 視窗隨即開啟。 按一下 [套用] 按鈕。

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
 只有當游標位於與欄位宣告相同的行上時，才可以進行 [ **封裝欄位** ] 作業。

 針對宣告多個欄位的宣告， **封裝欄位** 會使用逗號作為欄位之間的界限，並在最接近資料指標的欄位和游標所在的同一行上起始重構。 您也可以在宣告中選取欄位名稱，藉此指定要進行封裝的欄位。

 封裝欄位程式碼片段功能會將重構作業所產生的程式碼模型化。 程式碼片段是可以修改的。 如需詳細資訊，請參閱[程式碼片段](../ide/code-snippets.md)。

## <a name="see-also"></a>另請參閱
 [重構 (c # ) ](../csharp-ide/refactoring-csharp.md) [Visual c # 程式碼片段](../ide/visual-csharp-code-snippets.md)