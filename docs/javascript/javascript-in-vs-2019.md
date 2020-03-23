---
title: Visual Studio 2019 中的 JavaScript 和 TypeScript
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: df4630182e89dad08360794057bda856ff4d677b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549953"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>Visual Studio 2019 中的 JavaScript 和 TypeScript

## <a name="overview"></a>概觀

Visual Studio 2019 為 JavaScript 開發提供了豐富的支援，既可以直接使用 JavaScript，也可以使用 [TypeScript 程式設計語言](http://www.typescriptlang.org/)，這種語言是為了提供更有效率且更有趣的 JavaScript 開發體驗而開發的，尤其是在開發大規模的專案時。 您可以在 Visual Studio 中為許多應用程式類型和服務撰寫 JavaScript 或 TypeScript 程式碼。

## <a name="javascript-language-service"></a>JavaScript 語言服務

Visual Studio 2019 中的 JavaScript 體驗由提供 TypeScript 支援的相同引擎提供支援。 這為您提供了更好的功能支援、豐富功能以及現成的整合。

還原到傳統 JavaScript 語言服務的選項已無法使用。 使用者會有新的現成 JavaScript 語言服務可用。 新語言服務是僅以 TypeScript 語言服務為基礎，它是由靜態分析所提供。 這可讓我們為您提供更豐富的工具功能，因此您的 JavaScript 程式碼可受益於以型別定義為基礎的更豐富的 IntelliSense。 新的服務是輕量型服務，而且取用比傳統服務少的記憶體，為您提供更好的效能作為您的程式碼規模。 我們還改善了語言服務的效能，以處理較大型的專案。

## <a name="typescript-support"></a>TypeScript 支援

Visual Studio 2019 提供了幾種將 TypeScript 編譯整合到專案中的選項：

* [TypeScript NuGet 套件](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild)。 將 TypeScript 3.2 或更高版本的 NuGet 套件安裝到您的專案中時，會在編輯器中載入對應版本的 TypeScript 語言服務。
* [TypeScript npm 套件](https://www.npmjs.com/package/typescript)。 將 TypeScript 2.1 或更高版本的 npm 套件安裝到您的專案中時，會在編輯器中載入對應版本的 TypeScript 語言服務。
* TypeScript SDK 預設會在 Visual Studio 安裝程式中提供使用，以及從 [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017) 下載的獨立 SDK。

針對在 Visual Studio 2019 中開發的專案，我們建議您使用 TypeScript NuGet 和 npm 套件，以便在不同平台和環境中實現更高的可移植性。

NuGet 包的一個常見用法是使用 .NET 核心 CLI 編譯 TypeScript。 除非您手動編輯專案檔案以從 TypeScript SDK 安裝導入生成目標，否則 NuGet 包是使用 .NET Core CLI 命令（如 和`dotnet build``dotnet publish`） 啟用 TypeScript 編譯的唯一方法。

## <a name="remove-default-imports-aspnet-core-projects"></a>刪除預設導入（ASP.NET核心專案）

在使用非 SDK[樣式格式](https://docs.microsoft.com/nuget/resources/check-project-format)的舊專案中，可能需要刪除一些專案檔案元素。

如果您使用的 NuGet 包用於對專案的 MSBuild 支援，則專案檔案不得導入`Microsoft.TypeScript.Default.props`或`Microsoft.TypeScript.targets`。 檔由 NuGet 包導入，因此單獨包含這些檔可能會導致意外行為。

1. 按右鍵專案並選擇 **"卸載專案**"。

1. 按右鍵專案並選擇 **"編輯\<*專案檔案名*\>**"。

   專案檔案將打開。

1. 刪除 對`Microsoft.TypeScript.Default.props``Microsoft.TypeScript.targets`和 的引用。

   要刪除的導入如下所示：

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>專案

Visual Studio 2019 中已不再支援 UWP JavaScript 應用程式。 您無法建立或開啟 JavaScript UWP 專案 (具有 *.jsproj* 副檔名的檔案)。 您可以使用我們有關[建立可在 Windows 上正常運作之 Progressive Web App (PWA)](/microsoft-edge/progressive-web-apps/get-started) 的文件。
