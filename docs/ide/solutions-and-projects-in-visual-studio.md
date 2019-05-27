---
title: 方案和專案
ms.date: 10/05/2017
ms.topic: conceptual
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items [Visual Studio]
- solutions [Visual Studio]
- project items [Visual Studio]
- solutions [Visual Studio], designing
- projects [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0116a8c4fa6326a1176c132aef59a789daabffca
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461526"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Visual Studio 中的方案和專案

本文描述 Visual Studio 中的「專案」和「方案」概念。 同時簡短說明如何建立新的專案以及 [方案總管] 工具視窗。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的專案和方案](/visualstudio/mac/projects-and-solutions)。

## <a name="projects"></a>專案

當您在 Visual Studio 中建立 App、網站、外掛程式等項目時，您必須開始一個「專案」。 就邏輯方面而言，專案會包含所有原始程式碼檔案、圖示、影像、資料檔案等等，以編譯為可執行檔、程式庫或網站。 專案也包含編譯器設定和其他組態檔，這些是您的程式與其通訊的各種服務或元件所需的項目。

> [!NOTE]
> 您不需要使用 Visual Studio 中的方案或專案來編輯、建置和偵錯程式碼。 您可以只在 Visual Studio 中開啟包含原始程式檔的資料夾並開始編輯。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

專案定義於具有 *.vbproj*、*.csproj* 或 *.vcxproj* 這類副檔名的 XML 檔案。 此檔案包含虛擬資料夾階層，以及專案中所有項目的路徑。 它也包含組建設定。

> [!TIP]
> 若要在 Visual Studio 中查看專案檔的內容，請先卸載專案，方法是在 [方案總管] 中選取專案名稱，然後從操作功能表或右鍵功能表中選擇 [卸載專案]。 然後，再次開啟內容功能表並選擇 [編輯 \<專案名稱\>]。

在 Visual Studio 中，[方案總管] 會使用專案檔來顯示專案內容與設定。 當您編譯專案時，MSBuild 引擎會使用專案檔來建立可執行檔。 您也可以自訂專案來產生其他類型的輸出。

## <a name="solutions"></a>方案

「方案」內所含的專案。 儘管名稱為方案，但其並非「解答」。 方案僅是一或多個相關專案的容器、組建資訊、Visual Studio 視窗設定、任何未與特定專案建立關聯的其他檔案。 方案由具有自己獨特格式的文字檔 (副檔名為 *.sln*) 所描述，並不適合手動編輯。

Visual Studio 使用兩種檔案類型 (*.sln* 和 *.suo*) 來儲存方案的設定。

|副檔名|名稱|說明|
|---------------|----------|-----------------|
|.sln|Visual Studio 方案|將專案、專案項目和方案項目組織到方案中。|
|.suo|方案使用者選項|儲存使用者層級設定和自訂項目，例如中斷點。|

## <a name="create-new-projects"></a>建立新專案

建立新專案的最簡單方式是從特定類型的應用程式或網站的專案範本開始。 專案範本是由一組基本預先產生的程式碼檔案、組態檔、資產和設定所組成。 這些範本可在您建立新專案的對話方塊中使用 ([檔案] > [新增] > [專案])。 如需詳細資訊，請參閱[建立方案和專案](../ide/creating-solutions-and-projects.md)。

您也可以建立自訂專案與項目範本。 如需詳細資訊，請參閱[建立專案與項目範本](../ide/creating-project-and-item-templates.md)。

當您建立新專案時，根據預設它會儲存在 *%USERPROFILE%\source\repos*。 您可以在 [工具] > [選項] > [專案和方案] > [位置] 下的 [專案位置] 中自訂此位置。 如需詳細資訊，請參閱 [[選項] 對話方塊，[專案和方案] 頁面](../ide/reference/projects-and-solutions-options-dialog-box.md)。

## <a name="manage-projects-in-solution-explorer"></a>管理 [方案總管] 中的專案

建立新專案之後，即可使用方案總管來檢視和管理專案與方案，以及其相關聯項目。 下圖顯示 [方案總管] 與包含兩個專案的 C# 方案。

![底下提供說明，包括方案總管](../ide/media/vs2015_solution_explorer.png)

## <a name="see-also"></a>另請參閱

- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [專案和方案 (Visual Studio for Mac)](/visualstudio/mac/projects-and-solutions)
- [新增和移除專案項目 (Visual Studio for Mac)](/visualstudio/mac/add-and-remove-project-items)
