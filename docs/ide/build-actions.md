---
title: 檔案的建置動作
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301983"
---
# <a name="build-actions"></a>建置動作

Visual Studio 專案中的所有檔案都有一個建置動作。 建置動作控制在編譯專案時，檔案會發生什麼事。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的建置動作](/visualstudio/mac/build-actions)。

## <a name="set-a-build-action"></a>設定建置動作

若要設定檔案的建置動作，請在 [方案總管]**** 中選取檔案並按下 **Alt**+**Enter**，在 [屬性]**** 視窗中開啟檔案的屬性。 或是在 [方案總管]**** 中，以滑鼠右鍵按一下檔案，並選擇 [屬性]****。 在 [屬性]**** 視窗的 [進階]**** 區段下，使用 [建置動作]**** 旁的下拉式清單設定檔案的建置動作。

![Visual Studio 中的檔案建置動作](media/build-actions.png)

## <a name="build-action-values"></a>建置動作值

C# 和 Visual Basic 專案檔的一些較常見的建置動作如下：

|建置動作 | 專案類型 | 描述 |
|-|-|
| **AdditionalFiles** | C#、Visual Basic | 作為輸入傳遞至 C# 或 Visual Basic 編譯器的非來源文字檔。 此建置動作主要用來提供輸入給專案參考的[分析器](../code-quality/roslyn-analyzers-overview.md)，以便驗證程式碼品質。 如需詳細資訊，請參閱[使用其他檔案](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md)。|
| **ApplicationDefinition** | WPF | 定義您應用程式的檔案。 當您第一次建立專案時，這會是 *App.xaml*。 |
| **CodeAnalysisDictionary** | .NET | 程式碼分析用來進行拼寫檢查的自訂單字字典。 [請參閱操作：自訂代碼分析詞典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **編譯** | 任意 | 該檔案會作為來源檔案傳遞至編譯器。|
| **內容** | .NET | 可以藉由呼叫 <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType> 來將標示為 [內容]**** 的檔案擷取為資料流。 若是 ASP.NET 專案，這些檔案將在網站部署時納入為網站的一部分。|
| **DesignData** | WPF | 用於 XAML ViewModel 檔案，以允許在設計階段檢視使用者控制項，同時搭配虛擬類型和範例資料。 |
| **DesignDataWithDesignTimeCreateable** | WPF | 如同 **DesignData**，但具有實際類型。  |
| **Embedded Resource** | .NET | 該檔案會作為要內嵌至組件的資源傳遞至編譯器。 您可以呼叫 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> 從組件讀取檔案。|
| **EntityDeploy** | .NET | 適用於指定 EF 成品之部署的 Entity Framework (EF) .edmx 檔案。 |
| **Fakes** | .NET | 用於 Microsoft Fakes 測試架構。 請參閱[使用 Microsoft Fakes 隔離測試中的程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **無** | 任意 | 該檔案在任何方面都不是組建的一部分。 這個值可以用於文件檔，例如「讀我」檔案。|
| **網頁** | WPF | 將 XAML 檔編譯為二進位 .baml 檔，以便在運行時更快地載入。 |
| **資源** | WPF | 指定要將檔案內嵌到副檔名為 *.g.resources* 的組件資訊清單資源檔中。 |
| **陰影** | .NET | 用於包含已建置組件檔案名稱清單的 .accessor 檔案，每行一個。 針對清單上的每個組件，使用與原始檔案相同的名稱 `ClassName_Accessor` 來產生公用類別，但使用的是公用方法而不是私人方法。 用於單元測試。 |
| **飛濺螢幕** | WPF | 指定在啟動應用時要在運行時顯示的影像檔。 |
| **XamlAppDef** | Windows Workflow Foundation | 指示組建使用內嵌的工作流程，將工作流程 XAML 檔案建置到組件中。 |

> [!NOTE]
> 由於可以針對特定專案類型定義其他建置動作，因此建置動作清單會取決於專案類型，而且可能會出現不在此清單中的值。

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic 編譯器選項](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [建置動作 (Visual Studio for Mac)](/visualstudio/mac/build-actions)
