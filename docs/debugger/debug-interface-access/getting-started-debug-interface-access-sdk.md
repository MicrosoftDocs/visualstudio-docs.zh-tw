---
title: 消費者入門（Debug Interface Access SDK） |Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dd6a98f377ba295d6a866c9db95671de4ff16ea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745110"
---
# <a name="getting-started-debug-interface-access-sdk"></a>使用者入門 (偵錯介面存取 SDK)
Debug Interface Access （DIA） SDK 為您提供教學檔，以及說明如何使用 DIA API 的範例。 使用 DIA SDK 中的介面和方法來開發自訂應用程式，以開啟 .pdb 和 dbg 檔案，並搜尋其內容中的符號、值、屬性、位址和其他的偵錯工具資訊。 此 SDK 也會提供與在應用程式中C++找到之符號相關聯之屬性的參考資料表。

 若要充分運用 DIA SDK，您應該熟悉下列各項：

- C++程式設計語言

- COM 程式設計

- 用於編譯範例的 Visual Studio 整合式開發環境（IDE）

  DIA SDK 通常會與 Visual Studio 一起安裝，且其預設位置為 *[drive]* \Program Files\Microsoft Visual Studio 9.0 \ DIA SDK。 在安裝過程中，會自動註冊 DIA SDK msdia90 來執行程式設計，因此您必須使用它來將 `dia2.h` 包含在程式中，並連結至 `diaguids.lib`。

  標頭： include\dia2。h

  程式庫： lib\diaguids.lib

  DLL：bin\msdia80.dll

  IDL：idl\dia2.idl

## <a name="in-this-section"></a>本章節內容

[概觀](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

回顧 DIA 的基本架構。

[查詢 .Pdb 檔案](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

提供逐步指示，說明如何使用 DIA API 來查詢 .pdb 檔案。

## <a name="see-also"></a>請參閱

- [偵錯介面存取 SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)