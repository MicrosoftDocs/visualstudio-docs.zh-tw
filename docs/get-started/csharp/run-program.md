---
title: 如何運行 C# 程式
description: 有關如何在視覺工作室運行 C# 程式的初學者指南。
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ffe52fc2bf7d05084307b4d972e45f4b1d2acdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "76924613"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>如何：在視覺工作室運行 C# 程式

運行程式所需的操作取決於您從什麼開始、程式、應用或服務的類型，以及是否要在調試器下運行它。 在最簡單的情況下，當您在 Visual Studio 中打開專案時，請按**Ctrl**+**F5（****無需調試即可開始**）或**F5（****從調試開始**）或按主 Visual Studio 工具列上的綠色箭頭（**開始按鈕**）來生成並運行該專案。

![顯示開始按鈕的螢幕截圖](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>從專案開始

如果您有一個 C# 專案 *（.csproj*檔），則可以運行它（如果它是可運行的程式）。 如果專案包含包含方法`Main`的 C# 檔，並且其輸出是可執行檔 （EXE），則如果生成成功，則最有可能運行該檔。

如果在 Visual Studio 中的專案中已經擁有程式的代碼，請打開該專案。 要打開專案，請按兩下或點擊 Windows 檔資源管理器中的 *.csproj*或從 Visual Studio，選擇 **"打開專案**"，流覽以查找專案 *（.csproj）* 檔，然後選擇專案檔案。

專案在 Visual Studio 中載入後，按**Ctrl**+**F5（****無需調試即可啟動**）或使用 Visual Studio 工具列上的綠色 **"開始"** 按鈕運行程式。  如果有多個專案，則必須將具有`Main`該方法的專案設置為啟動專案。 要設置啟動專案，請按右鍵專案節點，然後選擇 **"設置為啟動專案**"。

![設置啟動專案](media/set-as-startup-project.png)

視覺化工作室嘗試構建和運行專案。  如果存在建置錯誤，請參閱 **"輸出"** 視窗中的生成輸出和**錯誤清單**視窗中的錯誤。

如果生成成功，應用以適合專案類型的方式運行。 主控台應用在終端視窗中運行，Windows 桌面應用在新視窗中啟動，Web 應用在瀏覽器中啟動（由 IIS Express 託管），等等。

## <a name="starting-from-code"></a>從代碼開始

如果要從代碼清單、代碼檔或少量檔開始，請先確保要運行的代碼來自受信任的源，並且是可運行的程式。 如果它有一個`Main`方法，它很可能被用作可運行的程式，您可以使用主控台應用範本創建專案，在 Visual Studio 中使用它。

### <a name="code-listing-for-a-single-file"></a>單個檔的代碼清單

啟動 Visual Studio，打開空的 C# 主控台專案，選擇專案中已包含的 .cs 檔中的所有代碼，然後將其刪除。 然後，將代碼的內容粘貼到 .cs 檔中。 粘貼代碼時，請覆蓋或刪除以前存在的代碼。 重命名檔以匹配原始代碼。

### <a name="code-listings-for-a-few-files"></a>幾個檔的代碼清單

啟動 Visual Studio，打開空的 C# 主控台專案，選擇專案中已包含的 .cs 檔中的所有代碼，然後將其刪除。 然後，將第一個代碼檔的內容粘貼到 .cs 檔中。 重命名檔以匹配原始代碼。 

對於第二個檔，按右鍵**解決方案資源管理器**中的專案節點以打開專案的快捷方式功能表，然後選擇 **"添加>現有專案**（或使用鍵組合**Shift**+**Alt**+**A），** 然後選擇代碼檔。

### <a name="multiple-files-on-disk"></a>磁片上的多個檔

1. 創建適當類型的新專案（如果您不確定，請使用 C#**主控台應用**）。

2. 按右鍵專案節點，se**添加** > **現有專案**以選擇檔並將其導入專案。  

### <a name="starting-from-a-folder"></a>從資料夾開始

當您使用包含許多檔的資料夾時，首先查看是否有專案或解決方案。  如果程式是使用 Visual Studio 創建的，則應查找專案檔案或解決方案檔。 查找具有 *.csproj*副檔名或 .sln 副檔名的檔，並在 Windows 檔資源管理器中按兩下其中一個在 Visual Studio 中打開這些檔。 請參閱[從視覺化工作室解決方案或專案開始](#starting-from-a-project)。

如果您沒有專案檔案（例如代碼是在另一個開發環境中開發的，則使用 Visual Studio 中的**Open 資料夾**方法打開頂級資料夾。 請參閱[開發沒有專案或解決方案的代碼](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

## <a name="starting-from-a-github-or-azure-devops-repo"></a>從 GitHub 或 Azure 開發人員計畫存儲庫開始

如果要運行的代碼在 GitHub 或 Azure DevOps 存儲庫中，則可以使用 Visual Studio 直接從存儲庫打開專案。 請參閱[從回購中打開專案](../tutorial-open-project-from-repo.md)。

## <a name="run-the-program"></a>執行程式

要啟動程式，請按主 Visual Studio 工具列上的綠色箭頭（**開始**按鈕），或按**F5**或**Ctrl**+**F5**來運行該程式。 使用 **"開始"** 按鈕時，它將在調試器下運行。  Visual Studio 嘗試在專案中生成代碼並運行它。  如果成功，太好了！ 但是，如果沒有，繼續閱讀一些關於如何成功構建它的想法。

## <a name="troubleshooting"></a>疑難排解

您的代碼可能有錯誤，但如果代碼正確，但僅取決於其他程式集或 NuGet 包，或者編寫到針對不同版本的 .NET，則可能可以輕鬆修復它。

### <a name="add-references"></a>新增參考

要正確生成，代碼必須正確，並且已設置對庫或其他依賴項的正確引用。 您可以查看紅色波浪線和**錯誤清單**，查看程式是否有任何錯誤，甚至在編譯和運行它之前也是如此。 如果您看到與未解析名稱相關的錯誤，則可能需要增加參考或 using 指令，或者兩者兼而有之。 如果代碼引用任何程式集或 NuGet 包，則需要在專案中添加這些引用。

Visual Studio 會嘗試説明您識別缺少的引用。 當名稱未解析時，編輯器中將顯示一個燈泡圖示。 如果按一下燈泡，可以看到有關如何解決此問題的一些建議。 修復方法可能是：

- 添加 using 指令
- 添加對程式集的引用，或
- 安裝 NuGet 包。

#### <a name="missing-using-directive"></a>缺少使用指令

例如，在下面的螢幕中，您可以選擇添加到`using System;`代碼檔的開頭以解析未解析的名稱： `Console`

![用於添加使用指令的燈泡螢幕截圖](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>缺少程式集引用

.NET 引用可以以程式集或 NuGet 包的形式進行。 通常，如果您找到原始程式碼，發行者或作者將解釋需要哪些程式集以及代碼所依賴的包。 要手動添加對專案的引用，請按右鍵**解決方案資源管理器**中的 **"引用"** 節點，選擇 **"增加參考**"並查找所需的程式集。

![添加參考功能表的螢幕截圖](media/add-reference.png)

您可以使用[引用管理器，按照"添加或刪除引用](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)"中的說明查找程式集並增加參考。

#### <a name="missing-nuget-package"></a>缺少 NuGet 包

如果 Visual Studio 檢測到缺少的 NuGet 包，則會出現一個燈泡，並為您提供安裝它的選項：

![要安裝套裝軟體的燈泡螢幕截圖](media/lightbulb-add-package.png)

如果這不能解決問題，並且 Visual Studio 找不到包，請嘗試連線搜索它。 請參閱[在視覺化工作室中安裝和使用 NuGet 包](/nuget/quickstart/install-and-use-a-package-in-visual-studio)。

## <a name="use-the-right-version-of-net"></a>使用正確的版本 .NET

由於 .NET 框架的不同版本具有某種程度的向後相容性，因此較新的框架可能會運行為舊框架編寫的代碼，而無需進行任何修改。 但是，有時您需要針對特定框架。 如果尚未安裝 .NET 框架或 .NET Core 的特定版本，則可能需要安裝該版本。 請參閱[修改視覺工作室](../../install/modify-visual-studio.md)。

要更改目標框架，請參閱[更改目標框架](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version)。 有關詳細資訊，請參閱故障排除[.NET 框架定位錯誤](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

## <a name="next-steps"></a>後續步驟

通過閱讀["歡迎訪問視覺工作室 IDE"](../visual-studio-ide.md)來探索視覺工作室開發環境。

## <a name="see-also"></a>另請參閱

[建立您的第一個 C# 應用程式](tutorial-console.md)
