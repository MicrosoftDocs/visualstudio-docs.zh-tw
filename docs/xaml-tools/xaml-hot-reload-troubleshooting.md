---
title: 對 XAML 熱重新載入進行疑難排解
description: 修正使用 XAML 熱重載時可能會遇到的問題。
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 40be42871bac0a138d15b11b86f34419f2a6c67d
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535298"
---
# <a name="troubleshooting-xaml-hot-reload"></a>對 XAML 熱重新載入進行疑難排解

此疑難排解指南包含詳細的指示，可解決導致 XAML 熱重載無法正常運作的大部分問題。

WPF 和 UWP 應用程式支援 XAML 熱重載。 如需作業系統和工具需求的詳細資訊，請參閱[使用 Xaml 熱重載撰寫和](xaml-hot-reload.md)偵測執行 xaml 程式碼。

## <a name="hot-reload-is-not-available"></a>無法使用熱重載

如果您在偵錯工具時看到應用程式內的工具列中出現「無法使用熱重載」訊息，請遵循本文中所述的指示來解決此問題。

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>確認已啟用 XAML 熱重載

此功能預設為啟用。 當您開始對應用程式進行檢查時，請確定您看到應用程式內的工具列，確認可以使用 XAML 熱重載：

![可用的 XAML 熱重載](../debugger/media/xaml-hot-reload-available.png)

如果您看不到應用程式內的工具列，請開啟**Debug** > **選項**， > **一般**。 請確定已選取 [**啟用 xaml 的 UI 偵錯工具**] 和 [**啟用 xaml 熱重載**] 這兩個選項。

![啟用 XAML 熱重載](../debugger/media/xaml-hot-reload-enable.png)

如果選取這些選項，請移至 [即時視覺化樹狀] （**Debug** > **Windows** > **即時視覺化樹狀結構**），並確定已選取 [**在應用程式工具列中顯示執行時間工具**] 按鈕（在最左邊）。

![啟用 XAML 熱重載](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>確認您使用的是 [啟動偵錯工具]，而不是 [附加至進程]

XAML 熱重載需要在應用程式啟動時，環境變數 `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` 設為1。 Visual Studio 會在**Debug** > **開始調試**（或**F5**）命令中自動設定此項。 如果您想要在**Debug** >  [**附加至進程**] 命令時使用 XAML 熱重載，請自行設定環境變數。

> [!NOTE]
> 若要設定環境變數，請搜尋「環境變數」，然後選擇 [**編輯系統內容變數**]。 在開啟的對話方塊中，選擇 [**環境變數**]，然後將它新增為使用者變數，並將值設定為 [`1`]。 若要清除，請在完成調試時移除變數。

## <a name="verify-that-your-msbuild-properties-are-correct"></a>請確認您的 MSBuild 屬性是否正確

根據預設，[來源資訊] 會包含在 [偵錯工具] 設定中。 它是由專案檔（例如 * .csproj）中的 MSBuild 屬性所控制。 針對 WPF，屬性為 `XamlDebuggingInformation`，必須設定為 `True`。 對於 UWP，屬性為 `DisableXbfLineInfo`，必須設定為 `False`。 例如:

WPF

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>請確認您使用的是正確的組建設定名稱

您必須手動設定正確的 MSBuild 屬性以支援 XAML 熱重載（請參閱上一節），或者您必須使用預設的組建設定名稱（Debug）。 如果您未正確設定 MSBuild 屬性，自訂群組建設定名稱將無法運作，也不會有發行組建。

## <a name="verify-that-your-xaml-file-has-no-errors"></a>確認您的 XAML 檔案沒有錯誤

如果您的 XAML 檔案在**錯誤清單**中顯示錯誤，則 Xaml 熱重載可能無法正常執行。

## <a name="see-also"></a>請參閱

[使用 XAML 熱重載撰寫和偵測執行中的 XAML 程式碼](xaml-hot-reload.md)
