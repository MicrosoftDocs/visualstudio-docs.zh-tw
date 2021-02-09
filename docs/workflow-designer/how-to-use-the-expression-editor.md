---
title: 工作流程設計工具-如何：使用運算式編輯器
description: 瞭解運算式編輯器是一個工作流程設計工具控制項，可供您在許多工作流程活動中用來輸入和評估運算式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 192418439bc25e6ac1b969483c0c48a030caa024
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894071"
---
# <a name="how-to-use-the-expression-editor"></a>HOW TO：使用運算式編輯器

運算式編輯器是在許多工作流程活動中用來輸入和評估運算式的工作流程設計工具控制項。 運算式編輯器提供完整的 IDE 編輯經驗，包括 IntelliSense、顏色標示、ParamInfo、錯誤波浪線，還有其他功能。 編譯器會在輸入之後驗證運算式。 如果運算式無效，就會顯示錯誤圖示。 編輯器也可以開啟為 [ **運算式編輯器** ] 對話方塊。

運算式是常值，或是繫結到引數或屬性的 Visual Basic 程式碼。 它們包含值元素 (例如，變數、常數、常值、與作業結合的屬性) ，以產生新的值。 運算式會使用 VB.NET 語法撰寫，即使應用程式使用 C# 也是如此。 這表示大小寫並不重要，而是使用單一等號 ( "=" 而非 "= =" ) 來執行比較，布林運算子是 "and" 和 "or"，而不是 "&&" 和 "| |" 符號，而不會使用 **任何** 專案，而不是 **null**。 如需 Visual Basic 中的運算式和運算子以及某些範例的詳細資訊，請參閱 [Visual Basic 中的運算子和運算式](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100))。

**運算式編輯器** 的行為如下所示：

- 如果焦點不在 [運算式編輯器] 上，看起來就會像一般 TextBlock 控制項。

- 一旦焦點放在 [運算式編輯器] 上，其外觀與行為就會像 [運算式編輯器] 控制項。 在失去焦點之後，運算式編輯器會再次看起來像是一般的 TextBlock。

- 如果焦點放在重新裝載工作流程設計工具中的 [運算式編輯器] 上，則其行為表現會像 TextBlock。 如果在重新裝載工作流程設計工具中失去焦點，則 [運算式編輯器] 看起來又會像一般 TextBlock。

> [!NOTE]
> 運算式編輯器的 IntelliSense 只能在 Visual Studio 內使用。 在 Visual Studio 和重新裝載案例中，編譯器會在輸入後驗證運算式，而運算式編輯器會在運算式無效時顯示錯誤圖示。

## <a name="use-the-expression-editor"></a>使用運算式編輯器

1. 在 Visual Studio 中，開啟新的或現有的工作流程專案。

2. 將活動加入至工作流程，例如 <xref:System.Activities.Statements.Assign> 活動。

    > [!NOTE]
    > 許多工作流程活動都有運算式編輯器。 在變數設計工具、引數設計工具及動態引數設計工具中，也會出現運算式 TextBlock， 而 <xref:System.Activities.Statements.Assign> 活動會用來做為範例。

3. 在 <xref:System.Activities.Statements.Assign> 活動的活動設計工具中，按一下左方的運算式編輯器。

     灰色浮水印字串 **\<To>** 和 **\<Enter a VB Expression>** 是活動中運算式編輯器的預設文字字串 <xref:System.Activities.Statements.Assign> 。

4. 輸入您的運算式。 如果您輸入字串，請務必以引號包圍字串。 如果您選擇將運算式引數繫結至某個變數，請勿加引號。

     當您完成時，請選取 [運算式編輯器] 之外的區域或區域，將焦點移至設計工具的另一個部分。 切換焦點會導致編譯器驗證運算式，如先前所述。

     輸入或編輯運算式的另一個方法是，按一下屬性方格中屬性名稱旁邊的省略號。 選取省略號會以對話方塊的形式開啟 **運算式編輯器** 。

## <a name="see-also"></a>另請參閱

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
