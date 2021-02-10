---
title: 使用 NuGet 編譯和建立 TypeScript 程式碼
description: 瞭解如何使用 NuGet 套件將 Typescript 支援新增至您的 Visual Studio 專案。
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 375f56d8a367c6d5cb090e10069b714b5a3843f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969538"
---
# <a name="compile-typescript-code-aspnet-core"></a>編譯 TypeScript 程式碼 (ASP.NET Core) 

您可以使用 TypeScript SDK （預設可在 Visual Studio 安裝程式中使用）或使用 NuGet 套件，將 TypeScript 支援新增至您的專案。 針對在 Visual Studio 2019 中開發的專案，我們建議您在不同的平臺和環境中使用 TypeScript NuGet 以提供更高的可攜性。

針對 ASP.NET Core 專案，NuGet 套件的常見用法之一是使用 .NET Core CLI 編譯 TypeScript。 除非您手動編輯專案檔以從 TypeScript SDK 安裝匯入組建目標，否則 NuGet 套件是使用 .NET Core CLI 命令（例如和）啟用 TypeScript 編譯的唯一方式 `dotnet build` `dotnet publish` 。 此外，對於與 ASP.NET Core 和 TypeScript 的 [MSBuild 整合](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) ，請選擇 npm 套件上的 NuGet 套件。

## <a name="add-typescript-support-with-nuget"></a>使用 NuGet 新增 TypeScript 支援

[Typescript NuGet 封裝](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) 會新增 typescript 支援。 將 TypeScript 3.2 或更高版本的 NuGet 套件安裝到您的專案中時，會在編輯器中載入對應版本的 TypeScript 語言服務。

如果已安裝 Visual Studio，則 Visual Studio 會自動挑選與其配套的 node.exe。 如果您未安裝 Node.js，建議您從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。

1. 在 Visual Studio 中開啟您的 ASP.NET Core 專案。

1. 在方案總管 (右窗格) 。 以滑鼠右鍵按一下專案節點，然後選擇 [ **管理 NuGet 套件**]。 在 [ **流覽** ] 索引標籤中，搜尋 [ **Microsoft**]，然後按一下右邊的 [ **安裝** ] 以安裝套件。

   ![新增 NuGet 套件](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio 會在方案總管的 [相依性 **]** 節點下新增 NuGet 套件。 下列封裝參考會加入您的 * .csproj 檔案中。

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. 以滑鼠右鍵按一下專案節點，然後選擇 [ **加入 > 新專案**]。 選擇 **TYPESCRIPT JSON 設定檔**，然後按一下 [ **新增**]。

   Visual Studio 將檔案 *tsconfig.js* 加入至專案根目錄。 您可以使用這個檔案來 [設定](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) TypeScript 編譯器的選項。

1. 開啟 *tsconfig.js開啟* ] 和 [更新]，以設定您想要的編譯器選項。

   以下是簡單 *tsconfig.json* file 的範例。

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   在此範例中：
   - *包含* 告訴編譯器哪裡可以找到 TypeScript ( *. a t) 檔案。
   - *outDir* 選項會指定 TypeScript 編譯器所轉換之一般 JavaScript 檔案的輸出檔案夾。
   - *sourceMap* 選項會指出編譯器是否會產生 *sourceMap* 檔案。

   先前的設定僅提供設定 TypeScript 的基本簡介。 如需其他選項的詳細資訊，請參閱 [ 上的tsconfig.js](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)。

### <a name="build-the-application"></a>建置應用程式

