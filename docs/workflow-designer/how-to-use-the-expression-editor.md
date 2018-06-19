---
title: 工作流程設計工具-如何： 使用運算式編輯器
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e14a967b9721973d8d545e10f58cab3c68b8e15
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976500"
---
# <a name="how-to-use-the-expression-editor"></a>HOW TO：使用運算式編輯器

運算式編輯器是 Windows 工作流程設計工具控制項做為輸入及評估這些運算式用於許多工作流程活動。 [運算式編輯器] 提供完整功能的 IDE 編輯經驗，包括 IntelliSense、顏色標示、ParamInfo、錯誤不規則曲線等等。 編譯器在運算式輸入之後會加以驗證。 如果運算式無效，就會顯示錯誤圖示。 編輯器也可做為開啟**運算式編輯器** 對話方塊。

 運算式是常值，或是繫結到引數或屬性的 Visual Basic 程式碼。 它們會包含與作業結合的項目 (例如變數、常數、常值、屬性)，以產生新的值。 運算式會使用 VB.NET 語法撰寫，即使應用程式使用 C# 也是如此。 這表示大寫並不重要，執行比較使用單一等於 （"="） 的符號，而不是 （"= ="）、 布林運算子是字 「 和 」 和 「 或 」 而不是符號 」 （& s) （& a)"和"&#124;&#124;"，和**做任何動作**而非**null**。 如需有關運算式和 Visual Basic 中的運算子以及一些範例，請參閱[運算子和 Visual Basic 中的運算式](http://go.microsoft.com/fwlink/?LinkId=186818)。

 **運算式編輯器**行為，如下所示：

-   如果焦點不在 [運算式編輯器] 上，看起來就會像一般 TextBlock 控制項。

-   一旦焦點放在 [運算式編輯器] 上，其外觀與行為就會像 [運算式編輯器] 控制項。 失去焦點之後，看起來又會像一般 TextBlock。

-   如果焦點放在重新裝載工作流程設計工具中的 [運算式編輯器] 上，則其行為表現會像 TextBlock。 如果在重新裝載工作流程設計工具中失去焦點，則 [運算式編輯器] 看起來又會像一般 TextBlock。

> [!NOTE]
> 只有在 Visual Studio 2010 內使用運算式編輯器的 IntelliSense。 在 Visual Studio 2010 和重新裝載的案例中，編譯器在運算式之後驗證其輸入，而且如果運算式無效，運算式編輯器會顯示錯誤圖示。

## <a name="use-the-expression-editor"></a>使用 「 運算式編輯器

1.  在 Visual Studio 2010 中，開啟新的或現有的工作流程專案。

2.  將活動加入至工作流程，例如 <xref:System.Activities.Statements.Assign> 活動。

    > [!NOTE]
    > 許多工作流程活動都有運算式編輯器。 在變數設計工具、引數設計工具及動態引數設計工具中，也會出現運算式 TextBlock， 而 <xref:System.Activities.Statements.Assign> 活動會用來做為範例。

3.  在 <xref:System.Activities.Statements.Assign> 活動的活動設計工具中，按一下左方的運算式編輯器。

     灰色浮水印字串**\<至 >** 和**\<輸入 VB 運算式 >** 是預設文字字串中的運算式編輯器<xref:System.Activities.Statements.Assign>活動。

4.  輸入您的運算式。 如果您輸入字串，請務必以引號包圍字串。 如果您選擇將運算式引數繫結至某個變數，請勿加引號。

     完成之後，請在 [運算式編輯器] 外選擇一個區域，將焦點移至設計工具的另一部分。 這樣會導致編譯器以前述方式驗證運算式。

     還有一種方法可以輸入/編輯運算式，就是在屬性方格中，按一下屬性名稱旁邊的省略符號。 這會開啟**運算式編輯器**身分 對話方塊。

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Presentation.View.ExpressionTextBox>