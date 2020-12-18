---
title: 無法設定資料中斷點 |Microsoft Docs
ms.date: 12/3/2019
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 4cded3bfdb6adc206f02ef54402964f4e7276f93
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668777"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>針對資料中斷點錯誤進行疑難排解
此頁面將逐步引導您解決在使用「值變更時中斷」時所看到的常見錯誤

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>診斷「無法設定資料中斷點」錯誤
> [!IMPORTANT]
> .NET Core 3.0 和更新的支援 Managed 資料中斷點。 您可以在 [這裡](https://dotnet.microsoft.com/download)下載最新版本。

以下是使用 managed 資料中斷點時可能發生的錯誤清單。 其中包含錯誤發生原因的其他說明，以及解決錯誤的可能解決方案或因應措施。

- *「目標進程所使用的 .NET 版本不支援資料中斷點。資料中斷點需要在 x86 或 x64 上執行的 .NET Core 3.0 +。」*

  - Managed 資料中斷點的支援是從 .NET Core 3.0 開始。 在3.0 下的 .NET Core .NET Framework 或版本中，目前不支援此功能。 
    
  - **解決方案**：解決方法是將您的專案升級至 .net Core 3.0。

- *「在 managed 堆積上找不到值，因此無法追蹤。」*
  - 在堆疊上宣告的變數。
    - 我們不支援在堆疊上建立的變數設定資料中斷點，因為一旦函式結束之後，這個變數就會無效。
    - 因應 **措施：在** 使用變數的程式列上設定中斷點。

  - 不是從下拉式清單展開的變數上的「當值變更時中斷」。
    - 偵錯工具會在內部需要知道包含您要追蹤之欄位的物件。垃圾收集行程可能會在堆積中移動您的物件，讓偵錯工具必須知道持有您要追蹤之變數的物件。 
    - 因應 **措施：如果** 您是在您想要設定資料中斷點的物件內的方法中，請移至一個框架，然後使用此 `locals/autos/watch` 視窗來展開物件，並將您想要的欄位設定為數據中斷點。

- *「靜態欄位或靜態屬性不支援資料中斷點。」*
    
  - 目前不支援靜態欄位和屬性。 如果您對這項功能有興趣，請提供 [意見](#provide-feedback)反應。

- *「無法追蹤結構的欄位和屬性。」*

  - 目前不支援結構的欄位和屬性。 如果您對這項功能有興趣，請提供 [意見](#provide-feedback)反應。

- *「屬性值已變更且無法再追蹤。」*

  - 屬性可能會變更在執行時間期間的計算方式，如果發生這種情況，屬性相依的變數數目會增加，而且可能會超過硬體限制。 請參閱下文中的 `"The property is dependent on more memory than can be tracked by the hardware."`。

- *「屬性相依于硬體所能追蹤的記憶體。」*
    
  - 每個架構都有一組可支援的位元組數和硬體資料中斷點，以及您想要設定資料中斷點的屬性已超過該限制。 請參閱 [資料中斷點硬體限制](#data-breakpoint-hardware-limitations) 表格，以瞭解有多少硬體支援的資料中斷點和位元組可供您使用的架構使用。 
  - 因應 **措施：在** 可能會在屬性內變更的值上設定資料中斷點。

- *「使用舊版 c # 運算式評估工具時，不支援資料中斷點」。*

  - 只有非舊版 c # 運算式評估工具支援資料中斷點。 
  - **解決方案**：若要停用舊版 c # 運算式評估工具，請前往 [取消核取] `Debug -> Options` 下 `Debugging -> General` `"Use the legacy C# and VB expression evaluators"` 。

## <a name="data-breakpoint-hardware-limitations"></a>資料中斷點硬體限制

您的程式執行所在的架構 (平臺設定) ，其可使用的硬體資料中斷點數目有限。 下表指出每個架構可使用的暫存器數目。

| 架構 | 支援的硬體資料中斷點數目 | 最大位元組大小|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>提供意見反應

對於這項功能的任何問題或建議，請透過 [說明] 讓我們知道 > 傳送意見反應 > 在 IDE 或[開發人員社群](https://aka.ms/feedback/suggest?space=8)中回報[問題](../ide/how-to-report-a-problem-with-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [使用 .Net Core 3.0 中的「值變更時中斷](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)」。
- [DevBlog：當值變更時中斷： Visual Studio 2019 中的 .NET Core 資料中斷點](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
