---
title: SQL 可以 &apos; 找不到 ssdebugps.dll |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 67d7602357a39cbdce0c96b494f4c02758533e73
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871386"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>錯誤： SQL 可以&#39;t Find SSDEBUGPS.DLL

SSDEBUGPS.dll 是 SQL Server 偵錯主機元件。

當您嘗試啟動偵錯時會發生這個錯誤，並表示指定的檔案不在 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 電腦上。 可能的原因是從未執行遠端偵錯 (Remote Debugging) 安裝程式，或者已刪除這個檔案。

有兩個方法可以解決這個錯誤：一是重新執行遠端偵錯安裝程式，二是將該檔案複製到 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 電腦。

若要重新執行遠端偵錯程式設定，請遵循 [遠端偵錯](../debugger/remote-debugging.md)程式的指示。

如果找得到 ssdebugps.dll 的複本，就可以將該複本複製到 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 電腦。 如果有這個檔案，會在 \Program Files\ Common Files\Microsoft Shared\SQL Debugging 目錄中。 您可能會在另一部 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 電腦或安裝了 Visual Studio 2005 的電腦上找到它。

將 SSDEBUGPS.dll 複製到 SQL Server 2005 電腦：

1. 將該檔案複製到 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 電腦上具有相同名稱和路徑的目錄。

2. 開啟 [命令提示字元] 並執行下列命令，即可登錄該檔案：

    ```cmd
    regsvr32 ssdebugps.dll
    ```
