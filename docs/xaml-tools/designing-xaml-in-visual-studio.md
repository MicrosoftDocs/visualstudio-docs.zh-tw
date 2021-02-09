---
title: 在 Visual Studio 和 Blend for Visual Studio 中設計 XAML
titleSuffix: ''
description: 瞭解 Visual Studio 中的視覺化設計工具，以及如何在 XAML 中建立 UI 和體驗 Blend for Visual Studio 的功能。
ms.custom: SEO-VS-2020
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: fc6c05b925c8dac5c488ce3eea79ca683b590b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876416"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>在 Visual Studio 與 Blend for Visual Studio 中設計 XAML

Visual Studio 和 Blend for Visual Studio 都提供視覺化工具，用於為各種應用程式類型建立更吸引人的使用者介面和豐富的媒體體驗。 這兩個整合式開發環境 (IDE) 共用一組通用的功能，包括視覺化 XAML 編輯器 (設計工具)。 Blend for Visual Studio (支援 WPF 與 UWP 平台) 提供額外的工具來設計視覺狀態和建立動畫。

您可以在 Visual Studio 與 Blend for Visual Studio 之間來回切換，甚至可以在這兩個 IDE 中同時開啟相同的專案。 如果在一個 IDE 中將變更儲存至 XAML 檔案，當您切換到另一個 IDE 時，透過自動重新載入即可套用那些變更。 您可以流覽至  >    >    >  任一 IDE 中的 [工具選項] 環境 **檔**，以控制重載行為。

## <a name="installation"></a>安裝

- 若要建立 WPF 應用程式，請安裝 Visual Studio 中的 [.NET 桌面開發] 工作負載。 此外，也將安裝 Blend for Visual Studio。

     ![Visual Studio 安裝程式的 .NET 桌面開發工作負載螢幕擷取畫面](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- 若要建立 UWP 應用程式，請安裝 Visual Studio 中的 [通用 Windows 平台開發] 工作負載。 此外，也將安裝 Blend for Visual Studio。

     ![從 Visual Studio 安裝程式通用 Windows 平臺開發工作負載的螢幕擷取畫面](../xaml-tools/media/uwp-workload.png)

- 若要建立 Xamarin.Forms 應用程式，請安裝 Visual Studio 中的 [使用 .NET 進行行動開發] 工作負載。 「不」安裝 Blend for Visual Studio；Blend 並不支援 Xamarin.Forms 應用程式。

     ![從 Visual Studio 安裝程式的 .NET 工作負載進行行動裝置開發的螢幕擷取畫面](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>共用功能

就大多數基本開發工作而言，Visual Studio 與 Blend for Visual Studio 共用一組相同的視窗和功能，但有些微差異。 一些重點包括：

- **IntelliSense：** 這兩個 Ide 都支援 IntelliSense 功能，例如語句完成。

- **調試：** 您可以在 [Visual Studio](inspect-xaml-properties-while-debugging.md) 和 [Blend for Visual Studio](../xaml-tools/debug-xaml-in-blend.md)中進行偵錯工具，包括在程式碼中設定中斷點，以在應用程式執行時，對執行中的應用程式進行偵錯工具，以及使用 [熱重新載入](../xaml-tools/xaml-hot-reload.md) 變更 XAML 程式碼。 為了維持與 Visual Studio 一致的偵錯體驗，Blend for Visual Studio 包含大部分的 Visual Studio 偵錯視窗和工具列。

- 檔案 **重載：** 您可以在 Visual Studio 或 Blend for Visual Studio 中編輯 XAML 檔案。 當您在兩個 IDE 之間切換時，編輯過且已儲存的檔案會自動重新載入。 您可以流覽至  >    >    >  任一 IDE 中的 [工具選項] 環境 **檔**，以控制重載行為。

- 已 **同步處理的版面配置和設定：** 當您使用相同的個人化帳戶登入時，針對 Visual Studio 或 Blend for Visual Studio 的設計自訂工具視窗配置和設定喜好設定，會在您的裝置和版本之間進行同步處理。 請參閱[跨多部電腦同步處理設定](../ide/synchronized-settings-in-visual-studio.md)。

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Blend for Visual Studio 中的進階功能

若要提升產能，請考慮使用 Blend for Visual Studio 來處理下列工作。 這些都是 Blend for Visual Studio 可提供比 Visual Studio 設計工具或程式碼本身更多功能之處。

| Task | Visual Studio | Blend for Visual Studio | 詳細資訊 |
| - | - | - | - |
| **設計視覺狀態** | 沒有任何工具可協助您設計視覺狀態；您必須以程式設計方式建立它們。 | 使用設計工具來根據控制項的狀態變更其外觀。 | [視覺狀態](modify-the-style-of-objects-in-blend.md#visual-states) |
| **建立動畫** |動畫沒有設計工具，您必須以程式設計方式來建立動畫。 這需要了解動畫、WPF 中的計時系統以及大量編碼專業知識。|您能以視覺化方式建立動畫，並在 Blend for Visual Studio 中預覽。 這比在程式碼中建置動畫來得更多更精準。 您可以新增觸發程序來處理使用者互動，而且可以切換到程式碼以加入事件處理常式和其他功能。|[製作物件動畫](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**將圖形和文字轉換成更容易操作的路徑**|不支援。|您可以將圖形轉換成路徑，使其更好編輯控制，藉此稍微或大幅變更圖形 (例如矩形和橢圓形)。 您可以調整形狀或合併路徑，並從多個圖形中建立複合路徑。<br /><br />您也可以將文字區塊轉換成路徑，以便做為向量影像來操作。|[繪製圖案與路徑](../xaml-tools/draw-shapes-and-paths.md)|
|**編輯控制項、範本和樣式**|需要編碼並具備 WPF 樣式和範本的知識。|將任何影像轉換成控制項。<br /><br />只要按幾下滑鼠，即可使用範本編輯工具來變更控制項、樣式和範本。<br /><br />例如，您可以使用 Blend for Visual Studio 樣式資源來實作常見 WPF 控制項 (例如按鈕、清單方塊，捲軸列、功能表等)，並直接在 Blend for Visual Studio 中變更其色彩、樣式或基礎範本。 之後如果想要的話，您可以切換到程式碼做最後修飾。|[修改物件的樣式](modify-the-style-of-objects-in-blend.md)|
|**將 UI 連接到資料**|您可以從資源 (例如 SQL Server 資料庫、WCF 或 Web 服務、物件或 SharePoint 清單) 建立資料來源，然後將資料來源繫結至 UI 控制項。<br /><br />設計階段資料必須以手動方式建立才能獲得互動式的設計體驗。|針對 .NET Framework 應用程式，輕鬆建立範例資料來進行原型設計和測試。 準備好時切換到即時資料。<br /><br />Blend for Visual Studio 的資料產生功能相當傑出 (您可以輕鬆地即時新增名稱、數字、URL、相片)，為您節省許多時間。<br /><br />對於即時資料，您可以將 UI 控制項繫結至 XML 檔案，或任何 CLR 資料來源。|[顯示資料](display-data-in-blend.md)|

如需進階 XAML 設計的詳細資訊，請參閱[使用 Blend for Visual Studio 建立 UI](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [XAML 概觀](xaml-overview.md)
- [Blend for Visual Studio 概觀](creating-a-ui-by-using-blend-for-visual-studio.md)
