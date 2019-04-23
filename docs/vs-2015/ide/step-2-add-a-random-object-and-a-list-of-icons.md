---
title: 步驟 2：新增隨機物件和圖示清單 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e71debec563aa54d5232686b599f286d147b1a7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073003"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>步驟 2：新增隨機物件及圖示的清單
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在這個步驟中，您會為遊戲建立一組配對符號。 每個符號會加入至表單上 TableLayoutPanel 中的兩個隨機儲存格。 若要這麼做，您必須使用兩個 `new` 陳述式來建立兩個物件。 第一個是 `Random` 物件，就像是您用於數學測驗遊戲中的物件。 該物件在這個程式碼中會用來隨機選擇 TableLayoutPanel 中的儲存格。 第二個物件 (您可能不熟悉) 是一個 `List` 物件，用來儲存隨機選擇的符號。  
  
### <a name="to-add-a-random-object-and-a-list-of-icons"></a>若要加入隨機物件和圖示清單  
  
1. 在方案總管中選擇 [Form1.cs] (如果使用的是 Visual C#) 或 [Form1.vb] (如果使用的是 Visual Basic)，然後在功能表列上，選擇 [檢視]、[程式碼]。 或者，您可以選擇 **F7** 鍵或按兩下方案總管中的 [Form1]。  
  
     這會顯示 Form1 背後的程式碼模組。  
  
2. 在現有的程式碼中，加入下列程式碼。  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#1)]  
  
     如果是使用 Visual C#，請務必將程式碼放在左大括號之後，而正好在類別宣告 (`public partial class Form1 : Form`) 的後面。 如果使用的是 Visual Basic，請將程式碼放在類別宣告 (`Public Class Form1`) 的後面。  
  
3. 新增 `List` 物件時，請注意開啟的 **IntelliSense** 視窗。 以下是 Visual C# 範例，不過，類似的文字會在您於 Visual Basic 中加入清單時顯示。  
  
     ![顯示 Click 事件的 [屬性] 視窗](../ide/media/express-listintellisense.png "Express_ListIntellisense")  
IntelliSense 視窗  
  
    > [!NOTE]
    >  IntelliSense 視窗時只有在您手動輸入程式碼時才會出現。 如果您複製並貼上程式碼，它不會出現。  
  
     如果您查看小型區段中的程式碼 (和備註)，就很容易了解。 您的程式可以使用 `List` 物件來追蹤許多不同類型的項目。 清單可存放數字、true/false 值、文字或其他物件。 您甚至可以擁有保有其他 `List` 物件的 `List` 物件。 清單中的項目稱為「項目」，而每個清單只能保有一種類型的項目。 因此數字清單只可以保有數字，您無法將文字加入至此種清單。 同樣地，您無法將數字加入至 true/false 值的清單。  
  
     當您使用 `List` 陳述式建立 `new` 物件時，必須指定您想在其中儲存的資料類型。 這就是為什麼在 **IntelliSense** 視窗頂端的工具提示會顯示清單中的項目類型。 而且，這就是 `List<string>` (在 Visual C# 中) 和 `List(Of String)` (在 Visual Basic 中) 的含意：它是一個保有 `string` 資料類型項目的 `List` 物件。 字串是程式用來存放文字的項目，該文字就是 **IntelliSense** 視窗右邊的工具提示所告訴您的內容。  
  
4. 請考慮為何在 Visual Basic 中必須先建立暫存陣列，但是在 Visual C# 中，您可以使用一個陳述式建立清單。 這是因為 Visual C# 語言具有「集合初始設定式」，用於準備接受值的清單。 在 Visual Basic 中，您可以使用集合初始設定式。 不過，為了與舊版的 Visual Basic 相容，建議您使用上述程式碼。  
  
     當您使用含有 `new` 陳述式的集合初始設定式時，在建立新的 `List` 物件之後，程式會以您在大括號內提供的資料來填入該物件。 在這種情況下，您會取得名為**圖示**的字串清單，而且該清單將會初始化，使其包含十六個字串。 每一個字串都是單一字母，而且會對應到標籤中的圖示。 所以遊戲將會有一對驚嘆號、一對大寫字母 N、一對逗號等 (這些字元會設定為 Webdings 字型，會顯示為符號，例如公車、腳踏車、蜘蛛等，依此類推)。您的 `List` 物件總共會有十六個字串，每一個字串適用於 TableLayoutPanel 面板中的每一個儲存格。  
  
    > [!NOTE]
    >  在 Visual Basic 中，您會得到相同的結果，但是字串會先放入暫存陣列中，然後該暫存陣列會轉換為 `List` 物件。 陣列類似於清單，但有所不同，例如建立的陣列為固定大小。 清單可以視需要壓縮和擴展，在此程式中這點很重要。  
  
### <a name="to-continue-or-review"></a>若要繼續或檢視  
  
- 若要前往下一個教學課程步驟，請參閱[步驟 3：將隨機圖示指派給每個標籤](../ide/step-3-assign-a-random-icon-to-each-label.md)。  
  
- 若要回到上一個教學課程步驟，請參閱[步驟 1：建立專案，並將資料表加入至您的表單](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)。
