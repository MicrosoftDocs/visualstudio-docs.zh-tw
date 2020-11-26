---
title: 程式碼樣式選項及程式碼清除
description: 瞭解如何設定 Visual Studio，以使用程式碼清除 (Visual Studio 2019) 和格式化檔 (Visual Studio 2017) 命令來套用程式碼樣式喜好設定。
ms.custom: SEO-VS-2020
ms.date: 04/25/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9172fff2dde1528c5ea382aea996d316e0738ea0
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189741"
---
# <a name="code-style-preferences"></a>程式碼樣式喜好設定

您可以使用 [EditorConfig 檔案](#code-styles-in-editorconfig-files)針對每個專案定義程式碼樣式設定，或是針對所有您在 Visual Studio 中編輯的程式碼，使用文字編輯器的 [選項](#code-styles-in-the-options-dialog-box) 頁面進行設定。 針對 C# 程式碼，您也可以使用 [程式碼清除] (Visual Studio 2019) 和 [格式化文件] (Visual Studio 2017) 命令來設定 Visual Studio，套用這些程式碼樣式喜好設定。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的編輯器行為](/visualstudio/mac/editor-behavior)。

## <a name="code-styles-in-editorconfig-files"></a>EditorConfig 檔案中的程式碼樣式

.NET 的[程式碼樣式設定](/dotnet/fundamentals/code-analysis/code-style-rule-options)可透過將 [EditorConfig](create-portable-custom-editor-options.md) 檔案新增到專案來指定。 EditorConfig 檔案都會與程式碼基底 (而非 Visual Studio 個人化帳戶) 建立關聯。 EditorConfig 檔案中設定的優先權高於 [選項] 對話方塊中所指定程式碼樣式。 當您想要針對存放庫或專案的所有參與者強制執行編碼樣式時，請使用 EditorConfig 檔案。

::: moniker range=">=vs-2019"

您可以手動填入您的 EditorConfig 檔案，或是根據您在 Visual Studio 中 [選項] 對話方塊中所選擇的程式碼樣式設定來自動產生該檔案。 您可以在 [**工具**  >  **選項**  >  **文字編輯器**]、[**c #** 或 **基本**] > 程式 **代碼樣式** 的  >  **一般**> 使用此選項頁面。 按一下 [從設定產生 .editorconfig 檔案] 來根據此 [選項] 頁面上的設定自動產生程式碼樣式 *.editorconfig* 檔案。

![在 Visual Studio 2019 中從設定產生 editorconfig 檔案](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>[選項] 對話方塊中的程式碼樣式

您可以透過從 [工具] 功能表開啟 [選項] 對話方塊，來為您所有的 C# 和 Visual Basic 專案設定程式碼樣式喜好設定。 在 [選項] 對話方塊中，選取 [文字編輯器] > [C#] 或 [Basic] > [程式碼樣式] > [一般]。

清單中的每個項目會在選取時顯示個別的喜好設定預覽：

::: moniker range="vs-2017"

![程式碼樣式選項](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![程式碼樣式選項](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

此視窗中所設定的選項適用於您的 Visual Studio 個人化帳戶，而且不會與特定專案或程式碼基底建立關聯。 此外，它們不會在建置階段強制執行，包含於持續整合 (CI) 組建中。 若您想要將程式碼樣式喜好設定與您的專案建立關聯，並在建置期間強制套用樣式，請在與專案建立關聯的 [.editorconfig](#code-styles-in-editorconfig-files) 檔案中指定喜好設定。

### <a name="preference-and-severity"></a>喜好設定和嚴重性

對於此頁面上的各個程式碼樣式，您可以使用每一行的下拉式清單來設定 [喜好設定] 和 [嚴重性] 的值。 [嚴重性] 可設定為 [僅重構]、[建議]、[警告] 或 [錯誤]。 如果您想要針對程式碼樣式啟用[快速動作](../ide/quick-actions.md)，請務必將 [嚴重性] 設定設為 [僅重構] 以外的值。 **Quick Actions** :::image type="icon" source="media/light-bulb-dropdown.png"::: 當使用非慣用樣式時，會出現 [快速動作] 燈泡、錯誤燈泡 :::image type="icon" source="media/error-bulb.png"::: 或螺絲起子 :::image type="icon" source="media/screwdriver.png"::: 圖示，而且您可以在 [**快速動作**] 清單中選擇一個選項，以自動將程式碼重寫為慣用的樣式。

::: moniker range=">=vs-2019"

## <a name="enforce-code-styles-on-build"></a>在組建上強制執行程式碼樣式

從 Visual Studio 2019 16.8 版（包括 .NET 5.0 RC2 SDK）開始，您可以對所有 .NET 專案 [強制執行組建的 .net 程式碼慣例](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis) 。 在組建階段，.NET 程式碼樣式違規將會顯示為「IDE」前置詞的警告或錯誤。 這可讓您在程式碼基底中嚴格強制執行一致的程式碼樣式。

::: moniker-end

## <a name="apply-code-styles"></a>套用程式碼樣式

::: moniker range="vs-2017"

您可以設定 [格式化文件] 命令 ([編輯] > [進階] > [格式化文件]) 來套用您的程式碼樣式設定 (從 EditorConfig 檔案或 [程式碼樣式])，以及其一般會進行的格式化 (例如縮排)。 若專案中存在 *.editorconfig* 檔案，則會優先使用這些設定。

> [!NOTE]
> 使用 [格式化文件] 命令套用程式碼樣式僅適用於 C# 程式碼檔案。 這是實驗性的功能。

您可以在 [格式化][ 選項頁面](reference/options-text-editor-csharp-formatting.md#format-document-settings)上設定您希望 [格式化文件] 套用的設定。

![Visual Studio 2017 中格式化文件的程式碼樣式設定](media/format-document-settings-experiment.png)

> [!TIP]
> 設定為 [ **無** ] 的規則不會參與程式碼清除，但可透過 [ **快速動作] 和 [重構** ] 功能表個別套用。

當您第一次觸發 [格式化文件] 命令時，黃色的資訊列會提示您設定程式碼清除設定。

::: moniker-end

::: moniker range=">=vs-2019"

針對 c # 程式碼檔案，Visual Studio 2019 的編輯器底部有一個 [程式 **代碼清除**] 按鈕 (鍵盤： **ctrl** + **K**、 **ctrl** + **E**) 從 EditorConfig 檔或 [程式 **代碼樣式** 選項] 頁面套用程式碼樣式。 若專案中存在 *.editorconfig* 檔案，則會優先使用這些設定。

![在 Visual Studio 2019 中執行程式碼清除](media/execute-code-cleanup.png)

> [!TIP]
> 設定為 [ **無** ] 的規則不會參與程式碼清除，但可透過 [ **快速動作] 和 [重構** ] 功能表個別套用。

首先，在 [設定程式碼清除] 對話方塊中設定您想要套用的程式碼樣式 (從兩個設定檔中擇一進行設定)。 若要開啟此對話方塊，請按一下程式碼清除掃帚圖示旁邊的擴張箭頭，然後選擇 [設定程式碼清除]。

![在 Visual Studio 2019 中設定程式碼清除](media/configure-code-cleanup.png)

設定程式碼清除之後，您可以按一下 [掃帚] 圖示，或按 **ctrl** + **K**、 **ctrl** + **E** 以執行程式碼清除。 您也可以跨整個專案或解決方案執行程式碼清除。 以滑鼠右鍵按一下 [方案總管] 中的專案或解決方案名稱，選取 [分析與程式碼清除]，然後選取 [執行程式碼清除]。

![跨整個專案或解決方案執行程式碼清除](media/run-code-cleanup-project-solution.png)

若您想要在每次儲存檔案時套用程式碼樣式設定，建議您參考 [Code Cleanup on Save](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) (儲存時清除程式碼) 延伸模組。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [快速動作](../ide/quick-actions.md)
- [EditorConfig 的 .NET 編碼慣例設定](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [編輯器行為 (Visual Studio for Mac)](/visualstudio/mac/editor-behavior)
