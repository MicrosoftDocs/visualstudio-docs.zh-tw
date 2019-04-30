---
title: 工作流程設計工具-如何：使用運算式編輯器
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce46f1db900aa5c37b49a1cc228290d7d99d29a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949535"
---
# <a name="how-to-use-the-expression-editor"></a>HOW TO：使用運算式編輯器

「 運算式編輯器 」 是用於許多工作流程活動，以輸入及評估運算式的工作流程設計工具控制項。 運算式編輯器提供了成熟的 IDE 編輯經驗，包括 IntelliSense、 顏色標示、 paraminfo、 錯誤波浪線，至於其他功能曲線等等。 輸入之前，編譯器會驗證運算式。 如果運算式無效，就會顯示錯誤圖示。 編輯器也可以開啟做**運算式編輯器** 對話方塊。

運算式是常值，或是繫結到引數或屬性的 Visual Basic 程式碼。 他們包含值的項目 （例如變數、 常數、 常值、 屬性） 會結合以產生新值的作業。 運算式會使用 VB.NET 語法撰寫，即使應用程式使用 C# 也是如此。 這表示大小寫並不重要，使用單一等號 」 來執行 「 比較登入 （"="而不是"= ="）、 布林運算子是字 「 和 」 和 「 或 」 而不是符號"& &"和"| |"，和**Nothing**用而不是**null**。 如需有關運算式和 Visual Basic 中的運算子以及一些範例，請參閱[運算子和 Visual Basic 中的運算式](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100))。

**運算式編輯器**行為，如下所示：

- 如果焦點不在 [運算式編輯器] 上，看起來就會像一般 TextBlock 控制項。

- 一旦焦點放在 [運算式編輯器] 上，其外觀與行為就會像 [運算式編輯器] 控制項。 失去焦點之後，運算式編輯器看起來像一般 TextBlock 一次。

- 如果焦點放在重新裝載工作流程設計工具中的 [運算式編輯器] 上，則其行為表現會像 TextBlock。 如果在重新裝載工作流程設計工具中失去焦點，則 [運算式編輯器] 看起來又會像一般 TextBlock。

> [!NOTE]
> 只有在 Visual Studio 內使用運算式編輯器的 IntelliSense。 在 Visual Studio 和重新裝載的案例中，編譯器在運算式之後驗證其輸入和運算式編輯器會顯示錯誤圖示，如果運算式無效。

## <a name="use-the-expression-editor"></a>使用運算式編輯器

1. 在 Visual Studio 中開啟新的或現有的工作流程專案。

2. 將活動加入至工作流程，例如 <xref:System.Activities.Statements.Assign> 活動。

    > [!NOTE]
    > 許多工作流程活動都有運算式編輯器。 在變數設計工具、引數設計工具及動態引數設計工具中，也會出現運算式 TextBlock， 而 <xref:System.Activities.Statements.Assign> 活動會用來做為範例。

3. 在 <xref:System.Activities.Statements.Assign> 活動的活動設計工具中，按一下左方的運算式編輯器。

     灰色浮水印字串**\<至 >** 並**\<輸入 VB 運算式 >** 是預設值的文字字串中的運算式編輯器<xref:System.Activities.Statements.Assign>活動。

4. 輸入您的運算式。 如果您輸入字串，請務必以引號包圍字串。 如果您選擇將運算式引數繫結至某個變數，請勿加引號。

     當您完成時，選取區域或區域外部運算式編輯器的焦點轉移到另一個組件的設計工具。 將焦點轉移可讓編譯器驗證運算式，如先前所述。

     輸入或編輯運算式的替代方式是按一下屬性方格中的屬性名稱旁邊的省略符號。 選取省略符號開啟**運算式編輯器**為對話方塊。

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Presentation.View.ExpressionTextBox>