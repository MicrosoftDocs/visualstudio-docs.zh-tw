---
title: 偵錯來源檔案、 通用屬性、 方案屬性頁對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83bed0588a0959ab85906d949e1b0752396223ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852921"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>方案屬性頁對話方塊、通用屬性、偵錯原始程式檔
此屬性頁可指定對方案進行偵錯時，偵錯工具將於何處尋找原始程式檔。

 若要存取 [偵錯來源檔案] 屬性頁，請以滑鼠右鍵按一下您在 [方案總管] 中的方案，然後從捷徑功能表選取 [屬性]。 展開 [通用屬性] 資料夾，然後按一下 [偵錯來源檔案] 頁面。

 **包含原始程式碼的目錄**包含在其中偵錯工具搜尋原始程式檔時偵錯方案的目錄清單。 另外也會搜尋所指定目錄的子目錄。

 **不會尋找這些原始程式檔**輸入任何您不想偵錯工具讀取的檔案名稱。 如果偵錯工具在上面其中一個指定的目錄中找到這些檔案中的某一個，就會忽略該檔案。 如果在進行偵錯時出現 [尋找原始碼] 對話方塊，而您按一下 [取消]，您之前搜尋的檔案就會新增至這個清單，如此偵錯工具就不會繼續搜尋該檔案。

## <a name="see-also"></a>另請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)