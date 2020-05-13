---
title: 步驟 2：新增隨機物件和圖示清單
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f4731778ebb3acbdc3bb7d9b5827c1015541d98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579427"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>步驟 2：新增隨機物件和圖示清單

在這個步驟中，您會為遊戲建立一組配對符號。 每個符號會加入至表單上 TableLayoutPanel 中的兩個隨機儲存格。 若要這麼做，您必須使用兩個 `new` 陳述式來建立兩個物件。 第一個是 <xref:System.Random> 物件，就像是您用於數學測驗遊戲中的物件。 該物件在這個程式碼中會用來隨機選擇 TableLayoutPanel 中的儲存格。 第二個物件 (您可能不熟悉) 是一個 <xref:System.Collections.Generic.List%601> 物件，用來儲存隨機選擇的符號。

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>新增隨機物件和圖示清單

1. 在 **"解決方案資源管理器"** 中，如果使用的是 C#，請選擇*Form1.cs，* 或者如果您使用的是"視覺化基本"，請選擇 *"* 查看代碼"，然後在功能表列上選擇"**查看** > **代碼**"。 或者，您可以選擇 **F7** 鍵或按兩下方案總管**** 中的 [Form1]****。

     這會顯示 Form1 背後的程式碼模組。

2. 在現有的程式碼中，加入下列程式碼。

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > 使用此頁面右上角的程式設計語言控制項查看 C# 程式碼片段或 Visual Basic 程式碼片段。<br><br>![程式設計語言控制Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

      如果使用 C#，請確保將代碼放在開頭大括弧之後，並在類聲明 （）`public partial class Form1 : Form`之後。 如果使用的是 Visual Basic，請將程式碼放在類別宣告 (`Public Class Form1`) 的後面。

3. 新增清單物件時，請注意開啟的 **IntelliSense** 視窗。 下面是一個 C# 示例，但在 Visual Basic 中添加清單時會出現類似的文本。

     ![顯示 Click 事件的 [屬性] 視窗](../ide/media/express_listintellisense.png)<br/>***IntelliSense**視窗*

    > [!NOTE]
    > IntelliSense 視窗時只有在您手動輸入程式碼時才會出現。 如果您複製並貼上程式碼，它不會出現。

     如果您查看小型區段中的程式碼 (和備註)，就很容易了解。 您的程式可以使用清單物件來追蹤許多不同類型的項目。 清單可存放數字、true/false 值、文字或其他物件。 您的清單物件中甚至還可以包含其他的清單物件。 清單中的項目稱為元素，而每個清單只能保有一種類型的元素。 因此數字清單只可以保有數字，您無法將文字加入至此種清單。 同樣地，您無法將數字加入至 true/false 值的清單。

     當您使用 `List` 陳述式建立 `new` 物件時，必須指定您想在其中儲存的資料類型。 這就是為什麼在 **IntelliSense** 視窗頂端的工具提示會顯示清單中的項目類型。 此外`List<string>`，這就是（在 C#中）`List(Of String)`和（在 Visual Basic 中）的含義：它是`List`一個包含`string`資料類型元素的物件。 字串是程式用來存放文字的項目，該文字就是 **IntelliSense** 視窗右邊的工具提示所告訴您的內容。

4. 請考慮為什麼在 Visual Basic 中必須首先創建臨時陣列，但在 C# 中，可以使用一個語句創建清單。 這是因為 C# 語言具有*集合初始化器*，用於準備清單以接受值。 在 Visual Basic 中，您可以使用集合初始設定式。 不過，為了與舊版的 Visual Basic 相容，建議您使用上述程式碼。

     當您使用含有 `new` 陳述式的集合初始設定式時，在建立新的清單物件之後，程式會以您在大括號內提供的資料來填入該物件。 在這種情況下，您會取得名為 icons 的字串清單，而且該清單將會初始化，使其包含十六個字串。 每一個字串都是單一字母，而且會對應到標籤中的圖示。 所以遊戲將會有一對驚嘆號、一對大寫字母 N、一對逗號等 （當這些字元設置為 Webdings 字體時，它們將顯示為符號，如匯流排、自行車、蜘蛛等。清單物件將包含 16 個字串，在"表佈局面板"面板中每個儲存格一個字串。

    > [!NOTE]
    > 在 Visual Basic 中，您會得到相同的結果，但是字串會先放入暫存陣列中，然後該暫存陣列會轉換為清單物件。 陣列類似於清單，但有所不同，例如建立的陣列為固定大小。 清單可以視需要壓縮和擴展，在此程式中這點很重要。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 要轉到下一個教程步驟，請參閱[**步驟 3：為每個標籤分配一個隨機圖示**](../ide/step-3-assign-a-random-icon-to-each-label.md)。

- 要返回到前面的教程步驟，請參閱步驟[1：創建專案並將表添加到表單](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)中。
