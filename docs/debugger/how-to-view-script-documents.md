---
title: 如何：查看指令檔 |Microsoft Docs
ms.date: 11/05/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e362e0504c4ed2584bbbbea687fe3c58fc79edb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714435"
---
# <a name="how-to-view-script-documents-javascript"></a>如何：查看指令檔（JavaScript）

伺服器端腳本檔會顯示在方案總管中。 只有在您處於偵錯模式或中斷模式時，才會看得見用戶端指令碼檔。 用戶端腳本檔案會出現在 [**腳本**檔] 節點中。

針對動態產生頁面的某些應用程式類型，當您從瀏覽器中載入的指令檔設定中斷點時，進入中斷模式和 debug 會比較容易。 同樣地，您可以從載入的指令檔加入 `debugger` 語句，進入中斷模式。 本文說明如何查看這些檔。

> [!NOTE]
> 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]之前，從伺服器端腳本產生的用戶端腳本檔案會出現在 [腳本瀏覽器] 視窗中。

### <a name="to-view-a-server-side-script-document"></a>若要檢視伺服器端指令碼文件

1. 在 [方案總管] 中，開啟 [\<網站路徑名稱>] 節點。

2. 按兩下您想要檢視的指令碼檔。

     伺服器端指令碼檔會在來源視窗中開啟。

### <a name="to-view-a-client-side-script-document"></a>若要檢視用戶端指令碼文件

1. 在 [方案總管] 中，開啟 [指令碼文件] 節點。

2. 按兩下您想要檢視的指令碼檔。

     用戶端指令碼檔會在來源視窗中開啟。

## <a name="see-also"></a>請參閱
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)