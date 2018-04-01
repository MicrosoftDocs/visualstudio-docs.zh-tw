---
title: 沒有可用來源 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a11770bc54a7b96aa918b73b34e0028731bf0f9c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="no-source-available"></a>沒有可用來源
您的專案未包含您嘗試檢視之程式碼的原始程式碼。 常見的原因按兩下沒有原始程式碼的模組**呼叫堆疊視窗**或**執行緒 視窗**。 您可以繼續偵錯，但無法使用來源視窗設定中斷點，或是在此位置執行其他動作。 如果您要設定中斷點，請使用**反組譯碼視窗**改為。  
  
 在 [方案屬性頁] 中，您可以變更偵錯工具搜尋原始程式檔的目錄，並告知偵錯工具忽略選取的原始程式檔。 請參閱[來源檔案、 通用屬性、 方案屬性頁對話方塊偵錯](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)。  
  
 **瀏覽以尋找原始程式碼**  
 按一下這個連結開啟對話方塊，您可以在其中瀏覽以尋找原始程式碼。  
  
 **顯示反組譯碼**  
 啟動**反組譯碼視窗**。  
  
 **永遠顯示反組譯碼遺漏的來源檔案**  
 選取此選項可顯示**反組譯碼視窗**自動當沒有來源可供使用時。 這項設定也可以變更在**選項**對話方塊中，**偵錯**類別，**一般**頁面上，選取或清除**顯示反組譯碼如果不到來源**。  
  
## <a name="see-also"></a>請參閱  
 [偵錯來源檔案、 通用屬性、 方案屬性頁對話方塊](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (SOS 偵錯延伸模組)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)