---
title: 取得字型和色彩資訊文字的顏色標示 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f5d66a2baada5841dc6a0edefb6fa759168bcb5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924080"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>取得文字顏色標示的字型和色彩資訊
呈現，或在使用者介面 (UI) 項目中顯示彩色的文字的程序取決於專案、 技術和開發人員的喜好設定的類型。 **字型和色彩**屬性頁會將設定儲存。

 需要顯示彩色的文字的大部分實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>和相關聯的呈現、 擷取和儲存文字顯示設定的介面。

> [!NOTE]
>  當自訂核心編輯器 (支援**文字 EditorCategory**)，建議您在語言服務中使用著色技術。 如需詳細資訊，請參閱 <<c0> [ 字型和色彩概觀](../extensibility/font-and-color-overview.md)。

## <a name="get-default-font-and-color-information"></a>取得預設字型和色彩資訊
 所有**字型和色彩**應指定設定的任何視窗，以顯示文字**顯示項目**之一**分類**。 如需詳細資訊，請參閱 <<c0> [ 字型和色彩、 環境、 選項對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。

若要以色彩標示，VSPackage 必須取得目前**字型和色彩**設定。 VSPackage 可以取得目前的設定，以下列方式，根據其需求：

-   您可以使用的字型和色彩的持續性機制來擷取預存] 或 [目前狀態。 如需詳細資訊，請參閱 <<c0> [ 預存的存取字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。

-   使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面的服務，可提供要取得的執行個體的字型和色彩資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>，如果 VSPackage 也不是字型和色彩提供者。

-   實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 介面。

若要確保透過輪詢所得到的結果是最新狀態，可能會使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以判斷更新是否需要在呼叫的擷取方法之前<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。

取得字型和色彩資訊之後，剖析來識別需要顏色標示的項目要顯示的文字。 使用適當的字型和色彩 視窗中顯示的文字。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [使用字型和文字](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [使用色彩](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI （繪圖裝置介面）](https://msdn.microsoft.com/library/7e1d4540-bb2e-4257-8eee-eee376acba83)