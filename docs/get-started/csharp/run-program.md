---
title: 如何執行程式 (C#)
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
ms.openlocfilehash: ee28bde6de10006ccfdc5175cca629ad9d1590d0
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649641"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>如何:在視覺工作室運行 C# 程式

執行程式所需的操作取決於您從什麼開始、程式、應用或服務的類型,以及是否要在調試器下運行它。 在最簡單的情況下,當您在 Visual Studio 中打開專案時,請按**Ctrl**+**F5(****無需調試即可開始**)或**F5(****從調試開始**)或按主 Visual Studio 工具列上的綠色箭頭(**開始按鈕**)來生成並運行該專案。

![顯示開始按鍵的螢幕擷取](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>從項目開始

如果您有一個 C# 專案 *(.csproj*檔),則可以執行它(如果它是可執行的程式)。 如果專案包含包含方法`Main`的 C# 檔,並且其輸出是可執行檔 (EXE),則如果生成成功,則最有可能運行該檔。

如果在 Visual Studio 中的項目中已經擁有程式的代碼,請打開該專案。 要打開專案,請雙擊或點擊 Windows 檔案資源管理員中的 *.csproj*或從 Visual Studio,選擇 **「打開專案**」,流覽以查找專案 *(.csproj)* 檔案,然後選擇專案檔。

專案在 Visual Studio 中載入後,按**Ctrl**+**F5(****無需除錯即可啟動**)或使用 Visual Studio 工具列上的綠色 **「開始」** 按鈕執行程式。  如果有多個專案,則必須將具有`Main`該方法的專案設置為啟動專案。 要設置啟動專案,請右鍵單擊專案節點,然後選擇 **「設置為啟動專案**」。

![設定啟動項目](media/set-as-startup-project.png)

可視化工作室嘗試構建和運行專案。  如果存在產生錯誤,請參閱 **「輸出」** 視窗中的產生輸出和**錯誤列表**視窗中的錯誤。

如果生成成功,應用以適合項目類型的方式運行。 控制台應用在終端視窗中運行,Windows 桌面應用在新視窗中啟動,Web 應用在瀏覽器中啟動(由 IIS Express 託管),等等。

## <a name="starting-from-code"></a>從代碼開始

如果要從代碼清單、代碼檔或少量檔開始,請先確保要運行的代碼來自受信任的源,並且是可運行的程式。 如果它有一個`Main`方法,它很可能被用作可運行的程式,您可以使用主控台應用範本創建專案,在 Visual Studio 中使用它。

### <a name="code-listing-for-a-single-file"></a>單一檔案的代碼清單

啟動 Visual Studio,打開空的 C# 主控台項目,選擇專案中已包含的 .cs 檔中的所有代碼,然後將其刪除。 然後,將代碼的內容粘貼到 .cs 檔中。 貼上代碼時,請覆蓋或刪除以前存在的代碼。 重新命名檔以符合原始碼。

### <a name="code-listings-for-a-few-files"></a>幾個檔案的代碼清單

啟動 Visual Studio,打開空的 C# 主控台項目,選擇專案中已包含的 .cs 檔中的所有代碼,然後將其刪除。 然後,將第一個代碼文件的內容粘貼到 .cs 檔中。 重新命名檔以符合原始碼。 

對於第二個檔,右鍵單擊**解決方案資源管理器**中的專案節點以打開專案的快捷方式功能表,然後選擇 **「新增>現有專案**(或使用鍵群組**Shift**+**Alt**+**A),** 然後選擇代碼檔。

### <a name="multiple-files-on-disk"></a>磁碟上的多個檔案

1. 建立適當類型的新專案(如果您不確定,請使用 C#**控制台應用**)。

2. 右鍵單擊專案節點,se**添加** > **現有專案**以選擇檔並將其導入專案。  

### <a name="starting-from-a-folder"></a>從資料夾開始

當您使用包含許多檔的資料夾時,首先查看是否有專案或解決方案。  如果程式是使用 Visual Studio 創建的,則應查找專案檔或解決方案檔。 尋找具有 *.csproj*副檔名或 .sln 副檔名的檔案,並在 Windows 檔案資源管理器中按兩下其中一個在 Visual Studio 中打開這些檔。 請參考[從視覺化工作室解決方案或項目開始](#starting-from-a-project)。

如果您沒有專案檔(例如代碼是在另一個開發環境中開發的,則使用 Visual Studio 中的**Open 資料夾**方法打開頂級資料夾。 請參考[開發沒有項目或解決方案的代碼](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

## <a name="starting-from-a-github-or-azure-devops-repo"></a>從 GitHub 或 Azure 開發人員計劃儲存函式庫開始

如果要運行的代碼在 GitHub 或 Azure DevOps 儲存庫中,則可以使用 Visual Studio 直接從儲存庫打開專案。 請參考[從回購中開啟項目](../tutorial-open-project-from-repo.md)。

## <a name="run-the-program"></a>執行程式

要啟動程式,請按主 Visual Studio 工具列上的綠色箭頭(**開始**按鈕),或按**F5**或**Ctrl**+**F5**來執行該程式。 使用 **「開始」** 按鈕時,它將在除錯器下運行。  Visual Studio 嘗試在專案中生成代碼並運行它。  如果成功,太好了! 但是,如果沒有,繼續閱讀一些關於如何成功構建它的想法。

## <a name="troubleshooting"></a>疑難排解

您的代碼可能有錯誤,但如果代碼正確,但僅取決於其他程式集或 NuGet 包,或者編寫到針對不同版本的 .NET,則可能可以輕鬆修復它。

### <a name="add-references"></a>新增參考

要正確生成,代碼必須正確,並且已設置對庫或其他依賴項的正確引用。 您可以查看紅色波浪線和**錯誤列表**,查看程式是否有任何錯誤,甚至在編譯和運行它之前也是如此。 如果您看到與未解析名稱相關的錯誤,則可能需要添加引用或 using 指令,或者兩者兼而有之。 如果代碼引用任何程式集或 NuGet 包,則需要在專案中添加這些引用。

Visual Studio 會嘗試説明您識別缺少的引用。 當名稱未解析時,編輯器中將顯示一個燈泡圖示。 如果單擊燈泡,可以看到有關如何解決此問題的一些建議。 修復方法可能是:

- 新增 using 指令
- 新增對程式集的參考或
- 安裝 NuGet 包。

#### <a name="missing-using-directive"></a>缺少使用指令

例如,在下面的螢幕中,您可以選擇新增到`using System;`代碼檔的開頭以解析未解析的名稱: `Console`

![新增使用指令的燈泡螢幕擷取](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>遺失程式集參照

.NET 引用可以以程式集或 NuGet 套件的形式進行。 通常,如果您找到原始程式碼,發行者或作者將解釋需要哪些程式集以及代碼所依賴的包。 要手動添加對專案的引用,請右鍵單擊**解決方案資源管理器**中的 **「引用」** 節點,選擇 **「添加引用**」並查找所需的程式集。

![新增參考選單的螢幕擷取](media/add-reference.png)

您可以使用[引用管理員,按照"添加或刪除引用](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)"中的說明查找程式集並添加引用。

#### <a name="missing-nuget-package"></a>缺少 NuGet 套件

如果 Visual Studio 偵測到缺少的 NuGet 套件,則會出現一個燈泡,並為您提供安裝它的選項:

![要安裝套件的燈泡螢幕截圖](media/lightbulb-add-package.png)

如果這不能解決問題,並且 Visual Studio 找不到包,請嘗試連線搜尋它。 請參考[在視覺化工作室中安裝與使用 NuGet 套件](/nuget/quickstart/install-and-use-a-package-in-visual-studio)。

## <a name="use-the-right-version-of-net"></a>使用正確的版本 .NET

由於 .NET 框架的不同版本具有某種程度的向後相容性,因此較新的框架可能會運行為舊框架編寫的代碼,而無需進行任何修改。 但是,有時您需要針對特定框架。 如果尚未安裝 .NET 框架或 .NET Core 的特定版本,則可能需要安裝該版本。 請參閱[修改視覺工作室](../../install/modify-visual-studio.md)。

要改變目標框架,請參閱[變更目標框架](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version)。 關於詳細資訊,請參閱故障排除[.NET 框架定位錯誤](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

## <a name="next-steps"></a>後續步驟

通過閱讀[「歡迎瀏覽視覺工作室 IDE」](../visual-studio-ide.md)來探索視覺工作室開發環境。

## <a name="see-also"></a>另請參閱

[建立您的第一個 C# 應用程式](tutorial-console.md)
