---
title: 查看指令檔 |Microsoft Docs
description: 瞭解如何使用方案總管在 Visual Studio 中查看 JavaScript 伺服器端指令檔。
ms.custom: SEO-VS-2020
ms.date: 11/05/2019
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfaa4e2558d8d1f102b0e442e9c509313f860e4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853094"
---
# <a name="how-to-view-script-documents-javascript"></a>如何： (JavaScript 查看指令檔) 

伺服器端腳本檔會在方案總管中顯示。 只有在您處於偵錯模式或中斷模式時，才會看得見用戶端指令碼檔。 用戶端腳本檔案會出現在 [ **腳本** 檔] 節點中。

針對動態產生頁面的部分應用程式類型，當您從瀏覽器中載入的指令檔設定中斷點時，可以更輕鬆地進入中斷模式和偵錯工具。 同樣地，您可以 `debugger` 從載入的指令檔中加入語句，以進入中斷模式。 本文說明如何查看這些檔。

> [!NOTE]
> 在中 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ，從伺服器端腳本產生的用戶端腳本檔會出現在 [腳本瀏覽器] 視窗中。

### <a name="to-view-a-server-side-script-document"></a>若要檢視伺服器端指令碼文件

1. 在 **方案總管** 中，開啟 **\<Website Pathname>** 節點。

2. 按兩下您想要檢視的指令碼檔。

     伺服器端指令碼檔會在來源視窗中開啟。

### <a name="to-view-a-client-side-script-document"></a>若要檢視用戶端指令碼文件

1. 在 [方案總管] 中，開啟 [指令碼文件] 節點。

2. 按兩下您想要檢視的指令碼檔。

     用戶端指令碼檔會在來源視窗中開啟。

## <a name="see-also"></a>另請參閱
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)