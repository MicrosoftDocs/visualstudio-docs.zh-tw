---
title: 使用者入門 （偵錯介面存取 SDK） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0c3c6df3fc92370d939771a7e94334db7f2cfc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-debug-interface-access-sdk"></a>使用者入門 (偵錯介面存取 SDK)
偵錯介面存取 (DIA) SDK 會提供您與指示文件說明如何使用 DIA API 的範例。 使用介面和方法在 DIA SDK 來開發自訂應用程式開啟的.pdb 和.dbg 檔案，搜尋其內容中的符號、 值、 屬性、 位址和其他偵錯資訊。 此 SDK 也提供 c + + 應用程式中找到的符號相關聯的屬性參考資料表。  
  
 為了有效運用 DIA SDK，您應該要熟悉下列程式碼：  
  
-   C + + 程式設計語言  
  
-   COM 程式設計  
  
-   編譯範例的 visual Studio 整合式的開發環境 (IDE)  
  
 DIA SDK 通常會隨 Visual Studio 和其預設位置是*[磁碟機]*\Program Files\Microsoft Visual Studio 9.0\DIA SDK。 安裝的一部分，msdia90.dll，會實作 DIA SDK，會自動註冊，所有您要使用它做為包含`dia2.h`在您的程式和連結`diaguids.lib`。  
  
 標頭： include\dia2.h  
  
 程式庫： lib\diaguids.lib  
  
 DLL: bin\msdia80.dll  
  
 IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>本節內容  
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 檢閱 dia 時發生的基本架構  
  
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 提供逐步指示如何使用 DIA API 來查詢.pdb 檔案。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)