---
title: '如何 (c # ) 執行程式'
description: '如何在 Visual Studio 中執行 c # 程式的初學者指南。'
ms.custom: vs-acquisition, get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e20caabb55e65801224177168f5c936f81402bbd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385223"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>如何：在 Visual Studio 中執行 c # 程式

執行程式所需執行的動作，取決於您的起點、應用程式或服務的型別，以及您是否要在偵錯工具下執行它。 在最簡單的情況下，當您在 Visual Studio 中開啟專案時，請按下 **Ctrl** + **F5** (**啟動但不) 調試** 程式，或按 **f5** (**開始進行調試** 程式) ，或按下 [主要 (] 工具列上的綠色箭號) [**開始] 按鈕** Visual Studio，來建立並執行專案。

![顯示 [開始] 按鈕的螢幕擷取畫面](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>從專案開始

如果您有 c # 專案 (*.csproj* 檔案) ，則可以執行它（如果它是可執行檔程式）。 如果專案包含具有方法的 c # 檔案 `Main` ，且其輸出是可執行檔 (EXE) ，則很有可能會在成功建立時執行。

如果您在 Visual Studio 的專案中已經有程式碼，請開啟專案。 若要開啟專案，請從 Windows 檔案總管按兩下或按一下 *.csproj* ，或從 Visual Studio 中，選擇 [ **開啟專案**]，流覽以尋找專案 (*.csproj*) 檔，然後選擇專案檔。

在 Visual Studio 中載入專案之後，請按下 **Ctrl** + **F5** (**啟動但不) 調試** 程式，或使用 Visual Studio 工具列上的綠色 [**開始**] 按鈕來執行程式。  如果有多個專案，則必須將使用 `Main` 方法的專案設定為啟始專案。 若要設定啟始專案，請以滑鼠右鍵按一下專案節點，然後選擇 [ **設定為啟始專案**]。

![設定啟始專案](media/set-as-startup-project.png)

Visual Studio 嘗試建立並執行您的專案。  如果有組建錯誤，您會在 [ **輸出** ] 視窗中看到組建輸出，並在 [ **錯誤清單** ] 視窗中看到錯誤。

如果組建成功，應用程式會以適用于專案類型的方式執行。 主控台應用程式會在終端機視窗中執行、Windows 桌面應用程式會在新視窗中啟動、在瀏覽器中啟動 web 應用程式 (IIS Express) ），依此類推。

## <a name="starting-from-code"></a>從程式碼開始

如果您是從程式代碼清單、程式碼檔案或少量的檔案開始，請先確定您要執行的程式碼是來自信任的來源，而且是可執行檔程式。 如果它有 `Main` 方法，則可能會做為可執行檔程式，您可以使用主控台應用程式範本建立專案，以在 Visual Studio 中使用它。

### <a name="code-listing-for-a-single-file"></a>單一檔案的程式代碼清單

開始 Visual Studio，開啟空白的 c # 主控台專案，選取專案中已有的 .cs 檔案中的所有程式碼，然後將它刪除。 然後，將您的程式碼內容貼到 .cs 檔案中。 當您貼上程式碼時，請覆寫或刪除先前的程式碼。 重新命名檔案以符合原始程式碼。

### <a name="code-listings-for-a-few-files"></a>一些檔案的程式代碼清單

開始 Visual Studio，開啟空白的 c # 主控台專案，選取專案中已有的 .cs 檔案中的所有程式碼，然後將它刪除。 然後，將第一個程式碼檔案的內容貼到 .cs 檔案中。 重新命名檔案以符合原始程式碼。 

若為第二個檔案，請以滑鼠右鍵按一下 **方案總管** 中的專案節點，開啟專案的快捷方式功能表，然後選擇 [**加入 > 現有專案**] (或使用按鍵組合 **Shift** + **Alt** + **a**) ，然後選取程式碼檔案。

### <a name="multiple-files-on-disk"></a>磁片上的多個檔案

1. 如果您不確定) ，請建立適當類型的新專案 (使用 c # **主控台應用程式** 。

2. 以滑鼠右鍵按一下專案節點，   >  然後選擇 [加入 **現有專案**] 來選取檔案，並將它們匯入您的專案中。  

### <a name="starting-from-a-folder"></a>從資料夾開始

當您使用許多檔案的資料夾時，請先查看是否有專案或方案。  如果是使用 Visual Studio 建立程式，您應該會找到專案檔或方案檔。 尋找副檔名為 *.csproj* 或 .sln 的檔案，並在 Windows 檔案總管中，按兩下其中一個檔案，在 Visual Studio 中開啟檔案。 請參閱 [從 Visual Studio 解決方案或專案開始](#starting-from-a-project)。

如果您沒有專案檔（例如，如果程式碼是在另一個開發環境中開發），請使用 Visual Studio 中的 [ **開啟資料夾** ] 方法開啟最上層資料夾。 請參閱 [開發沒有專案或解決方案](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)的程式碼。

## <a name="starting-from-a-github-or-azure-devops-repo"></a>從 GitHub 或 Azure DevOps 存放庫開始

如果您想要執行的程式碼是在 GitHub 或 Azure DevOps 存放庫中，您可以使用 Visual Studio 直接從存放庫開啟專案。 請參閱從存放庫 [開啟專案](../tutorial-open-project-from-repo.md)。

## <a name="run-the-program"></a>執行程式

若要啟動程式，請按下主要 Visual Studio 工具列上的綠色箭號 ([**開始**] 按鈕) ，或按 **f5** 或 **Ctrl** + **f5** 來執行程式。 當您使用 [ **開始** ] 按鈕時，它會在偵錯工具下執行。  Visual Studio 嘗試在您的專案中建立程式碼並加以執行。  如果成功，很棒！ 但如果沒有，請繼續閱讀有關如何讓它成功建立的一些想法。

## <a name="troubleshooting"></a>疑難排解

您的程式碼可能有錯誤，但如果程式碼正確，但只是相依于其他的元件或 NuGet 套件，或者是以不同版本的 .NET 撰寫而成，您可能可以輕鬆地修正此問題。

### <a name="add-references"></a>新增參考

若要正確建立，程式碼必須正確，並將正確的參考設定為程式庫或其他相依性。 您可以查看紅色波浪線和 **錯誤清單** ，查看程式是否有任何錯誤，即使在編譯和執行之前也是一樣。 如果您看到與無法解析的名稱相關的錯誤，您可能需要加入參考或 using 指示詞，或兩者。 如果程式碼參考任何元件或 NuGet 封裝，您必須在專案中新增這些參考。

Visual Studio 會嘗試協助您找出遺漏的參考。 當名稱無法解析時，編輯器中會出現燈泡圖示。 如果您按一下燈泡，可以看到一些如何修正問題的建議。 修正程式可能是：

- 新增 using 指示詞
- 加入元件的參考，或
- 安裝 NuGet 套件。

#### <a name="missing-using-directive"></a>遺漏 using 指示詞

例如，在下列畫面中，您可以選擇新增至程式 `using System;` 代碼檔案的開頭，以解析未解析的名稱 `Console` ：

![新增 using 指示詞的燈泡螢幕擷取畫面](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>遺漏元件參考

.NET 參考可以是元件或 NuGet 套件的形式。 通常，如果您找到原始程式碼，發行者或作者將會說明需要哪些元件，以及程式碼相依的套件。 若要手動加入專案的參考，請以滑鼠右鍵按一下 **方案總管** 中的 [**參考**] 節點，選擇 [**加入參考**]，然後找出必要的元件。

![[新增參考] 功能表的螢幕擷取畫面](media/add-reference.png)

您可以遵循 [使用參考管理員加入或移除參考](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)中的指示，找到元件並加入參考。

#### <a name="missing-nuget-package"></a>缺少 NuGet 套件

如果 Visual Studio 偵測到遺漏的 NuGet 套件，則會出現燈泡，並提供您安裝的選項：

![要安裝套件的燈泡螢幕擷取畫面](media/lightbulb-add-package.png)

如果這無法解決問題，且 Visual Studio 找不到套件，請嘗試在線上搜尋。 請參閱 [在 Visual Studio 中安裝和使用 NuGet 套件](/nuget/quickstart/install-and-use-a-package-in-visual-studio)。

## <a name="use-the-right-version-of-net"></a>使用正確的 .NET 版本

因為不同版本的 .NET Framework 有某種程度的回溯相容性，所以較新的架構可能會執行針對較舊架構所撰寫的程式碼，而不需要任何修改。 但是，有時候您需要以特定的架構為目標。 您可能需要安裝特定版本的 .NET Framework 或 .NET Core （如果尚未安裝）。 請參閱 [修改 Visual Studio](../../install/modify-visual-studio.md)。

若要變更目標 framework，請參閱 [變更目標 framework](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version)。 如需詳細資訊，請參閱 [疑難排解 .NET Framework 目標錯誤](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

## <a name="next-steps"></a>後續步驟

閱讀 [歡迎使用 VISUAL STUDIO IDE，以](../visual-studio-ide.md)探索 Visual Studio 開發環境。

## <a name="see-also"></a>另請參閱

[建立您的第一個 C# 應用程式](tutorial-console.md)
