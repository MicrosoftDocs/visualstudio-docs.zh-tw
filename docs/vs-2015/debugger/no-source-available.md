---
title: 沒有可用來源 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69ea9c3a41f83b9c06dc18d6da1f859017f12ca5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697802"
---
# <a name="no-source-available"></a>沒有可用來源
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您的專案未包含您嘗試檢視之程式碼的原始程式碼。 常見的原因為在 [呼叫堆疊] 視窗或 [執行緒] 視窗中，按兩下沒有原始程式碼的模組。 您可以繼續偵錯，但無法使用來源視窗設定中斷點，或是在此位置執行其他動作。 如果您必須設定中斷點，請改用 [反組譯碼] 視窗。  
  
 在 [方案屬性頁] 中，您可以變更偵錯工具搜尋原始程式檔的目錄，並告知偵錯工具忽略選取的原始程式檔。 請參閱[偵錯來源檔案、 通用屬性、 方案屬性頁對話方塊](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)。  
  
 **瀏覽以尋找原始程式碼**  
 按一下這個連結開啟對話方塊，您可以在其中瀏覽以尋找原始程式碼。  
  
 **顯示反組譯碼**  
 啟動 [反組譯碼] 視窗。  
  
 **永遠顯示遺漏來源檔案的反組譯碼**  
 選取這個選項以在沒有原始程式碼可用時，自動顯示 [反組譯碼] 視窗。 這項設定也可以在 [選項] 對話方塊、[偵錯] 分類、[一般] 頁面中，透過選取或清除 [找不到可用的原始碼時顯示反組譯碼] 的方式變更。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯來源檔案、通用屬性、方案屬性頁對話方塊](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (SOS 偵錯延伸模組)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
