---
title: "如何： 使用運算式編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: "13"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 55061da71038b3af38049a431db08fda6638144f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-expression-editor"></a>HOW TO：使用運算式編輯器
[運算式編輯器] 是 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 控制項，在許多工作流程活動中，會用來做為輸入及評估這些運算式的工具。 [運算式編輯器] 提供完整功能的 IDE 編輯經驗，包括 IntelliSense、顏色標示、ParamInfo、錯誤不規則曲線等等。 編譯器在運算式輸入之後會加以驗證。 如果運算式無效，就會顯示錯誤圖示。 編輯器也可做為開啟**運算式編輯器** 對話方塊。  
  
 運算式是常值，或是繫結到引數或屬性的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 程式碼。 它們會包含與作業結合的項目 (例如變數、常數、常值、屬性)，以產生新的值。 運算式會使用 VB.NET 語法撰寫，即使應用程式使用 C# 也是如此。 這表示大寫並不重要，執行比較使用單一等於 （"="） 的符號，而不是 （"= ="）、 布林運算子是字 「 和 」 和 「 或 」 而不是符號 」 （& s) （& a)"和"&#124; &#124;"，和**做任何動作**而非**null**。 如需有關運算式和運算子中的[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]和部分範例，請參閱[運算子和 Visual Basic 中的運算式](http://go.microsoft.com/fwlink/?LinkId=186818)。  
  
 **運算式編輯器**行為，如下所示：  
  
-   如果焦點不在 [運算式編輯器] 上，看起來就會像一般 TextBlock 控制項。  
  
-   一旦焦點放在 [運算式編輯器] 上，其外觀與行為就會像 [運算式編輯器] 控制項。 失去焦點之後，看起來又會像一般 TextBlock。  
  
-   如果焦點放在重新裝載工作流程設計工具中的 [運算式編輯器] 上，則其行為表現會像 TextBlock。 如果在重新裝載工作流程設計工具中失去焦點，則 [運算式編輯器] 看起來又會像一般 TextBlock。  
  
> [!NOTE]
>  [運算式編輯器] 的 IntelliSense 僅能在 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 內部使用。 在 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 與重新裝載的情況下，編譯器在運算式輸入之後會加以驗證，而如果運算式無效，運算式編輯器會顯示錯誤圖示。  
  
### <a name="using-the-expression-editor"></a>使用運算式編輯器  
  
1.  在 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 中，開啟新的或現有的工作流程專案。  
  
2.  將活動加入至工作流程，例如 <xref:System.Activities.Statements.Assign> 活動。  
  
    > [!NOTE]
    >  許多工作流程活動都有運算式編輯器。 在變數設計工具、引數設計工具及動態引數設計工具中，也會出現運算式 TextBlock， 而 <xref:System.Activities.Statements.Assign> 活動會用來做為範例。  
  
3.  在 <xref:System.Activities.Statements.Assign> 活動的活動設計工具中，按一下左方的運算式編輯器。  
  
     灰色浮水印字串**\<至 >**和**\<輸入 VB 運算式 >**是預設文字字串中的運算式編輯器<xref:System.Activities.Statements.Assign>活動。  
  
4.  輸入您的運算式。 如果您輸入字串，請務必以引號包圍字串。 如果您選擇將運算式引數繫結至某個變數，請勿加引號。  
  
     完成之後，請在 [運算式編輯器] 外選擇一個區域，將焦點移至設計工具的另一部分。 這樣會導致編譯器以前述方式驗證運算式。  
  
     還有一種方法可以輸入/編輯運算式，就是在屬性方格中，按一下屬性名稱旁邊的省略符號。 這會開啟**運算式編輯器**身分 對話方塊。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>