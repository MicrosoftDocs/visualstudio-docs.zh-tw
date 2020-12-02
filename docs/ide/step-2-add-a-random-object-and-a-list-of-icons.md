---
title: 步驟 2：新增隨機物件和圖示清單
description: 瞭解如何為遊戲建立一組相符的符號。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1018b390f6ebbf67fab88554aa85fe6a8ecec88d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480690"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>步驟 2：新增隨機物件和圖示清單

在這個步驟中，您會為遊戲建立一組配對符號。 每個符號會加入至表單上 TableLayoutPanel 中的兩個隨機儲存格。 若要這麼做，您必須使用兩個 `new` 陳述式來建立兩個物件。 第一個是 <xref:System.Random> 物件，就像是您用於數學測驗遊戲中的物件。 該物件在這個程式碼中會用來隨機選擇 TableLayoutPanel 中的儲存格。 第二個物件 (您可能不熟悉) 是一個 <xref:System.Collections.Generic.List%601> 物件，用來儲存隨機選擇的符號。

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>新增隨機物件和圖示清單

1. 在 [**方案總管** 中，如果您使用的是 c #，請選擇 [ *Form1.cs* ] *，如果您* 使用 Visual Basic，則選擇 [form1.vb]，然後在功能表列上選擇 [ **View**  >  **Code**]。 或者，您可以選擇 **F7** 鍵或按兩下方案總管中的 [Form1]。

     這會顯示 Form1 背後的程式碼模組。

2. 在現有的程式碼中，加入下列程式碼。

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > 您可以使用此頁面右上方的程式設計語言控制項來查看 c # 程式碼片段或 Visual Basic 程式碼片段。<br><br>![Docs.Microsoft.com 的程式設計語言控制項](../ide/media/docs-programming-language-control.png)

      如果您使用的是 c #，請務必將程式碼放在左大括弧之後，而緊接在類別宣告之後 (`public partial class Form1 : Form`) 。 如果使用的是 Visual Basic，請將程式碼放在類別宣告 (`Public Class Form1`) 的後面。

3. 新增清單物件時，請注意開啟的 **IntelliSense** 視窗。 以下是 c # 範例，但當您在 Visual Basic 中加入清單時，會出現類似的文字。

     ![顯示 Click 事件的 [屬性] 視窗](../ide/media/express_listintellisense.png)<br/>**_IntelliSense_* 視窗*

    > [!NOTE]
    > IntelliSense 視窗時只有在您手動輸入程式碼時才會出現。 如果您複製並貼上程式碼，它不會出現。

     如果您查看小型區段中的程式碼 (和備註)，就很容易了解。 您的程式可以使用清單物件來追蹤許多不同類型的項目。 清單可存放數字、true/false 值、文字或其他物件。 您的清單物件中甚至還可以包含其他的清單物件。 清單中的項目稱為元素，而每個清單只能保有一種類型的元素。 因此數字清單只可以保有數字，您無法將文字加入至此種清單。 同樣地，您無法將數字加入至 true/false 值的清單。

     當您使用 `List` 陳述式建立 `new` 物件時，必須指定您想在其中儲存的資料類型。 這就是為什麼在 **IntelliSense** 視窗頂端的工具提示會顯示清單中的項目類型。 此外， `List<string>` c # ) 中的 (以及 `List(Of String)` Visual Basic) 中的 (表示：它是 `List` 保存資料類型元素的物件 `string` 。 字串是程式用來存放文字的項目，該文字就是 **IntelliSense** 視窗右邊的工具提示所告訴您的內容。

4. 請考慮為什麼必須先建立暫存陣列 Visual Basic，但是在 c # 中，您可以使用一個語句來建立清單。 這是因為 c # 語言具有 *集合初始化運算式*，可準備接受值的清單。 在 Visual Basic 中，您可以使用集合初始設定式。 不過，為了與舊版的 Visual Basic 相容，建議您使用上述程式碼。

     當您使用含有 `new` 陳述式的集合初始設定式時，在建立新的清單物件之後，程式會以您在大括號內提供的資料來填入該物件。 在這種情況下，您會取得名為 icons 的字串清單，而且該清單將會初始化，使其包含十六個字串。 每一個字串都是單一字母，而且會對應到標籤中的圖示。 所以遊戲將會有一對驚嘆號、一對大寫字母 N、一對逗號等  (當這些字元設定為 Webdings 字型時，它們會顯示為符號，例如匯流排、自行車、編目程式等等。 ) 清單物件全部都有十六個字串，TableLayoutPanel 面板中的每個資料格都有一個。

    > [!NOTE]
    > 在 Visual Basic 中，您會得到相同的結果，但是字串會先放入暫存陣列中，然後該暫存陣列會轉換為清單物件。 陣列類似於清單，但有所不同，例如建立的陣列為固定大小。 清單可以視需要壓縮和擴展，在此程式中這點很重要。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程步驟，請參閱 [**步驟3：將隨機圖示指派給每個標籤**](../ide/step-3-assign-a-random-icon-to-each-label.md)。

- 若要回到上一個教學課程步驟，請參閱 [步驟1：建立專案並將資料表加入至您的表單](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)。
