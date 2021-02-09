---
title: 開始使用 (Debug 介面存取 SDK) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6a60e7b685fe277cfe44e5dd3ab1c4825dba67af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865311"
---
# <a name="getting-started-debug-interface-access-sdk"></a>使用者入門 (偵錯介面存取 SDK)
 (DIA) SDK 的 Debug 介面存取會提供您教學檔，以及說明如何使用 DIA API 的範例。 使用 DIA SDK 中的介面和方法來開發自訂應用程式，以開啟 .pdb 和 dbg 檔案，並搜尋其內容中的符號、值、屬性、位址和其他偵錯工具資訊。 此 SDK 也提供與 c + + 應用程式中的符號相關聯之屬性的參考資料表。

 若要充分利用 DIA SDK，您應該熟悉下列各項：

- C + + 程式設計語言

- COM 程式設計

- Visual Studio 整合式開發環境 (IDE) 編譯範例

  DIA SDK 通常會隨著 Visual Studio 安裝，且其預設位置為 *[磁片磁碟機]* \Program Files\Microsoft Visual Studio 9.0 \ DIA SDK。 在安裝過程中，會自動註冊執行 DIA SDK 的 msdia90.dll，所以您只需要在程式中加入，就可以將 `dia2.h` 連結到 `diaguids.lib` 。

  標頭： include\dia2。h

  程式庫： lib\diaguids.lib

  DLL：bin\msdia80.dll

  IDL：idl\dia2.idl

## <a name="in-this-section"></a>本節內容

[概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

審核 DIA 的基本架構。

[查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

提供逐步指示，說明如何使用 DIA API 來查詢 .pdb 檔。

## <a name="see-also"></a>另請參閱

- [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)