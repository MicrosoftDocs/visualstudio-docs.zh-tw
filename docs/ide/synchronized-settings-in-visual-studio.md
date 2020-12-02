---
title: 同步處理設定
description: 瞭解如何藉由登入相同的個人化帳戶，在多部電腦之間同步處理您的 Visual studio 設定。
ms.custom: SEO-VS-2020
ms.date: 06/18/2020
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5326264063d135582f2e9b8730ffcf16cba9e3d6
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479198"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>跨多部電腦同步處理 Visual Studio 設定

當您使用相同的個人化帳戶在多部電腦上登入 Visual Studio 時，可以跨電腦同步處理您的設定。

## <a name="synchronized-settings"></a>同步設定

預設會同步處理下列設定：

- 開發設定。 您需要在第一次開啟 Visual Studio 時選取設定集合，但是可以隨時變更選取範圍。 如需詳細資訊，請參閱[環境設定](../ide/environment-settings.md)。

- 使用者定義的命令別名。 如需有關如何定義命令別名的詳細資訊，請參閱 [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。

- **視窗**  >  **管理視窗版面** 配置頁面中的使用者定義視窗版面配置。

- [**工具**  >  **選項**] 頁面中的下列選項：

  - **環境**  >  **[一般** 選項] 頁面上的主題和功能表列大小寫設定。

  - **環境** 字型  >  **和色彩** 選項頁面上的所有設定。

  - **環境**  >  **鍵盤** 選項頁面上的所有鍵盤快速鍵。

  - [**環境**] 索引標籤  >  **和 [Windows 選項]** 頁面上的所有設定。

  - **環境**  >  **啟動** 選項頁面上的所有設定。

  - [文字編輯器] 選項頁面上的所有設定，例如[程式碼樣式喜好設定](code-styles-and-code-cleanup.md)。

  - **XAML 設計工具** 選項頁面上的所有設定。

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>關閉特定電腦的同步設定

Visual Studio 的同步設定預設為開啟。 您可以前往 [**工具** 選項環境帳戶] 頁面關閉電腦上的同步  >  **Options**  >  **Environment**  >  **Accounts** 處理設定，並 **在登入 Visual Studio 時** 取消核取各裝置的設定。

例如，如果您決定不要同步處理電腦 "A" 上 Visual Studio 中的設定，則在電腦 "A" 上所做的任何設定變更都不會出現在電腦 "B" 或電腦 "C" 上。 電腦 "B" 和 "C" 會繼續互相同步處理，但不會和電腦 "A" 同步。

> [!NOTE]
> 如果您選擇 [**工具** 選項環境帳戶] 頁面上的選項來選擇不同步處理設定  >  **Options**  >  **Environment**  >  **Accounts** ，則您在相同電腦上的其他 Visual Studio 版本或版本不會受到影響。 Visual studio 的那些並存安裝將繼續同步處理其設定 (除非您也在該處取消選取選項)。

## <a name="synchronize-settings-across-visual-studio-ide-products-and-editions"></a>同步處理 Visual Studio IDE 產品和版本之間的設定

設定會在「並存」安裝的 Visual Studio 版本之間同步處理。 設定也會跨 Visual Studio IDE 產品進行同步處理，包括 Blend for Visual Studio。 不過，個別 Visual Studio IDE 產品可能會有自己的設定，而不會與 Visual Studio 共用。 例如，電腦 A 上的 Blend for Visual Studio 專屬設定不會和電腦 A 或 B 上的 Visual Studio 共用。

## <a name="side-by-side-synchronized-settings"></a>並存同步設定

::: moniker range="vs-2017"

您無法於不同 Visual Studio 並存安裝之間共用特定設定 (例如工具視窗配置)。 *%userprofile%\Documents\Visual Studio 2017\Settings* 中的 *CurrentSettings.vssettings* 檔案位於安裝特定資料夾中，類似於 *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*。

> [!NOTE]
> 若要使用新的安裝特定設定，請執行全新安裝。 當您升級現有的 Visual Studio 安裝時，它會使用現有的共用位置。

如果您目前有 Visual Studio 的並存安裝，並想要使用新的安裝特定設定檔位置，請遵循下列步驟：

1. 升級至 Visual Studio 2017 15.3 版或更新版本。

2. 使用 [匯入和匯出設定精靈] 將您所有現有設定匯出至 *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* 資料夾外的某個位置。

3. 開啟 [VS 2017 的開發人員命令提示字元]，並執行 `devenv /resetuserdata`。

1. 開啟 Visual Studio，並從匯出的設定檔中匯入儲存的設定。

::: moniker-end

::: moniker range=">=vs-2019"

您無法於不同 Visual Studio 並存安裝之間共用特定設定 (例如工具視窗配置)。 *%userprofile%\Documents\Visual Studio 2019\Settings* 中的 *CurrentSettings.vssettings* 檔案位於安裝特定資料夾中，類似於 *%localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Settings*。

::: moniker-end

## <a name="reset-synchronized-settings"></a>重設同步設定

若要將所有設定重設為預設值，請登入 Visual Studio，然後選取 [**工具** 匯  >  **入和匯出設定**] 以開啟 [匯 **入和匯出設定] Wizard**。 選取 [重設所有設定]，然後遵循精靈的其餘步驟進行。

## <a name="see-also"></a>另請參閱

- [個人化 IDE](../ide/personalizing-the-visual-studio-ide.md)
- [環境設定](../ide/environment-settings.md)
- [環境 > 帳戶選項對話方塊](reference/accounts-environment-options-dialog-box.md)
- [並存安裝 Visual Studio 版本](../install/install-visual-studio-versions-side-by-side.md)
