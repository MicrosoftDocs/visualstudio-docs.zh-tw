---
title: 使用者入門 （偵錯介面存取 SDK） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 089d824a6f693d7a0661b2e099ded82e0b02f403
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554403"
---
# <a name="getting-started-debug-interface-access-sdk"></a>使用者入門 (偵錯介面存取 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

偵錯介面存取 (DIA) SDK 會提供您指示文件與說明如何使用 DIA API 的範例。 使用介面和方法在 DIA SDK 開發自訂的應用程式所開啟的.pdb 和.dbg 檔案，並搜尋其內容的符號、 值、 屬性、 位址和其他偵錯資訊。 此 SDK 也提供參考資料表中找到與符號相關聯的屬性C++應用程式。  
  
 若要最佳方式使用 DIA SDK，您應該先熟悉下列項目：  
  
- C++程式設計語言  
  
- COM 程式設計  
  
- 編譯範例的 visual Studio 整合式的開發環境 (IDE)  
  
  DIA SDK 通常會隨 Visual Studio 和其預設位置是 *[磁碟機]* \Program Files\Microsoft Visual Studio 9.0\DIA SDK。 安裝的一部分，msdia90.dll，會實作 DIA SDK，會自動註冊，您需要如何使用它只包含`dia2.h`在您的程式和連結`diaguids.lib`。  
  
  標頭： include\dia2.h  
  
  程式庫： lib\diaguids.lib  
  
  DLL：bin\msdia80.dll  
  
  IDL：idl\dia2.idl  
  
## <a name="in-this-section"></a>本節內容  
 [概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 檢閱 dia 時發生的基本架構  
  
 [查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 提供有關如何使用 DIA API 來查詢.pdb 檔案的逐步指示。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
