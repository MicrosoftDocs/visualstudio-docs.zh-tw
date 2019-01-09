---
title: 同步處理設定
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 107b1096f694e0dc784181eae675a0c1a2285726
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935199"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>跨多部電腦同步處理 Visual Studio 設定

當您使用相同的個人化帳戶在多部電腦上登入 Visual Studio 時，可以跨電腦同步處理您的設定。

## <a name="synchronized-settings"></a>同步設定

預設會同步處理下列設定：

- 開發設定。 您需要在第一次開啟 Visual Studio 時選取設定集合，但是可以隨時變更選取範圍。 如需詳細資訊，請參閱[環境設定](../ide/environment-settings.md)。

- 使用者定義的命令別名。 如需有關如何定義命令別名的詳細資訊，請參閱 [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。

- [視窗] > [管理視窗配置] 頁面中的使用者定義視窗配置。

- 位於 [工具] > [選項] 頁面的下列選項：

   - [環境] > [一般] 選項頁面上的主題和功能表列大小寫設定。

   - [環境] > [字型和色彩] 選項頁面上的所有設定。

   - [環境] > [鍵盤] 選項頁面上的所有鍵盤快速鍵。

   - [環境] > [索引標籤和視窗] 選項頁面上的所有設定。

   - [環境] > [啟動] 選項頁面上的所有設定。

   - [文字編輯器] 選項頁面上的所有設定。

   - [XAML 設計工具] 選項頁面上的所有設定。

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>關閉特定電腦的同步設定

Visual Studio 的同步設定預設為開啟。 您可以移至 [工具] > [選項] > [環境] > [帳戶] 頁面，然後取消勾選 [登入 Visual Studio 時同步處理多部裝置的設定]，即可關閉電腦的同步設定。

例如，如果您決定不要同步處理電腦 "A" 上 Visual Studio 的設定，則任何在電腦 "A" 上面的設定變更都不會出現在電腦 "B" 或電腦 "C" 上。 電腦 "B" 和 "C" 會繼續互相同步處理，但不會和電腦 "A" 同步。

> [!NOTE]
> 如果您取消選取 [工具] > [選項] > [環境] > [帳戶] 頁面上的選項而選擇不要同步處理設定，您在同一部電腦上所擁有的其他版本 Visual Studio 不會受到影響。 Visual studio 的那些並存安裝將繼續同步處理其設定 (除非您也在該處取消選取選項)。

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>同步處理 Visual Studio 系列產品和版本之間的設定

設定會在「並存」安裝的 Visual Studio 版本之間同步處理。 Visual Studio 系列產品中 (包括 Blend for Visual Studio) 的設定也會同步處理。 不過，個別系列產品可能有它自己不會與 Visual Studio 共用的設定。 例如，電腦 A 上的 Blend for Visual Studio 專屬設定不會和電腦 A 或 B 上的 Visual Studio 共用。

## <a name="side-by-side-synchronized-settings"></a>並存同步設定

在 Visual Studio 2017 15.3 版和更新版本中，不會在不同的 Visual Studio 2017 並存安裝之間共用特定設定 (例如工具視窗配置)。 *%userprofile%\Documents\Visual Studio 2017\Settings* 中的 *CurrentSettings.vssettings* 檔案位於安裝特定資料夾中，類似於 *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*。

> [!NOTE]
> 若要使用新的安裝特定設定，請執行全新安裝。 當您將現有的 Visual Studio 2017 安裝升級為最新的更新時，它會使用現有的共用位置。

如果您目前有 Visual Studio 2017 的並存安裝，並且想要使用新的安裝特定設定檔案位置，請遵循下列步驟：

1. 升級至 Visual Studio 2017 15.3 版或更新版本。

1. 使用 [匯入\匯出設定精靈] 將您所有現有的設定匯出至 *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* 資料夾外的某個位置。

1. 開啟已升級 Visual Studio 安裝的**適用於 VS 2017 的開發人員命令提示字元**，並執行 `devenv /resetuserdata`。

1. 啟動 Visual Studio，並從匯出的設定檔匯入儲存的設定。

## <a name="see-also"></a>另請參閱

- [個人化 IDE](../ide/personalizing-the-visual-studio-ide.md)
- [環境設定](../ide/environment-settings.md)
- [環境 > 帳戶選項對話方塊](reference/accounts-environment-options-dialog-box.md)
