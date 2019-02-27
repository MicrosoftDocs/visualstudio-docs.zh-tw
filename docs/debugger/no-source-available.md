---
title: 沒有可用來源 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d1d1307a119fa23bf7ba015130ab9c7b6f69d5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703691"
---
# <a name="no-source-available"></a>沒有可用來源
您的專案未包含您嘗試檢視之程式碼的原始程式碼。 常見的原因為在 [呼叫堆疊] 視窗或 [執行緒] 視窗中，按兩下沒有原始程式碼的模組。 您可以繼續偵錯，但無法使用來源視窗設定中斷點，或是在此位置執行其他動作。 如果您必須設定中斷點，請改用 [反組譯碼] 視窗。

 在 [方案屬性頁] 中，您可以變更偵錯工具搜尋原始程式檔的目錄，並告知偵錯工具忽略選取的原始程式檔。 請參閱[偵錯來源檔案、 通用屬性、 方案屬性頁對話方塊](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)。

 **瀏覽以尋找原始程式碼**按一下這個連結即可開啟的對話方塊，您可以瀏覽以尋找原始程式碼。

 **顯示反組譯**會啟動**反組譯碼視窗**。

 **永遠顯示反組譯碼是否有遺漏的原始程式檔**選取此選項可顯示**反組譯碼視窗**自動沒有原始程式碼時可用。 這項設定也可以在 [選項] 對話方塊、[偵錯] 分類、[一般] 頁面中，透過選取或清除 [找不到可用的原始碼時顯示反組譯碼] 的方式變更。

## <a name="see-also"></a>請參閱
- [方案屬性頁對話方塊、通用屬性、偵錯原始程式檔](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (SOS 偵錯延伸模組)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)