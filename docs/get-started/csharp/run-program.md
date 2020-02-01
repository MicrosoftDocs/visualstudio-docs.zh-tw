---
title: 如何執行C#程式
description: 有關如何在 Visual Studio 中執行C#程式的初學者指南。
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
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76924613"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>如何：在 Visual Studio 中C#執行程式

執行程式的必要動作取決於您開始的專案、程式、應用程式或服務的類型，以及是否要在偵錯工具下執行。 在最簡單的情況下，當您在 Visual Studio 中開啟專案時，請按**Ctrl**+**F5** （[**啟動但不** **進行**偵錯工具]）或**F5** （從 [開始] [啟動]）來建立並執行它，或按主要 Visual Studio 工具列上的綠色箭號（[開始]**按鈕**）。

![顯示 [開始] 按鈕的螢幕擷取畫面](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>從專案開始

如果您有C#專案（ *.csproj*檔案），則可以執行它（如果它是可執行檔程式）。 如果專案包含C#具有 `Main` 方法的檔案，且其輸出為可執行檔（EXE），則當成功建立時，很有可能會執行它。

如果 Visual Studio 中的專案中已經有程式碼，請開啟專案。 若要開啟專案，請按兩下或從 Windows 檔案瀏覽器中按一下 *.csproj* ，或從 Visual Studio，選擇 [**開啟專案**]，流覽以尋找專案（ *.csproj*）檔案，然後選擇專案檔。

在 Visual Studio 中載入專案之後，請按**Ctrl**+**F5** （[**啟動但不進行調試**程式]），或使用 [Visual Studio] 工具列上的綠色 [**開始**] 按鈕來執行程式。  如果有多個專案，則必須將具有 `Main` 方法的專案設定為啟始專案。 若要設定啟始專案，請以滑鼠右鍵按一下專案節點，然後選擇 [**設定為啟始專案**]。

![設定啟始專案](media/set-as-startup-project.png)

Visual Studio 嘗試建立並執行您的專案。  如果發生組建錯誤，您會在 [**輸出**] 視窗中看到組建輸出，並在 [**錯誤清單**] 視窗中看見錯誤。

如果組建成功，應用程式會以適用于專案類型的方式執行。 主控台應用程式會在終端機視窗中執行，Windows 傳統型應用程式會在新視窗中啟動，web 應用程式會在瀏覽器中啟動（由 IIS Express 所裝載）等等。

## <a name="starting-from-code"></a>從程式碼開始

如果您是從程式代碼清單、程式碼檔案或少量檔案開始，請先確定您要執行的程式碼來自受信任的來源，而且是可執行檔程式。 如果它有 `Main` 的方法，它可能會作為可執行檔程式，讓您可以使用主控台應用程式範本來建立專案，以便在 Visual Studio 中使用它。

### <a name="code-listing-for-a-single-file"></a>單一檔案的程式代碼清單

啟動 Visual Studio，開啟空白C#的主控台專案，選取專案中的 .cs 檔案中的所有程式碼，然後將它刪除。 然後，將您的程式碼內容貼入 .cs 檔案中。 當您貼上程式碼時，請覆寫或刪除之前存在的代碼。 將檔案重新命名以符合原始程式碼。

### <a name="code-listings-for-a-few-files"></a>幾個檔案的程式代碼清單

啟動 Visual Studio，開啟空白C#的主控台專案，選取專案中的 .cs 檔案中的所有程式碼，然後將它刪除。 然後，將第一個程式碼檔案的內容貼入 .cs 檔案中。 將檔案重新命名以符合原始程式碼。 

針對第二個檔案，以滑鼠右鍵按一下**方案總管**中的專案節點，開啟專案的快捷方式功能表，然後選擇 [**加入 > 現有專案**] （或使用按鍵**組合+** **Alt**+**a**），然後選取程式碼檔案。

### <a name="multiple-files-on-disk"></a>磁片上的多個檔案

1. 建立適當類型的新專案（如果您不C#確定，請使用**主控台應用程式**）。

2. 以滑鼠右鍵按一下專案節點，se [**加入** > **現有專案**] 以選取檔案，然後將檔案匯入到您的專案中。  

### <a name="starting-from-a-folder"></a>從資料夾開始

當您使用多個檔案的資料夾時，請先查看是否有專案或解決方案。  如果程式是使用 Visual Studio 建立的，您應該會找到專案檔或方案檔。 尋找副檔名為 *.csproj*或 .sln 的檔案，並在 Windows 檔案瀏覽器中按兩下其中一個檔案，以在 Visual Studio 中開啟它們。 請參閱[從 Visual Studio 方案或專案開始](#starting-from-a-project)。

如果您沒有專案檔（例如，如果程式碼是在另一個開發環境中開發），請使用 Visual Studio 中的 [**開啟資料夾**] 方法來開啟最上層資料夾。 請參閱[開發不含專案或解決方案](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)的程式碼。

## <a name="starting-from-a-github-or-azure-devops-repo"></a>從 GitHub 或 Azure DevOps 存放庫開始

如果您想要執行的程式碼位於 GitHub 或 Azure DevOps 存放庫中，您可以使用 Visual Studio 直接從存放庫開啟專案。 請參閱從存放庫[開啟專案](../tutorial-open-project-from-repo.md)。

## <a name="run-the-program"></a>執行程式

若要啟動程式，請按主要 Visual Studio 工具列上的綠色箭號（[**開始**] 按鈕），或按**f5**或**Ctrl**+**f5**來執行程式。 當您使用 [**開始**] 按鈕時，它會在偵錯工具下執行。  Visual Studio 嘗試在您的專案中建立程式碼並加以執行。  如果成功，很棒！ 但如果沒有，請繼續閱讀以瞭解如何使其成功組建的一些概念。

## <a name="troubleshooting"></a>疑難排解

您的程式碼可能會有錯誤，但如果程式碼正確，但只取決於一些其他元件或 NuGet 套件，或已撰寫成以不同版本的 .NET 為目標，您可以輕鬆地加以修正。

### <a name="add-references"></a>新增參考

若要正確建立，程式碼必須正確，並將正確的參考設定為程式庫或其他相依性。 您可以查看紅色曲線和**錯誤清單**，以查看程式是否有任何錯誤，即使在您編譯和執行之前也一樣。 如果您看到與無法解析的名稱相關的錯誤，您可能需要加入參考或 using 指示詞，或兩者。 如果程式碼參考任何元件或 NuGet 封裝，您必須在專案中加入這些參考。

Visual Studio 嘗試協助您識別遺漏的參考。 當名稱無法解析時，編輯器中會出現燈泡圖示。 如果您按一下燈泡，可以看到一些如何修正問題的建議。 修正可能是：

- 新增 using 指示詞
- 加入元件的參考，或
- 安裝 NuGet 套件。

#### <a name="missing-using-directive"></a>缺少 using 指示詞

例如，在下列畫面中，您可以選擇將 `using System;` 新增至程式碼檔案的開頭，以解析無法解析的名稱 `Console`：

![用燈泡來新增 using 指示詞的螢幕擷取畫面](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>缺少元件參考

.NET 參考可以是元件或 NuGet 套件的形式。 通常，如果您找到原始程式碼，發行者或作者會說明所需的元件，以及程式碼相依的封裝。 若要手動加入專案的參考，請以滑鼠右鍵按一下**方案總管**中的 [**參考**] 節點，選擇 [**加入參考**]，然後找出所需的元件。

![[加入參考] 功能表的螢幕擷取畫面](media/add-reference.png)

您可以遵循[使用參考管理員新增或移除參考](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)中的指示，尋找元件並加入參考。

#### <a name="missing-nuget-package"></a>缺少 NuGet 套件

如果 Visual Studio 偵測到遺失的 NuGet 套件，則會出現燈泡，並提供您安裝它的選項：

![要安裝套件的燈泡螢幕擷取畫面](media/lightbulb-add-package.png)

如果這樣做無法解決問題，而且 Visual Studio 找不到套件，請嘗試在線上進行搜尋。 請參閱[在 Visual Studio 中安裝和使用 NuGet 套件](/nuget/quickstart/install-and-use-a-package-in-visual-studio)。

## <a name="use-the-right-version-of-net"></a>使用正確版本的 .NET

因為 .NET Framework 的不同版本具有某種程度的回溯相容性，所以較新的架構可能會執行針對舊版架構所撰寫的程式碼，而不需要進行任何修改。 但是，有時候您需要以特定架構為目標。 您可能需要安裝特定版本的 .NET Framework 或 .NET Core （如果尚未安裝的話）。 請參閱[修改 Visual Studio](../../install/modify-visual-studio.md)。

若要變更目標 framework，請參閱[變更目標 framework](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version)。 如需詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)。

## <a name="next-steps"></a>後續步驟

閱讀[歡迎使用 VISUAL STUDIO IDE](../visual-studio-ide.md)，探索 Visual Studio 的開發環境。

## <a name="see-also"></a>請參閱

[建立您的C#第一個應用程式](tutorial-console.md)
