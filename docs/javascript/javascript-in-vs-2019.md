---
title: Visual Studio 2019 中的 JavaScript 和 TypeScript
description: 瞭解 Visual Studio 2019 如何使用 JavaScript 直接使用 JavaScript，以及使用 TypeScript 程式設計語言，為 JavaScript 開發提供豐富的支援。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 267bd8567b60a66bcf9d78c3aef8f02bbc942e0d
ms.sourcegitcommit: e12d6cdaeb37564f05361965db2ec8ad0d4f21ad
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025874"
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
* [TypeScript npm 封裝](https://www.npmjs.com/package/typescript)。 將 TypeScript 2.1 或更高版本的 npm 套件安裝到您的專案中時，會在編輯器中載入對應版本的 TypeScript 語言服務。
* TypeScript SDK 預設會在 Visual Studio 安裝程式中提供使用，以及從 [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395) 下載的獨立 SDK。

> [!TIP]
> 針對在 Visual Studio 2019 中開發的專案，我們建議您使用 TypeScript NuGet 或 TypeScript npm 套件，以在不同的平臺和環境之間獲得更高的可攜性。 如需詳細資訊，請參閱 [使用 NuGet 編譯 typescript 程式碼](../javascript/compile-typescript-code-nuget.md) ，並 [使用 tsc 編譯 typescript 程式碼](../javascript/compile-typescript-code-npm.md)。

## <a name="projects"></a>專案

Visual Studio 2019 中已不再支援 UWP JavaScript 應用程式。 您無法建立或開啟 JavaScript UWP 專案 (具有 *.jsproj* 副檔名的檔案)。 您可以使用我們有關[建立可在 Windows 上正常運作之 Progressive Web App (PWA)](/microsoft-edge/progressive-web-apps-chromium) 的文件。
