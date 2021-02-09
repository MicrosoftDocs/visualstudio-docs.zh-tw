---
title: 程式碼片段
description: 瞭解程式碼片段，以及它們如何是可以插入程式碼檔案中的小型可重複使用程式碼區塊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 642bfe9fdccaa607476facb792120502437cb4b8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841961"
---
# <a name="code-snippets"></a>程式碼片段

程式碼片段是可重複使用之程式碼的小型區塊，可以使用右鍵功能表 (操作功能表) 命令或快速鍵的組合在程式碼檔案中插入。 其常包含常用的程式碼區塊，例如 `try-finally` 或 `if-else` 區塊，但可以用來插入整個類別或方法。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[程式碼片段 (Visual Studio for Mac)](/visualstudio/mac/snippets)。

程式碼片段可使用的語言包括 C#、C++、Visual Basic、XML 和 T-SQL 等等。 若要查看所有可用的語言已安裝程式碼片段，請從 [**工具**] 功能表開啟 [**程式碼片段管理員**] (或按下 **ctrl** + **K**、 **ctrl** + **B**) ，然後從頂端的下拉式功能表中選擇語言。

![[程式碼片段管理員] 對話方塊](media/code-snippets-manager.png)

程式碼片段可用下列一般方式存取：

- 在功能表列上，選擇 [**編輯**  >  **IntelliSense**  >  **插入程式碼片段**]

- 從程式碼編輯器的滑鼠右鍵功能表或操作功能表中，選擇 [代碼 **段**  >  **插入代碼** 段]

- 從鍵盤按下 **ctrl** + **K**、**ctrl** + **X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>擴充程式碼片段和範圍陳述式程式碼片段

在 Visual Studio 中，有兩種類型的程式碼片段：擴充程式碼片段，這會在指定的插入點加入，而且可能會取代程式碼片段捷徑，以及範圍陳述式程式碼片段 (僅限 C# 和 C++)，可在選取的程式碼區塊前後加入。

擴充程式碼片段的範例：在 C# 中，捷徑 tryf 可用來插入 try-finally 區塊：

```csharp
try
{

}
finally
{

}
```

若要插入此程式碼片段，請在滑鼠右鍵功能表中按一下 [ **插入程式碼片段** ]， ([程式碼] 視窗的操作功能表) ，然後按一下 [ **Visual c #**]，再輸入 `tryf` ，然後按 **tab** 鍵。或者，您可以輸入 `tryf` ，然後按 **tab** 鍵兩次。

範圍陳述式程式碼片段的範例：在 C++中，捷徑 `if` 可用作插入程式碼片段或範圍陳述式程式碼片段。 如果您選取一行程式碼 (例如 `return FALSE;`) ，然後選擇 [以範圍 **括住**]  >  ****，則會在該行周圍展開程式碼片段：

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>程式碼片段取代參數

程式碼片段可以包含取代參數，這些都是您必須取代的預留位置，以符合您要撰寫的精確程式碼。 在上述範例中，`true` 是取代參數，您必須以適當的條件取代。 在此程式碼片段中同一個取代參數的每個執行個體都要重複這項您所進行的取代。

例如，在 Visual Basic 中有會插入屬性的程式碼片段。 若要插入程式碼片段， 請  >  從 Visual Basic 程式碼檔案中的滑鼠右鍵功能表或操作功能表中選擇 [程式碼片段 **插入代碼** 段]。 然後，選擇程式 **代碼模式**  >  **屬性、程式、事件**  >  **定義屬性**。

![定義屬性的程式碼片段功能表](media/code-snippets-vb-property.png)

以下是已插入的程式碼：

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

如果您變更 `newPropertyValue` 為 `m_property`，則會變更每個 `newPropertyValue` 的執行個體。 如果您在屬性宣告中變更 `String` 為 `Int`，則已設定方法中的值也會變更為 `Int`。

## <a name="see-also"></a>另請參閱

- [逐步解說：建立程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)
- [如何：散發程式碼片段](../ide/how-to-distribute-code-snippets.md)
- [使用程式碼片段的最佳作法](../ide/best-practices-for-using-code-snippets.md)
- [疑難排解程式碼片段](../ide/troubleshooting-snippets.md)
- [C # 程式碼片段](../ide/visual-csharp-code-snippets.md)
- [C + + 程式碼片段](../ide/visual-cpp-code-snippets.md)
- [程式碼片段結構描述參考](../ide/code-snippets-schema-reference.md)
- [程式碼片段 (Visual Studio for Mac)](/visualstudio/mac/snippets)
