---
title: XAML 設計工具選項頁面
ms.date: 03/02/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2ef58fb7b1f58eb9d7618981251bdc7981142500
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315536"
---
# <a name="xaml-designer-options-page"></a>XAML 設計工具選項頁面

使用 [XAML 設計工具] 選項頁面來指定如何設定 XAML 文件中元素和屬性的格式。 若要開啟此頁面，請選擇 [工具] 功能表，然後選擇 [選項]。 若要存取 [XAML 設計工具] 屬性頁面，請選擇 [XAML 設計工具] 節點。 當您開啟文件時，會套用 XAML 設計工具的設定。 因此，若要變更設定，您需要關閉然後重新開啟 Visual Studio，才能看到變更。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[重設設定](../environment-settings.md#reset-settings)。

## <a name="enable-xaml-designer"></a>啟用 XAML 設計工具

選取時，此設定會啟用 XAML 設計工具。 XAML 設計工具提供視覺化工作區，讓您編輯 XAML 文件。 Visual Studio 中的特定功能，例如資源與資料繫結的 IntelliSense，需要啟用 XAML 設計工具。

只有在啟用 XAML 設計工具時，下列設定才適用。 如果您變更這個選項，必須重新啟動 Visual Studio，設定才會生效。

## <a name="default-document-view"></a>預設文件檢視

使用此設定可控制載入 XAML 文件時是否出現設計檢視。

|||
|-|-|
|**原始碼檢視**|指定是否只有 XAML 原始碼會出現在 XAML 檢視。 載入大型文件時，這非常有用。|
|**設計檢視**|指定是否只有視覺化 XAML 設計工具會出現在 XAML 檢視。|
|**分割檢視**|指定是否視覺化 XAML 設計工具和 XAML 原始碼相鄰出現在 XAML 檢視中 (位置根據 [分割方向] 設定)。|

## <a name="split-orientation"></a>分割方向

使用此設定可控制編輯 XAML 文件時，何時以及如何顯示 XAML 設計工具。 這些設定只適用於 [預設文件檢視] 設為 [分割檢視] 時。

|||
|-|-|
|**垂直**|XAML 原始碼出現在 XAML 檢視的左邊，另一邊則出現 XAML 設計工具。|
|**水平**|XAML 設計工具會顯示在 XAML 檢視的頂端，XAML 原始碼出現在它下方。|
|**Default**|XAML 文件會使用文件專案之目標平台的建議分割方向。 對於大部分的平台，這相當於 [水平]。|

## <a name="zoom-by-using"></a>縮放方式

使用此設定可決定編輯 XAML 文件時，縮放的運作方式。

|||
|-|-|
|**滑鼠滾輪**|捲動滑鼠滾輪來放大 XAML 設計工具。|
|**CTRL + 滑鼠滾輪**|按住 **Ctrl** 鍵同時捲動滑鼠滾輪，來放大 XAML 設計工具。|
|**Alt + 滑鼠滾輪**|按住 **Alt** 鍵同時捲動滑鼠滾輪，來放大 XAML 設計工具。|

這些設定會決定編輯 XAML 文件時的設計工具行為。

|||
|-|-|
|**建立時自動命名互動元素**|指定當您將互動元素新增至設計工具時，是否要提供新互動元素的預設名稱。|
|**自動在建立元素時插入配置屬性**|指定當您將新項目新增至設計工具時，是否要提供新項目的配置屬性。 配置屬性就是會影響控制項配置的屬性，例如 Margin 和 VerticalAlignment。 下列 XAML 顯示選取此選項與不選取此選項時建立按鈕的方式：<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**使用四分色配置**|指定目前選取的控制項是否對齊父容器的最近邊緣。 如果清除此核取方塊，則控制項對齊方式不會在移動或建立作業期間變更。|
|**自動填入工具箱項目**|指定目前方案中的使用者控制項和自訂控制項是否自動顯示在工具箱。|

## <a name="settings-blend-only"></a>設定 (僅 Blend)

使用這些選項可決定使用 Blend 編輯 XAML 檔案時的設定。

|||
|-|-|
|**縮放方式**|捲動滑鼠滾輪，或者按住 **Ctrl** 或 **Alt** 鍵並同時捲動滑鼠滾輪，來放大 XAML 設計工具。|
|**類型單位**|指定設計工具上的度量單位是根據點數還是像素。 因為通用 Windows 應用程式不支援點，所以如果選取 [點]，單位會自動轉換為像素。|

## <a name="artboard-blend-only"></a>畫板 (僅 Blend)

使用這些設定可決定在 Blend 中編輯 XAML 文件時的 XAML 設計工具行為。

### <a name="snapping"></a>貼齊

|||
|-|-|
|**顯示貼齊格線**|選取此選項時，設計工具中會顯示格線，幫助您對齊控制項。 選取 [貼齊格線] 選項時，新增到設計工具的控制項會貼齊這些格線。|
|**貼齊格線**|在設計工具新增或移動控制項時，它們會貼齊格線。|
|**格線間距**|以像素或點為單位 (由 [類型單位] 設定所決定)，指定格線之間的間距。|
|**貼齊對齊線**|指定控制項是否貼齊對齊線。|
|**預設邊界**|啟用 [貼齊對齊線] 時，以像素或點為單位 (由 [類型單位] 設定所決定)，指定控制項和對齊線之間的間距。|
|**預設邊框間距**|啟用 [貼齊對齊線] 時，以像素或點為單位 (由 [類型單位] 設定所決定)，指定控制項和對齊線之間的額外間距。|

### <a name="animation"></a>動畫

使用此設定可決定在 Blend 中啟用相依 (未加速) 動畫時，是否會出現警告。

### <a name="effects"></a>效果

使用這些設定可決定使用 Blend 在 XAML 設計工具中編輯 XAML 檔案時，是否呈現效果。

|||
|-|-|
|**呈現效果**|指定使用 Blend 在 XAML 設計工具中編輯 XAML 檔案時，是否呈現效果。|
|**縮放臨界值**|指定當選取 [呈現效果] 核取方塊時，效果呈現所使用的縮放百分比。 如果放大超過此設定，效果將不再呈現於 XAML 設計工具中。|

## <a name="see-also"></a>另請參閱

- [WPF 中的 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [逐步解說：我的第一個 WPF 傳統型應用程式](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)