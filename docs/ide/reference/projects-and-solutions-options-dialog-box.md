---
title: 專案和解決方案、選項對話方塊
description: 瞭解如何使用 [專案和方案] 區段中的 [一般] 頁面，來定義與專案和方案相關 Visual Studio 的行為。
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2fab59a590b59452362a47d48bcdfa7dd8661f57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907512"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>選項對話方塊：一般專案和方案 \>

您可以使用此頁面定義與專案和解決方案有關的 Visual Studio 行為。 若要存取這些選項，請選取 [**工具**  >  **選項**]，展開 [**專案和方案**]，然後選取 **[一般**]。

下列選項位於 [一般] 頁面上。

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>建置完成但發生錯誤時一律顯示錯誤清單

只有在無法建置專案時，才在建置完成時開啟 [錯誤清單]。 這樣會顯示在建置過程中發生的錯誤。 清除此選項時，仍然會發生錯誤，但是建置完成時不會開啟視窗。 這個選項預設為啟用。

## <a name="track-active-item-in-solution-explorer"></a>在 [方案總管] 中追蹤使用中的項目

選取此選項時，方案總管會自動開啟並選取使用中的項目。 隨著您使用專案或方案中的不同檔案，或設計工具中的不同元件，選取的項目也會變更。 如果清除這個選項，方案總管中的選取項目就不會自動變更。 這個選項預設為啟用。

## <a name="show-advanced-build-configurations"></a>顯示進階建置組態

選取此選項時，[專案屬性頁] 對話方塊和 [方案屬性頁] 對話方塊就會顯示組建組態選項。 清除此選項時，Visual Basic 與 C# 專案 (包含一或兩個組態偵錯和發行) 的 [專案屬性頁] 對話方塊和 [方案屬性頁] 對話方塊就不會顯示組建組態選項。 如果專案具有使用者定義的組態，就會顯示建置組態選項。

取消選取此選項時，[建置] 功能表上的命令 (例如 [建置方案]、[重建方案] 及 [清除方案]) 會在發行組態上執行，而 [偵錯] 功能表上的命令 (例如 [開始偵錯] 及 [啟動但不偵錯]) 則會在偵錯組態上執行。

## <a name="always-show-solution"></a>一律顯示方案

選取此選項時，IDE 一律會顯示方案以及針對方案執行的所有命令。 清除此選項時，所有專案都會建立為獨立專案；如果方案只包含一個專案，您就不會在 [方案總管] 中看到方案，也不會在 IDE 中看到針對方案執行的命令。

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>在建立新專案時予以儲存

選取此選項時，您可以在 [新增專案] 對話方塊中指定專案的位置。 清除此選項時，所有新專案都會建立為暫存專案。 當您使用暫存專案時，可以建立和測試專案，而不需要指定磁碟位置。

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>在專案位置未受信任時警告使用者

如果您嘗試在未受完全信任的位置建立新專案或開啟現有專案 (例如，在 UNC 路徑或 HTTP 路徑上)，則會顯示訊息。 使用此選項，指定每當您在未受完全信任的位置嘗試建立或開啟專案時，是否要顯示訊息。

## <a name="show-output-window-when-build-starts"></a>建置開始時顯示輸出視窗

會在解決方案組建開始時，自動在 IDE 中顯示 [ [輸出] 視窗](../../ide/reference/output-window.md) 。

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>在重新命名檔案時提示符號重新命名

選取此選項時，Visual Studio 會顯示訊息方塊，詢問是否也應重新命名專案中所有對程式碼項目的參考。

## <a name="prompt-before-moving-files-to-a-new-location"></a>將檔案移至新位置前先提示

選取此選項時，在 [方案總管] 中執行檔案的位置變更前，Visual Studio 會顯示確認訊息方塊。

## <a name="reopen-documents-on-solution-load"></a>在解決方案載入時重新開啟文件

選取此選項時，會在開啟解決方案時，自動開啟上次關閉此解決方案時處於開啟狀態的文件。

重新開啟特定類型的檔案或設計工具可能會導致方案載入延遲。 如果您不想要還原解決方案先前的內容，請取消核取此選項以 [改善解決方案載入效能](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) 。

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>還原方案載入時的 [方案總管] 專案階層狀態

選取時，會根據上次開啟方案時節點為展開或摺疊，來還原 [方案總管] 中的節點狀態。 取消選取此選項可減少大型方案的方案載入時間。

> [!TIP]
> 如果您停用此選項，您可以選取 [方案總管] 工具列中的 [與使用中文件同步]，輕鬆地巡覽至 [方案總管] 中的使用中文件。
>
> ![[方案總管] 中的 [與使用中文件同步]](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>按兩下或按 Enter 鍵以開啟 SDK 樣式專案檔

選取此選項時，若在 [方案總管] 中按兩下 SDK 樣式專案節點，或是選取它，然後按 **Enter** 鍵，專案檔 (例如 \*.csproj 檔案) 就會在編輯器中以 XML 的形式開啟。 取消選取時，在 [方案總管] 中按兩下 SDK 樣式專案節點或選取它，然後按 **Enter**，只會有展開或摺疊節點的效果。

如果您未選取此選項並想要編輯 SDK 樣式專案檔，請在 [方案總管] 中以滑鼠右鍵按一下專案節點，然後選取 [編輯專案檔]。 針對其他專案類型，您必須先卸載專案，才能在 Visual Studio 中進行編輯。

> [!TIP]
> 「SDK 樣式專案」或[專案 SDK](../../msbuild/how-to-use-project-sdk.md) 具有 MSBuild 15.0 所引進較新且更簡化的專案檔格式。 SDK 樣式專案包含 `Project` 元素的 `Sdk` 屬性，例如 `<Project Sdk="Microsoft.NET.Sdk">`。 例如，當您從其中一個 Visual Studio 範本建立新的 .NET Core 專案時，Visual Studio 會建立 SDK 樣式專案。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [選項對話方塊：專案和方案 \> 位置](projects-solutions-locations-options.md)
- [選項對話方塊、專案和方案、建置並執行](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [選項對話方塊、專案和方案、Web 專案](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
