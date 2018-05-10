---
title: 在 Visual Studio 中同步處理設定
ms.date: 01/23/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91c8c931d71855913cdfaca4243711c917e3c8b4
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="synchronize-your-settings-in-visual-studio"></a>在 Visual Studio 中同步處理設定

當您使用相同的個人化帳戶在多部電腦上登入 Visual Studio 時，根據預設所有電腦皆會同步處理您的設定。

## <a name="synchronized-settings"></a>同步設定

預設會同步處理下列設定。

- 開發設定 (您必須在第一次執行 Visual Studio 時選取一組設定，但是可以隨時變更選取範圍。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md))。

- 位於 [工具] > [選項] 頁面的下列選項：

    - [環境] > [一般] 選項頁面上的主題和功能表列大小寫設定

    - [環境] > [字型和色彩] 選項頁面上的所有設定

    - [環境] > [鍵盤] 選項頁面上的所有鍵盤快速鍵

    - [環境] > [索引標籤和視窗] 選項頁面上的所有設定

    - [環境] > [啟動] 選項頁面上的所有設定

    - [文字編輯器] 選項頁面上的所有設定

    - [XAML 設計工具] 選項頁面上的所有設定

- 使用者定義的命令別名。 如需有關如何定義命令別名的詳細資訊，請參閱 [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。

- [視窗] > [管理視窗配置] 頁面中的使用者定義視窗配置

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>關閉特定電腦的同步設定

Visual Studio 的同步設定預設為開啟。 您可以移至 [工具] > [選項] > [環境] > [帳戶] 頁面，然後取消勾選核取方塊，就可以關閉電腦的同步設定。  例如，如果您決定不要同步處理電腦 A 上 Visual Studio 的設定，則任何在電腦 A 上的設定變更都不會出現在電腦 B 或電腦 C 上。電腦 B 和 C 會繼續互相同步處理，但不會和電腦 A 同步。

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>同步處理 Visual Studio 系列產品和版本之間的設定

可同步處理任何 Visual Studio 版本 (包含 Community 版本) 之間的設定。 也會同步處理 Visual Studio 系列產品之間的設定。 不過，這些系列產品中的每一個都可能有它自己不會與 Visual Studio 共用的設定。 例如，電腦 A 的某個產品專屬設定會和電腦 B 的另一個產品專屬設定共用，但不會和電腦 A 或 B 上的 Visual Studio 共用。

## <a name="side-by-side-synchronized-settings"></a>並存同步設定

在 Visual Studio 15.3 和更新的版本中，我們會將 *%userprofile%\Documents\Visual Studio 2017\Settings* 中的 *CurrentSettings.vssettings* 檔案位置變更為類似 *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings* 的安裝特定資料夾，以便停止 Visual Studio 2017 並存安裝之間共用的特定設定，例如工具視窗配置。

> [!NOTE]
> 若要使用新的安裝特定設定，您必須完成全新安裝。 當您將現有的 Visual Studio 2017 安裝升級為最新的更新時，它會使用現有的共用位置。 如果您目前有 Visual Studio 2017 的並存安裝，並決定進行升級，而且想要使用新的安裝特定設定檔案位置，請遵循這些步驟：

1. 升級後，使用**匯入/匯出設定**精靈，將所有現有設定匯出至 *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx* 資料夾外的某個位置。
2. 開啟已升級 Visual Studio 安裝的**適用於 VS 2017 的開發人員命令提示字元**，並從中執行 `devenv /resetuserdata`。
3. 啟動 Visual Studio，並從匯出的設定檔匯入儲存的設定。

## <a name="see-also"></a>另請參閱

[個人化 IDE](../ide/personalizing-the-visual-studio-ide.md)
