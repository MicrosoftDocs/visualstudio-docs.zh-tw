---
title: 沒有可用的來源 |Microsoft Docs
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
ms.openlocfilehash: 9f08ed499e61e54ffbc6508bc8353ea955d9a20c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730865"
---
# <a name="no-source-available"></a>沒有可用來源
您的專案未包含您嘗試檢視之程式碼的原始程式碼。 常見的原因為在 [呼叫堆疊] 視窗或 [執行緒] 視窗中，按兩下沒有原始程式碼的模組。 您可以繼續偵錯，但無法使用來源視窗設定中斷點，或是在此位置執行其他動作。 如果您必須設定中斷點，請改用 [反組譯碼] 視窗。

 在 [方案屬性頁] 中，您可以變更偵錯工具搜尋原始程式檔的目錄，並告知偵錯工具忽略選取的原始程式檔。 請參閱[Debug Source Files、通用屬性、方案屬性頁對話方塊](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)。

 **流覽以尋找原始程式碼**按一下此連結即可開啟對話方塊，您可以在其中流覽以尋找原始程式碼。

 **顯示**反組解碼啟動 [反組解碼 **] 視窗**。

 **一律顯示遺漏原始程式檔的**反組解碼選取此選項，可在沒有來源可用時自動顯示 [反組解碼 **] 視窗**。 這項設定也可以在 [選項] 對話方塊、[偵錯] 分類、[一般] 頁面中，透過選取或清除 [找不到可用的原始碼時顯示反組譯碼] 的方式變更。

## <a name="see-also"></a>請參閱
- [方案屬性頁對話方塊、通用屬性、偵錯原始程式檔](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (SOS 偵錯延伸模組)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)