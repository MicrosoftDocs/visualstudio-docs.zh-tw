---
title: '[調試原始檔]/[通用屬性]/[方案屬性頁]'
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
ms.openlocfilehash: 735432db485277e2265479e625f5e8acaa2cc2e3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738392"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>方案屬性頁對話方塊、通用屬性、偵錯原始程式檔
此屬性頁可指定對方案進行偵錯時，偵錯工具將於何處尋找原始程式檔。

 若要存取 [偵錯來源檔案] 屬性頁，請以滑鼠右鍵按一下您在 [方案總管] 中的方案，然後從捷徑功能表選取 [屬性]。 展開 [通用屬性] 資料夾，然後按一下 [偵錯來源檔案] 頁面。

 **包含原始程式碼的目錄**包含目錄清單，其中偵錯工具會在偵測方案時搜尋來源檔案。 另外也會搜尋所指定目錄的子目錄。

 **不要尋找這些原始程式**檔輸入您不想讓偵錯工具讀取的任何檔案名。 如果偵錯工具在上面其中一個指定的目錄中找到這些檔案中的某一個，就會忽略該檔案。 如果在進行偵錯時出現 [尋找原始碼] 對話方塊，而您按一下 [取消]，您之前搜尋的檔案就會新增至這個清單，如此偵錯工具就不會繼續搜尋該檔案。

## <a name="see-also"></a>請參閱

- [偵錯工具安全性](../debugger/debugger-security.md)
- [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)