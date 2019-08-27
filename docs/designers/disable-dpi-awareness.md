---
title: 在 Visual Studio 中停用 DPI 感知
description: 討論在 HDPI 監視器上 Windows Form 設計工具的限制，以及如何以非 DPI 感知處理序方式執行 Visual Studio。
ms.date: 04/05/2019
author: gewarren
ms.author: gewarren
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: fdcf255b8ad7c613a83284759a1f4859041acfc4
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69619970"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>在 Visual Studio 中停用 DPI 感知

Visual Studio 是一種 DPI 感知應用程式，這表示顯示會自動縮放。 若應用程式表示其並非 DPI 感知，作業系統便會將應用程式作為點陣圖來縮放。 這種行為也稱為 DPI 虛擬化。 應用程式仍會認為其正在以 100% 的縮放比例執行 (或是 96 DPI)。

本文會討論在 HDPI 監視器上 Windows Form 設計工具的限制，以及如何以非 DPI 感知處理序方式執行 Visual Studio。

## <a name="windows-forms-designer-on-hdpi-monitors"></a>HDPI 監視器上的 Windows Form 設計工具

Visual Studio 中的 **Windows Form 設計工具**不支援縮放比例。 這會使您在高 DPI (HDPI) 監視器上的 **Windows Form 設計工具**中開啟某些表單時發生顯示問題。 例如，控制項看起來可能會互相重疊，如下圖所示：

![HDPI 監視器上的 Windows Form 設計工具](./media/win-forms-designer-hdpi.png)

當您在 HDPI 監視器的 Visual Studio 中，於 **Windows Form 設計工具**內開啟表單時，Visual Studio 會在設計工具的頂端顯示黃色的資訊列：

![Visual Studio 中的資訊列以非 DPI 感知模式重新啟動](./media/scaling-gold-bar.png)

訊息會顯示**您主要顯示器上的縮放比例已設為 200% (192 dpi)。這可能會在設計工具視窗中造成轉譯問題。**

> [!NOTE]
> 此資訊列是在 Visual Studio 2017 版本 15.8 引入的。

若您並未使用設計工具且不需要調整您表單的版面配置，您可以忽略資訊列並繼續在程式碼編輯器或其他類型的設計工具中工作。 (您也可以[停用通知](#disable-notifications)來停止顯示資訊列。)只有 **Windows Form 設計工具**會受到影響。 若您需要在 **Windows Form 設計工具**中工作，下一節可協助您[解決問題](#to-resolve-the-display-problem)。

## <a name="to-resolve-the-display-problem"></a>解決顯示問題

您有三個可用來解決顯示問題的選項：

- [以非 DPI 感知處理序方式重新啟動 Visual Studio](#restart-visual-studio-as-a-dpi-unaware-process)
- [新增登錄項目](#add-a-registry-entry)
- [將您的顯示縮放比例設定設為 100%](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>以非 DPI 感知處理序方式重新啟動 Visual Studio

您可以選取黃色資訊列上的選項，以非 DPI 感知處理序方式重新啟動 Visual Studio。 這是解決問題的慣用方法。

以非 DPI 感知處理序方式執行 Visual Studio 時，雖然可以解決設計工具的版面配置，但字體可能會相當模糊。 Visual Studio 會在以非 DPI 感知處理序方式執行時顯示不同黃色資訊列，提示您 **Visual Studio 正在以非 DPI 感知處理序方式執行。WPF 和 XAML 設計工具可能無法正常顯示。** 資訊列也會提供**以 DPI 感知處理序方式重新啟動 Visual Studio** 的選項。

> [!NOTE]
> - 當您選取以非 DPI 感知處理序方式重新啟動 Visual Studio 的選項時，若 Visual Studio 中有取消停駐的工具視窗，則這些工具視窗的位置可能會變更。
> - 若您使用預設的 Visual Basic 設定檔，或您在 [工具]   > [選項]   > [專案和解決方案]  中取消選取了 [在建立時儲存新的專案]  選項，Visual Studio 便無法在以非 DPI 感知處理序方式重新啟動時重新開啟您的專案。 但是，您可以在 [檔案]   > [最近使用的專案和解決方案]  下選取專案來開啟它。

當您在 **Windows Form 設計工具**中完成工作後，請務必以 DPI 感知處理序方式來重新啟動 Visual Studio。 以非 DPI 感知處理序方式執行時，字體看起來可能會相當模糊，且您可能會在其他設計工具 (例如 **XAML 設計工具**) 中發現問題。 若您在 Visual Studio 正在以非 DPI 感知模式執行時關閉並重新開啟 Visual Studio，則其會再次進入 DPI 感知狀態。 您也可以按一下資訊列中的 [將 Visual Studio 重新啟動為 DPI 感知處理序]  。

### <a name="add-a-registry-entry"></a>新增登錄項目

您可以修改登錄，將 Visual Studio 標記為非 DPI 感知。 請開啟**登錄編輯程式**，然後新增項目到 **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** 子機碼：

**項目**：請根據您使用的是 Visual Studio 2017 還是 2019，使用以下其中一個值：

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> 若您正在使用 Visual Studio Professional 或 Enterprise 版本，請在項目中將 **Community** 替換成 **Professional** 或 **Enterprise**。 同時也請視需要替換磁碟機代號。

**類型**：REG_SZ

**值**：DPIUNAWARE

> [!NOTE]
> Visual Studio 會維持在非 DPI 感知模式，直到您移除登錄機碼為止。

### <a name="set-your-display-scaling-setting-to-100"></a>將您的顯示縮放比例設定設為 100%

若要在 Windows 10 中將您的顯示縮放比例設定設為 100%，請在工作列搜尋方塊中鍵入**顯示設定**，然後選取 [變更顯示設定]  。 在 [設定]  視窗中，將 [變更文字、應用程式及其他項目的大小]  設為 [100%]  。

將顯示縮放比例設為 100% 可能不會是您想要的結果，因為它可能會讓使用者介面過小而無法使用。

## <a name="disable-notifications"></a>停用通知

您可以在 Visual Studio 中選擇不要接收 DPI 縮放比例問題的通知。 例如，若您沒有在設計工具中工作，您便可能會想要停用通知。

若要停用通知，請選擇 [工具]   > [選項]  來開啟 [選項]  對話方塊。 然後，請選擇 [Windows Form 設計工具]   > [一般]  ，然後將 [DPI 縮放比例通知]  設為 [False]  。

![Visual Studio 中的 DPI 縮放比例通知選項](./media/notifications-option.png)

若您稍後想要重新啟用縮放比例通知，請將屬性設為 [True]  。

## <a name="troubleshoot"></a>疑難排解

若 DPI 感知轉換在 Visual Studio 中並未如您預期的方式運作，請檢查您在登錄編輯程式的 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** 子機碼中是否有 `dpiAwareness` 值。 若有的話，請刪除該值。

## <a name="see-also"></a>另請參閱

- [Windows Forms 內的自動縮放比例](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)