---
title: 檔案的建置動作
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45a0e4822bc9b6d20bd2cf63d664e6cba97c77bf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951296"
---
# <a name="build-actions"></a>建置動作

Visual Studio 專案中的所有檔案都有一個建置動作。 建置動作控制在編譯專案時，檔案會發生什麼事。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的建置動作](/visualstudio/mac/build-actions)。

## <a name="set-a-build-action"></a>設定建置動作

若要設定檔案的建置動作，請在 [方案總管] 中選取檔案並按下 **Alt**+**Enter**，在 [屬性] 視窗中開啟檔案的屬性。 或是在 [方案總管] 中，以滑鼠右鍵按一下檔案，並選擇 [屬性]。 在 [屬性] 視窗的 [進階] 區段下，使用 [建置動作] 旁的下拉式清單設定檔案的建置動作。

![Visual Studio 中的檔案建置動作](media/build-actions.png)

## <a name="build-action-values"></a>建置動作值

C# 和 Visual Basic 專案檔的部分建置動作如下：

* **無** - 檔案在任何方面都不是建置的一部分。 這個值可以用於文件檔，例如「讀我」檔案。
* **編譯** - 檔案會當作來源檔案傳遞至編譯器。
* **內容** - 標示為 [內容] 的檔案可以藉由呼叫 <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType> 來擷取為資料流。 若是 ASP.NET 專案，這些檔案將在網站部署時納入為網站的一部分。
* **EmbeddedResource** - 檔案會當作要在組件中內嵌的資源傳遞至編譯器。 您可以呼叫 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> 從組件讀取檔案。
* **AdditionalFiles** - 當作輸入傳遞至 C# 或 Visual Basic 編譯器的非原始程式文字檔。 此建置動作主要用來提供輸入給專案參考的[分析器](../code-quality/roslyn-analyzers-overview.md)，以便驗證程式碼品質。 如需詳細資訊，請參閱[使用其他檔案](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md)。

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic 編譯器選項](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [建置動作 (Visual Studio for Mac)](/visualstudio/mac/build-actions)