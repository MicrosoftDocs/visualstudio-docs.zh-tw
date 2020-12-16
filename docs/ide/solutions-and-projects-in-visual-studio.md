---
title: 方案和專案
description: 瞭解 Visual Studio 專案和方案、如何從範本建立新專案，以及如何在方案總管中查看 & 管理專案。
ms.custom: SEO-VS-2020
ms.date: 12/15/2020
ms.topic: conceptual
f1_keywords:
- vs.addnewitem
- vs.addnewsolutionitem
- vs.openproject
- vs.addexistingitem
- vs.addexistingsolutionitem
- vs.environment.projects
- vs.environment.solutions
- VS.SolutionExplorer
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ebe6e5c7479ce4e3cda435c51a883c4d5db8cc45
ms.sourcegitcommit: 6f37100d4b8c15a21d3858335ded3c26ab275b93
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97599495"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio 中的方案和專案

本頁面描述 *專案* 和 *方案* 在 Visual Studio 中的概念。 它也會簡短介紹方案總管工具視窗，以及如何建立新專案。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的專案和方案](/visualstudio/mac/projects-and-solutions)。

## <a name="projects"></a>專案

當您在 Visual Studio 中建立應用程式或網站時，您會開始使用 *專案*。 在邏輯上，專案會包含編譯成可執行檔、程式庫或網站的所有檔案。 這些檔案可以包含原始程式碼、圖示、影像、資料檔案等等。 專案也包含編譯器設定和其他組態檔，這些是您的程式與其通訊的各種服務或元件所需的項目。

### <a name="project-file"></a>專案檔

Visual Studio 使用 [msbuild](../msbuild/msbuild.md) 在方案中建立每個專案，而且每個專案都包含 MSBuild 專案檔。 副檔名會反映專案的類型，例如 c # 專案 ( .csproj) 、Visual Basic 專案 (. vbproj) 或資料庫專案 ( .dbproj) 。 專案檔是一份 XML 檔，其中包含 MSBuild 用來建立專案所需的所有資訊和指示，包括內容、平臺需求、版本設定資訊、網頁伺服器或資料庫伺服器設定，以及要執行的工作。

專案檔是以 [MSBUILD XML 架構](../msbuild/msbuild-project-file-schema-reference.md)為基礎。 若要查看 Visual Studio 中較新的 [sdk 樣式專案檔案](../msbuild/how-to-use-project-sdk.md)的內容，請以滑鼠右鍵按一下 **方案總管** 中的專案節點，然後選取 [**編輯 \<projectname\>**]。 若要查看該樣式的 .NET Framework 和其他專案的內容，請先卸載專案 (以滑鼠右鍵按一下 **方案總管** 中的專案節點，然後選取 **[卸載專案** ]) 。 然後，以滑鼠右鍵按一下專案，然後選擇 **[ \<projectname\> 編輯**]。

> [!NOTE]
> 您不需要使用 Visual Studio 中的方案或專案來編輯、建立和偵錯工具代碼。 您可以只在 Visual Studio 中開啟包含原始程式檔的資料夾並開始編輯。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

## <a name="solutions"></a>方案

「方案」內所含的專案。 儘管名稱為方案，但其並非「解答」。 方案僅是一或多個相關專案的容器、組建資訊、Visual Studio 視窗設定、任何未與特定專案建立關聯的其他檔案。 方案由具有自己獨特格式的文字檔 (副檔名為 *.sln*) 所描述，並不適合手動編輯。

### <a name="solution-file"></a>解決方案檔案

Visual Studio 會使用兩種檔案類型 (*.sln* 和 *.suo*) 來儲存解決方案的設定：

|分機|名稱|描述|
|---------------|----------|-----------------|
|.sln|Visual Studio 方案|將專案、專案項目和方案項目組織到方案中。|
|.suo|方案使用者選項|儲存使用者層級設定和自訂項目，例如中斷點。|

### <a name="solution-folder"></a>方案資料夾

「方案資料夾」是一種虛擬資料夾，只位於 **方案總管** 中，您可以在其中使用它來將方案中的專案分組。 如果您想要在電腦上尋找方案檔，請移至 [**工具**  >  **選項**  >  **專案和方案**  >  **位置**]。 如需詳細資訊，請參閱 [選項對話方塊：專案和方案 > 位置](./reference/projects-solutions-locations-options.md)。

## <a name="create-new-projects"></a>建立新專案

建立新專案的最簡單方式是從特定類型的應用程式或網站的專案範本開始。 專案範本是由一組基本預先產生的程式碼檔案、組態檔、資產和設定所組成。 您可以在建立新專案的對話方塊中，找到這些 **範本 ([**  >  **新增**  >  **專案**]) 。 如需詳細資訊，請參閱 [建立新專案](create-new-project.md) 和使用 [方案和專案](../ide/creating-solutions-and-projects.md)。

如果您經常以某種方式自訂您的專案，您可以建立自訂專案範本，然後用它來建立新專案。 如需詳細資訊，請參閱[建立專案與項目範本](../ide/creating-project-and-item-templates.md)。

當您建立新專案時，根據預設它會儲存在 *%USERPROFILE%\source\repos*。 您可以在 [工具] > [選項] > [專案和方案] > [位置] 下的 [專案位置] 設定中變更此位置。 如需這個專案和其他專案和方案設定的詳細資訊，請參閱 [ [選項] 對話方塊中的 [專案和方案] 頁面](./reference/projects-and-solutions-options-dialog-box.md)。

## <a name="solution-explorer"></a>方案總管

建立新專案之後，您可以使用 **方案總管** 來查看和管理專案和方案與其相關聯的專案。 下圖顯示包含兩個專案的 c # 方案 **方案總管** ：

![方案總管](../ide/media/vs2015_solution_explorer.png)

許多功能表命令都是從 [方案總管] 中各種項目的快顯功能表取得。 這些命令包括建置專案、管理 NuGet 套件、新增參考、重新命名檔案，以及執行測試等等。 [方案總管] 頂端工具列上的按鈕可從方案檢視切換到資料夾檢視、顯示隱藏的檔案、摺疊所有節點等等。

> [!TIP]
> 如果您已關閉方案總管，而您想要再次開啟它，請從功能表列選擇 [**視窗**  >  **重設視窗** 配置]。

對於 ASP.NET Core 專案，您可以自訂 [方案總管] 中檔案巢狀的方式。 如需詳細資訊，請參閱[自訂 [方案總管] 中的檔案巢狀](file-nesting-solution-explorer.md)。

而且，若要查看方案總管中出現之部分圖示的清單，請參閱 [類別檢視和物件瀏覽器圖示](class-view-and-object-browser-icons.md)。

## <a name="see-also"></a>另請參閱

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [移植、移轉及升級專案](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [專案和方案 (Visual Studio for Mac)](/visualstudio/mac/projects-and-solutions)
- [新增和移除專案項目 (Visual Studio for Mac)](/visualstudio/mac/add-and-remove-project-items)
