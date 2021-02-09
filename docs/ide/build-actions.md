---
title: 檔案的建置動作
description: 瞭解 Visual Studio 專案中的所有檔案如何具有組建動作，而組建動作會控制編譯專案時，該檔案會發生什麼事。
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 86df6673608359dcc7158762c3ef9d86c184fff6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850477"
---
# <a name="build-actions"></a>建置動作

Visual Studio 專案中的所有檔案都有一個建置動作。 建置動作控制在編譯專案時，檔案會發生什麼事。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的建置動作](/visualstudio/mac/build-actions)。

## <a name="set-a-build-action"></a>設定建置動作

若要設定檔案的建置動作，請在 [方案總管] 中選取檔案並按下 **Alt**+**Enter**，在 [屬性] 視窗中開啟檔案的屬性。 或是在 [方案總管] 中，以滑鼠右鍵按一下檔案，並選擇 [屬性]。 在 [屬性] 視窗的 [進階] 區段下，使用 [建置動作] 旁的下拉式清單設定檔案的建置動作。

![Visual Studio 中的檔案建置動作](media/build-actions.png)

## <a name="build-action-values"></a>建置動作值

C# 和 Visual Basic 專案檔的一些較常見的建置動作如下：

|建置動作 | 專案類型 | Description |
|-|-|
| **AdditionalFiles** | C#、Visual Basic | 作為輸入傳遞至 C# 或 Visual Basic 編譯器的非來源文字檔。 此建置動作主要用來提供輸入給專案參考的[分析器](../code-quality/roslyn-analyzers-overview.md)，以便驗證程式碼品質。 如需詳細資訊，請參閱[使用其他檔案](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md)。|
| **ApplicationDefinition** | WPF | 定義您應用程式的檔案。 當您第一次建立專案時，這會是 *App.xaml*。 |
| **CodeAnalysisDictionary** | .NET | 程式碼分析用來進行拼寫檢查的自訂單字字典。 請參閱 [如何：自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **編譯** | 任意 | 該檔案會作為來源檔案傳遞至編譯器。|
| **內容** | .NET | 可以藉由呼叫 <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType> 來將標示為 [內容] 的檔案擷取為資料流。 若是 ASP.NET 專案，這些檔案將在網站部署時納入為網站的一部分。|
| **DesignData** | WPF | 用於 XAML ViewModel 檔案，以允許在設計階段檢視使用者控制項，同時搭配虛擬類型和範例資料。 |
| **DesignDataWithDesignTimeCreateable** | WPF | 如同 **DesignData**，但具有實際類型。  |
| **Embedded Resource** | .NET | 該檔案會作為要內嵌至組件的資源傳遞至編譯器。 您可以呼叫 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> 從組件讀取檔案。|
| **EntityDeploy** | .NET | 適用於指定 EF 成品之部署的 Entity Framework (EF) .edmx 檔案。 |
| **Fakes** | .NET | 用於 Microsoft Fakes 測試架構。 請參閱[使用 Microsoft Fakes 隔離測試中的程式碼](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **None** | 任意 | 該檔案在任何方面都不是組建的一部分。 這個值可以用於文件檔，例如「讀我」檔案。|
| **頁面** | WPF | 將 XAML 檔案編譯為二進位 baml 檔案，以便在執行時間更快載入。 |
| **Resource** | WPF | 指定要將檔案內嵌到副檔名為 *.g.resources* 的組件資訊清單資源檔中。 |
| **Shadow** | .NET | 用於包含已建置組件檔案名稱清單的 .accessor 檔案，每行一個。 針對清單上的每個組件，使用與原始檔案相同的名稱 `ClassName_Accessor` 來產生公用類別，但使用的是公用方法而不是私人方法。 用於單元測試。 |
| **啟動顯示畫面** | WPF | 指定當應用程式啟動時要在執行時間顯示的影像檔案。 |
| **XamlAppDef** | Windows Workflow Foundation | 指示組建使用內嵌的工作流程，將工作流程 XAML 檔案建置到組件中。 |

> [!NOTE]
> 由於可以針對特定專案類型定義其他建置動作，因此建置動作清單會取決於專案類型，而且可能會出現不在此清單中的值。

## <a name="see-also"></a>另請參閱

- [C # 編譯器選項](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic 編譯器選項](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [建置動作 (Visual Studio for Mac)](/visualstudio/mac/build-actions)
