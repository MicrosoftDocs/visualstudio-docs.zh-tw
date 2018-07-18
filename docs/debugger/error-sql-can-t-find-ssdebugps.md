---
title: 錯誤： SQL 可以&#39;t 找不到 SSDEBUGPS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1498a287bdb474751dfaa5b4b23c30bc302544e7
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058252"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>錯誤： SQL 可以&#39;t 找不到 SSDEBUGPS

SSDEBUGPS.dll 是 SQL Server 偵錯主機元件。

當您嘗試啟動偵錯時會發生這個錯誤，並表示指定的檔案不在 [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] 電腦上。 可能的原因是從未執行遠端偵錯 (Remote Debugging) 安裝程式，或者已刪除這個檔案。

若要解決此錯誤的兩種方式： 藉由重新執行遠端偵錯安裝程式，並複製檔案拖曳至[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]機器。

若要重新執行遠端偵錯安裝程式，請遵循指示[遠端偵錯](../debugger/remote-debugging.md)。

如果找得到 ssdebugps.dll 的複本，您可以將它拖曳至複製[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]機器。 如果有這個檔案，會在 \Program Files\ Common Files\Microsoft Shared\SQL Debugging 目錄中。 您可能會發現它在另一個[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]機器，或已安裝 Visual Studio 2005 的電腦上。

若要將 SSDEBUGPS.dll 複製至 SQL Server 2005 電腦中：

1. 將檔案複製到具有相同的名稱和路徑的目錄中上,[!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]機器。

2. 註冊 %installationdirectory**命令提示字元**，並執行下列命令：

    ```cmd
    regsrv32 ssdebugps.dll
    ```
