---
title: 對 JavaScript 和 TypeScript 進行單元測試
description: Visual Studio 支援使用適用於 Visual Studio 的 Node.js 工具進行 JavaScript 和 TypeScript 程式碼單元測試
ms.date: 03/18/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: dc44e39223fd252ae8c4130a1b358aa6af981119
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671495"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>在 Visual Studio 中對 JavaScript 和 TypeScript 進行單元測試

您可以使用一些較熱門的 JavaScript 架構在 Visual Studio 中撰寫和執行單元測試，而不需要切換到命令提示字元。 支援 Node.js 和 ASP.NET Core 專案。

支援的架構包括：
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* 匯出執行器 (此架構是適用於 Visual Studio 的 Node.js 工具所特定)

如 ASP.NET Core、JavaScript 或 TypeScript，請參閱 [撰寫 ASP.NET Core 的單元測試 ](#write-unit-tests-for-aspnet-core)。

如果不支援您最愛的架構，請參閱[新增單元測試架構的支援](#addingFramework)，以取得新增支援的資訊。

## <a name="write-unit-tests-in-a-nodejs-project"></a>在 Node.js 專案中撰寫單元測試

將單元測試新增至您的專案之前，請確定您打算使用的架構已安裝在本機專案中。 使用 [npm 套件安裝視窗](npm-package-management.md#npmInstallWindow)可以輕鬆地完成此動作。

將單元測試新增至專案的慣用方法是在專案中建立 *tests* 資料夾，並在專案屬性中將其設定為測試根目錄。 您還必須選取要使用的測試架構。

![設定測試根目錄和測試架構](../javascript/media/unit-test-project-properties.png)

您可以使用 [新增項目] 對話方塊，將簡單的空白測試新增至您的專案。 相同專案中同時支援 JavaScript 和 TypeScript。

![新增單元測試](../javascript/media/unit-test-add-new-item.png)

如果是 Mocha 單元測試，請使用下列程式碼：

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

如果您尚未在專案屬性中設定單元測試選項，則必須確定 [屬性] 視窗中的 [測試架構] 屬性已針對您的單元測試檔案設定為正確的測試架構。 這是由單元測試檔案範本自動完成。

![測試架構](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> 單元測試選項優先於個別檔案的設定。

開啟 test explorer 之後 (選擇 [**測試**  >  **Windows**  >  **test explorer**) ]，Visual Studio 探索並顯示測試。 如果一開始未顯示測試，則重建專案以重新整理清單。

![測試總管](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> 若為 TypeScript，請不要使用 `outdir` `outfile` *tsconfig.js* 中的或選項，因為 Test Explorer 將無法找到您的單元測試。

## <a name="run-tests-nodejs"></a> (Node.js) 執行測試

您可以在 Visual Studio 或從命令列執行測試。

### <a name="run-tests-in-visual-studio"></a>在 Visual Studio 中執行測試

::: moniker range=">=vs-2019"
您可以按一下 [測試總管] 中的 [全部執行] 連結來執行測試。 或者，您可以選取一或多個測試或群組、按一下滑鼠右鍵，然後從快捷方式功能表選取 [ **執行** ]，來執行測試。 測試會在背景中執行，而 [測試總管] 會自動更新並顯示結果。 此外，您也可以用滑鼠右鍵按一下並選取 [ **debug**]，來將選取的測試進行偵錯工具。
::: moniker-end
::: moniker range="vs-2017"
您可以按一下 [測試總管] 中的 [全部執行] 連結來執行測試。 或者，您可以選取一或多個測試或群組，按一下滑鼠右鍵，然後從捷徑功能表中選取 [執行選取的測試] 來執行測試。 測試會在背景中執行，而 [測試總管] 會自動更新並顯示結果。 此外，您也可以選取 [偵錯選取的測試]，對選取的測試進行偵錯。
::: moniker-end

針對 TypeScript，單元測試會針對產生的 JavaScript 程式碼執行。

> [!NOTE]
> 在大部分的 TypeScript 案例中，您可以藉由在 TypeScript 程式碼中設定中斷點、以滑鼠右鍵按一下測試瀏覽器中的測試，然後選擇 [ **debug**]，來進行單元測試的偵錯工具。 在更複雜的案例中，例如使用來源對應的某些案例中，您可能會遇到 TypeScript 程式碼中的中斷點。 若要解決此問題，請嘗試使用 `debugger` 關鍵字。

> [!NOTE]
> 我們目前不支援分析測試或程式碼涵蓋範圍。

### <a name="run-tests-from-the-command-line"></a>從命令列執行測試

您可以使用下列命令，從 [開發人員命令提示字元執行 Visual Studio](../ide/reference/command-prompt-powershell.md) 的測試：

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

此命令會顯示如下輸出：

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> 如果您收到錯誤，指出找不到 *vstest.console.exe*，請確定您已開啟開發人員命令提示字元，而不是一般的命令提示字元。

## <a name="write-unit-tests-for-aspnet-core"></a>撰寫 ASP.NET Core 的單元測試

1. 建立 ASP.NET Core 專案並加入 TypeScript 支援。

   如需範例專案，請參閱 [使用 TypeScript 建立 ASP.NET Core 應用程式](../javascript/tutorial-aspnet-with-typescript.md)。 針對單元測試支援，建議您從標準 ASP.NET Core 專案範本開始。

   使用 NuGet 套件來新增 TypeScript 支援，而不是 npm TypeScript 套件。

1. 安裝 NuGet 套件 [UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/)

1. 在方案總管中，以滑鼠右鍵按一下專案節點，然後選擇 **[卸載專案**]。

   *.Csproj* 檔案應該會在 Visual Studio 中開啟。

1. 將下列元素加入至專案中的 *.csproj* 檔案。 `PropertyGroup`

   這個範例會將 Mocha 指定為測試架構。 您可以改為指定 Jest、磁帶或 Jasmine。

   ```xml
   <PropertyGroup>
      ...
      <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
      <JavaScriptTestFramework>Mocha</JavaScriptTestFramework>
      <GenerateProgramFile>false</GenerateProgramFile>
   </PropertyGroup>
   ```

   `JavaScriptTestRoot`元素會指定您的單元測試將會在專案根目錄的 [*測試*] 資料夾中。

1. 在方案總管中，以滑鼠右鍵按一下專案節點，然後選擇 [ **重載專案**]。

1. 依照 [ASP.NET Core 專案](../javascript/npm-package-management.md#aspnet-core-projects)的 npm 套件管理文章中所述，新增 npm 支援。

   這需要安裝 Node.js 執行時間以支援 npm，並在專案根目錄中新增 *package.js* 。

1. 在 *package.js開啟*] 的 [相依性] 下，新增您想要的 npm 封裝。

   例如，針對 mocha，您可以使用下列程式：

   ```json
   "dependencies": {
     "mocha": "8.3.0",
   ```

   某些單元測試架構（例如 Jest）需要額外的 npm 套件。 針對 Jest，請使用下列 JSON：

   ```json
   "dependencies": {
     "jest": "26.6.3",
     "jest-editor-support": "28.1.0"
   ```

   >[!NOTE]
   > 在某些情況下，方案總管可能不會顯示 npm-節點，因為 [此處](https://github.com/aspnet/Tooling/issues/479)所述的已知問題。 如果您需要查看 [npm] 節點，您可以 (以滑鼠右鍵按一下專案並選擇 **[卸載專案** ]) ，然後重載專案，讓 npm-節點重新出現。

1. 新增要測試的程式碼。

   如果您使用以 [TypeScript 建立 ASP.NET Core 應用程式](tutorial-aspnet-with-typescript.md)中所述的範例，請在連結 *庫* 的結尾處新增下列程式碼，該檔案位於 *scripts* 資料夾中。

   ```typescript
   function getData(value) {
      if (value > 1) {
         return true;
      }
   }
    
   module.exports = getData;
   ```

   針對 TypeScript，單元測試會針對產生的 JavaScript 程式碼執行。

1. 將單元測試新增至專案根目錄中的 [ *測試* ] 資料夾。

   例如，您可以藉由選取符合測試架構的正確檔索引標籤（在此範例中為 Mocha 或 Jest），來使用下列程式碼。 此程式碼會測試稱為的函式 `getData` 。

   # <a name="mocha"></a>[摩卡](#tab/mocha)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
   var assert = require('assert');
    
   describe('Test Suite 1', function () {
      it('getData', function () {
         assert.ok(true, getData(2));
      })
   })
   ```

   # <a name="jest"></a>[開玩笑](#tab/jest)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
    
   test('should return true', () => {
      expect(getData(2)).toBe(true);
   });
   ```

1. 開啟 test explorer (選擇 [**測試**  >  **Windows**  >  **test explorer** ]) ，然後 Visual Studio 探索和顯示測試。 如果一開始未顯示測試，則重建專案以重新整理清單。

   ![Test Explorer 測試探索](../javascript/media/unit-tests-aspnet-core-discovery.png)

   > [!NOTE]
   > 針對 TypeScript，請勿使用 `outfile` *tsconfig.json* 的選項，因為 Test Explorer 將無法找到您的單元測試。 您可以使用 `outdir` 選項，但請確定設定檔（例如和） `package.json` 位於 `tsconfig.json` 專案根目錄中。

## <a name="run-tests-aspnet-core"></a>執行測試 (ASP.NET Core) 

::: moniker range=">=vs-2019"
您可以按一下 [測試總管] 中的 [全部執行] 連結來執行測試。 或者，您可以選取一或多個測試或群組、按一下滑鼠右鍵，然後從快捷方式功能表選取 [ **執行** ]，來執行測試。 測試會在背景中執行，而 [測試總管] 會自動更新並顯示結果。 此外，您也可以用滑鼠右鍵按一下並選取 [ **debug**]，來將選取的測試進行偵錯工具。
::: moniker-end
::: moniker range="vs-2017"
您可以按一下 [測試總管] 中的 [全部執行] 連結來執行測試。 或者，您可以選取一或多個測試或群組，按一下滑鼠右鍵，然後從捷徑功能表中選取 [執行選取的測試] 來執行測試。 測試會在背景中執行，而 [測試總管] 會自動更新並顯示結果。 此外，您也可以選取 [偵錯選取的測試]，對選取的測試進行偵錯。
::: moniker-end

針對 TypeScript，單元測試會針對產生的 JavaScript 程式碼執行。

![測試總管結果](../javascript/media/unit-tests-aspnet-core-run.png)

> [!NOTE]
> 在大部分的 TypeScript 案例中，您可以藉由在 TypeScript 程式碼中設定中斷點、以滑鼠右鍵按一下測試瀏覽器中的測試，然後選擇 [ **debug**]，來進行單元測試的偵錯工具。 在更複雜的案例中，例如使用來源對應的某些案例中，您可能會遇到 TypeScript 程式碼中的中斷點。 若要解決此問題，請嘗試使用 `debugger` 關鍵字。

> [!NOTE]
> 我們目前不支援分析測試或程式碼涵蓋範圍。

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>新增單元測試架構的支援

您可以使用 JavaScript 實作 探索和執行邏輯，以新增其他測試架構的支援。 您可以使用測試架構的名稱新增資料夾來完成此動作：

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

此資料夾必須包含具有相同名稱的 JavaScript 檔案，該檔案會匯出下列兩個函式：

* `find_tests`
* `run_tests`

如需 `find_tests` 和 `run_tests` 實作的良好範例，請參閱 Mocha 單元測試架構在下列內容的實作：

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

探索可用的測試架構會在 Visual Studio 啟動時發生。 如果在 Visual Studio 執行時新增架構，請重新啟動 Visual Studio 來偵測此架構。 不過，當您對實作進行變更時，不需要重新啟動。

## <a name="unit-tests-in-net-framework"></a>.NET Framework 中的單元測試

您不僅可以在 Node.js 和 ASP.NET Core 專案中撰寫單元測試。 當您將 TestFramework 和 TestRoot 屬性新增至任何 C# 或 Visual Basic 專案時，會列舉那些測試，且您可以使用 [測試總管] 視窗執行它們。

若要啟用此功能，請以滑鼠右鍵按一下 [方案總管] 中的專案節點、選擇 [卸載專案]，然後選擇 [編輯專案]。 然後在專案檔中，將下列兩個項目新增至屬性群組。

> [!IMPORTANT]
> 請確定您要新增項目的屬性群組不包含指定的條件。
> 這可能會導致非預期的行為。

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

接下來，將測試新增至您指定的測試根資料夾，它們便可在 [測試總管] 視窗中執行。 如果一開始未出現，您可能需要重新建置專案。

## <a name="unit-test-net-core-and-net-standard"></a>.NET Core 與 .NET Standard 中的單元測試

除了上述屬性之外，您還需要安裝 NuGet 套件 [UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) 並設定屬性：

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

某些測試架構可能需要額外的 npm 套件以進行測試偵測。 例如，jest 需要 jest 編輯器支援 npm 套件。 如有必要，請查看特定架構的檔。
