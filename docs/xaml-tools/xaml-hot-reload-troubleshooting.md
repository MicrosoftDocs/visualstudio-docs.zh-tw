---
title: 對 XAML 熱重新載入進行疑難排解
description: 修正 XAML 熱重新載入可能遇到的問題。
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e13fd71c9d53ef49d7f7372986bfabc29c62747
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890444"
---
# <a name="troubleshooting-xaml-hot-reload"></a>對 XAML 熱重新載入進行疑難排解

這份疑難排解指南包含的詳細指示，應可解決導致 XAML 熱重新載入無法正確運作的大部分問題。

WPF 和 UWP 應用程式支援 XAML 熱重新載入。 如需作業系統和工具需求的詳細資訊，請參閱 [使用 XAML 熱重新載入撰寫和](xaml-hot-reload.md)偵測執行中的 XAML 程式碼。

## <a name="hot-reload-is-not-available"></a>熱重新載入無法使用

如果您在對應用程式進行偵錯工具時，在應用程式中的工具列看到「無法使用熱重新載入」訊息，請遵循本文中所述的指示來解決問題。

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>確認已啟用 XAML 熱重新載入

預設會啟用此功能。 當您開始對應用程式進行偵錯工具時，請確定您看到應用程式內的工具列，確認 XAML 熱重新載入可供使用：

![XAML 熱重新載入可用](../debugger/media/xaml-hot-reload-available.png)

如果您看不到應用程式內工具列，請開啟  >    >  **[一般**] 偵錯工具選項。 請確定已選取 [ **啟用 XAML 的 UI 偵錯工具** ] 和 [ **啟用 XAML 熱重新載入** 的兩個選項。

![[Visual Studio 偵錯工具選項] 視窗的螢幕擷取畫面。 選取 [一般偵錯工具] 選項，並勾選 [啟用 XAML 熱重新載入] 選項。](../debugger/media/xaml-hot-reload-enable.png)

如果選取這些選項，請移至 [即時視覺化樹狀] (**Debug**  >  **Windows**  >  **Live 視覺化樹狀結構**) 並確定已選取) [在 **應用程式中顯示執行時間工具**] 工具列按鈕 (。

![在 [即時視覺化樹狀結構] 視窗頂端的工具列螢幕擷取畫面，其中已選取 [在應用程式中顯示執行時間工具] 按鈕。](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>確認您使用開始偵錯工具，而不是附加至進程

XAML 熱重新載入要求在 `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` 應用程式啟動時，環境變數設為1。 Visual Studio 在「**調試** 程式  >  **啟動調試** 程式 (或 **F5**) 命令中自動設定此項。 如果您想要改用 XAML 熱重新載入搭配 **Debug**  >  **Attach to Process** 命令，請自行設定環境變數。

> [!NOTE]
> 若要設定環境變數，請使用 [開始] 按鈕來搜尋「環境變數」，然後選擇 [ **編輯系統內容變數**]。 在開啟的對話方塊中，選擇 [ **環境變數**]，然後將它新增為使用者變數，並將值設定為 `1` 。 若要清除，請在完成調試時移除變數。

## <a name="verify-that-your-msbuild-properties-are-correct"></a>確認您的 MSBuild 屬性正確

依預設，來源資訊會包含在「偵錯工具」設定中。 它是由專案檔中的 MSBuild 屬性所控制 (例如 * .csproj) 。 針對 WPF，屬性是 `XamlDebuggingInformation` ，必須設定為 `True` 。 針對 UWP，屬性為 `DisableXbfLineInfo` ，其必須設定為 `False` 。 例如：

WPF：

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>確認您使用正確的組建設定名稱

您必須手動設定正確的 MSBuild 屬性以支援 XAML 熱重新載入 (請參閱上一節) ，或者您必須使用預設組建設定名稱 (Debug) 。 如果您未正確設定 MSBuild 屬性，自訂群組建設定名稱將不會運作，也不會發行組建。

## <a name="verify-that-your-xaml-file-has-no-errors"></a>確認您的 XAML 檔案沒有任何錯誤

如果您的 XAML 檔案顯示 **錯誤清單** 中的錯誤，XAML 熱重新載入可能無法運作。

## <a name="see-also"></a>另請參閱

[使用 XAML 熱重新載入撰寫和偵測執行中的 XAML 程式碼](xaml-hot-reload.md)
