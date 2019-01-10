---
title: 使用者入門 （偵錯介面存取 SDK） |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: ee77d4b7f8f1073ce638c8933f468b369d772a71
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961721"
---
# <a name="getting-started-debug-interface-access-sdk"></a>使用者入門 (偵錯介面存取 SDK)
偵錯介面存取 (DIA) SDK 會提供您指示文件與說明如何使用 DIA API 的範例。 使用介面和方法在 DIA SDK 開發自訂的應用程式所開啟的.pdb 和.dbg 檔案，並搜尋其內容的符號、 值、 屬性、 位址和其他偵錯資訊。 此 SDK 也提供適用於 c + + 應用程式中找到的符號相關聯的屬性參考表格。  
  
 若要最佳方式使用 DIA SDK，您應該先熟悉下列項目：  
  
- C + + 程式設計語言  
  
- COM 程式設計  
  
- 編譯範例的 visual Studio 整合式的開發環境 (IDE)  
  
  DIA SDK 通常會隨 Visual Studio 和其預設位置是 *[磁碟機]* \Program Files\Microsoft Visual Studio 9.0\DIA SDK。 安裝的一部分，msdia90.dll，會實作 DIA SDK，會自動註冊，您需要如何使用它只包含`dia2.h`在您的程式和連結`diaguids.lib`。  
  
  標頭： include\dia2.h  
  
  程式庫： lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>本節內容  
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 檢閱 dia 時發生的基本架構  
  
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 提供有關如何使用 DIA API 來查詢.pdb 檔案的逐步指示。  
  
## <a name="see-also"></a>請參閱  
 [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)