---
title: 程式碼片段
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
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c06f9f7dc7e5a672e3fd5da3f3fc834fe223a783
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585414"
---
# <a name="code-snippets"></a>程式碼片段

程式碼片段是可重複使用之程式碼的小型區塊，可以使用右鍵功能表 (操作功能表) 命令或快速鍵的組合在程式碼檔案中插入。 其常包含常用的程式碼區塊，例如 `try-finally` 或 `if-else` 區塊，但可以用來插入整個類別或方法。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[程式碼片段 (Visual Studio for Mac)](/visualstudio/mac/snippets)。

程式碼片段可使用的語言包括 C#、C++、Visual Basic、XML 和 T-SQL 等等。 要查看語言的所有可用已安裝程式碼片段，請從 **"工具"** 功能表（或按**Ctrl**+**K、Ctrl** ** ** + **B）** 中打開**代碼程式碼片段管理器**，並從頂部的下拉式功能表中選擇該語言。

![[程式碼片段管理員] 對話方塊](media/code-snippets-manager.png)

程式碼片段可用下列一般方式存取：

- 在功能表列上，選擇 **"編輯** > **感知** > **插入片段"**

- 從代碼編輯器中的按右鍵或內容功能表中，選擇**程式碼片段** > **插入程式碼片段**

- 從鍵盤上，按**Ctrl**+**K**，**Ctrl**+**X**

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

您可以通過按一下代碼視窗的按右鍵功能表（內容功能表）中的**插入程式碼片段****，然後鍵入**，`tryf`然後按**Tab。** 或者，您可以鍵入`tryf`和按兩次**選項卡**。

範圍陳述式程式碼片段的範例：在 C++中，捷徑 `if` 可用作插入程式碼片段或範圍陳述式程式碼片段。 `return FALSE;`如果選擇一行代碼（例如），然後選擇 **"環繞與** > **"（如果**），程式碼片段將圍繞行展開：

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>程式碼片段取代參數

程式碼片段可以包含取代參數，這些都是您必須取代的預留位置，以符合您要撰寫的精確程式碼。 在上述範例中，`true` 是取代參數，您必須以適當的條件取代。 在此程式碼片段中同一個取代參數的每個執行個體都要重複這項您所進行的取代。

例如，在 Visual Basic 中有會插入屬性的程式碼片段。 要插入程式碼片段，請在視覺化基本代碼檔中從按右鍵或內容功能表中選擇 > **"程式碼片段插入程式碼片段**"。 **Snippet** 然後，選擇**代碼模式** > **屬性、過程、事件** > **定義屬性**。

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

- [演練：創建程式碼片段](../ide/walkthrough-creating-a-code-snippet.md)
- [如何：散發程式碼片段](../ide/how-to-distribute-code-snippets.md)
- [使用程式碼片段的最佳做法](../ide/best-practices-for-using-code-snippets.md)
- [故障排除程式碼片段](../ide/troubleshooting-snippets.md)
- [C# 程式碼片段](../ide/visual-csharp-code-snippets.md)
- [C++程式碼片段](../ide/visual-cpp-code-snippets.md)
- [程式碼片段架構引用](../ide/code-snippets-schema-reference.md)
- [程式碼片段 (Visual Studio for Mac)](/visualstudio/mac/snippets)