1. 在您的專案中新增 *typescript (、*) 或 typescript JSX (*tsx*) 檔案，然後加入 typescript 程式碼。 如需 TypeScript 的簡單範例，請使用下列程式：

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. 如果您使用較舊的非 SDK 樣式專案，請遵循 [移除預設匯入前移除預設匯入](#remove-default-imports) 的指示。

1. 選擇 [ **組建 > 組建方案**]。

   雖然應用程式會在您執行時自動建立，但我們想要查看在建立程式期間所發生的問題：

   如果您已產生來源對應，請開啟 *outDir* 選項中指定的資料夾，然後您會找到產生的 * .js 檔案 (s) 以及產生的 * js 對應檔 (s) 。

   需要來源對應檔案才能進行偵錯工具。

1. 如果您想要在每次儲存專案時編譯，請使用 *. tsconfig 中的 *compileOnSave* 選項。

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

如需使用 gulp 搭配工作執行器來建立應用程式的範例，請參閱 [ASP.NET Core 和 TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)。

如果您遇到 Visual Studio 使用的 Node.js 或協力廠商工具版本與您預期版本不同的問題，您可能需要設定 Visual Studio 的路徑以供使用。 選擇 [**工具**  >  **選項**]。 在 [**專案和方案**] 底下，選擇 [ **Web 套件管理**  >  **外部 web 工具**]。

### <a name="run-the-application"></a>執行應用程式

如需在編譯後執行應用程式的指示，請參閱 [建立您的第一個 Node.js 應用程式](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application)。

### <a name="nuget-package-structure-details"></a>NuGet 套件結構詳細資料

`Microsoft.TypeScript.MSBuild.nupkg` 包含兩個主要資料夾：

- *組建* 資料夾

    這兩個檔案位於此資料夾中。
    兩者都是進入點，分別適用于主要 TypeScript 目標檔案和 .props 檔案。

    1. *Microsoft TypeScript*

        此檔案會設定變數，以指定執行時間平臺，例如 *TypeScript.Tasks.dll* 的路徑，然後再從 [*工具*] 資料夾匯入 *Microsoft 的 TypeScript。*

    2. *.Props。*

        此檔案會從 *tools* 資料夾匯入 *.props* ，並設定屬性，指出已透過 NuGet 起始組建。

- *工具* 資料夾

    2.3 之前的套件版本僅包含一個 tsc 資料夾。 您可以在根層級上找到 *Microsoft 的 TypeScript. 目標* 和 *TypeScript.Tasks.dll* 。

    在封裝2.3 版和更新版本中，根層級包含 `Microsoft.TypeScript.targets` 和 `Microsoft.TypeScript.Default.props` 。 如需這些檔案的詳細資訊，請參閱 [MSBuild](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html)設定。

    此外，此資料夾包含三個子資料夾：

    1. *net45*

        此資料夾包含與其 `TypeScript.Tasks.dll` 相依的其他 dll。
        在 Windows 平臺上建立專案時，MSBuild 會使用此資料夾中的 Dll。

    2. *netstandard1.3*

        此資料夾包含的另一個版本，可在 `TypeScript.Tasks.dll` 非 Windows 電腦上建立專案時使用。

    3. *Tsc*

        此資料夾包含 `tsc.js` `tsserver.js` 和執行它們作為節點腳本所需的所有相依性檔案。

        > [!NOTE]
        > 如果 Visual Studio 已安裝，則會自動挑選隨附的 *node.exe* 。 否則，您必須在電腦上安裝 Node.js。

        3.1 之前的版本包含可 `tsc.exe` 執行編譯的可執行檔。 在3.1 版中，已移除這項功能，以使用 `node.exe` 。

### <a name="remove-default-imports"></a>移除預設匯入

在使用 [非 SDK 樣式格式](https://docs.microsoft.com/nuget/resources/check-project-format)的舊版 ASP.NET Core 專案中，您可能需要移除部分專案檔案元素。

如果您使用 NuGet 封裝來支援專案的 MSBuild，則專案檔不能匯入 `Microsoft.TypeScript.Default.props` 或 `Microsoft.TypeScript.targets` 。 這些檔案會由 NuGet 套件匯入，因此請個別包含這些檔案，可能會導致非預期的行為。

1. 以滑鼠右鍵按一下專案，然後選擇 **[卸載專案**]。

1. 以滑鼠右鍵按一下專案，然後選擇 [**編輯 \<*project file name*\>**]。

   專案檔案隨即開啟。

1. 移除 `Microsoft.TypeScript.Default.props` 和的參考 `Microsoft.TypeScript.targets` 。

   要移除的匯入結果如下所示：

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
