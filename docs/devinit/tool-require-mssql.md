---
title: require-mssql
description: devinit 工具需要-mssql。
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: f24ccfbe66075cdb5b9f0fb257e401b611862044
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842663"
---
# <a name="require-mssql"></a>require-mssql

此 `require-mssql` 工具是用來透過 MS SQL SERVER ISO 安裝 [Microsoft SQL Server 2019 Developer Edition](https://www.microsoft.com/sql-server/application-development) 。 SQL server 將 `localhost` 使用整合式 Windows 驗證來提供，sql server 將可透過連接字串存取 `"Server=localhost;Integrated Security=true;"` 。

## <a name="usage"></a>使用方式

如果 `input` 和 `additionalOptions` 屬性都省略或空白，則工具將會遵循以下詳述的 [預設](#default-behavior) 行為。

| 名稱                                             | 類型   | 必要 | 值                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **評論**                                     | 字串 | No       | 選擇性批註屬性。 未使用。                                                   |
| [**輸入**](#input)                              | 字串 | No       | 如需詳細資料，請參閱下列 [輸入](#input) 。                                                  |
| [**additionalOptions**](#additional-options)     | 字串 | No       | 未使用。 請參閱下方的 [其他選項](#additional-options) 以取得詳細資料。              |

### <a name="input"></a>輸入

`input`屬性可以是具有下列兩個值之一的字串：

| 值     | 描述                              |
|-----------|------------------------------------------|
| 安裝   | 安裝 SQL server。                     |
| uninstall | 卸載所有的 SQL server 安裝。 |

### <a name="additional-options"></a>其他選項

未使用。

### <a name="default-behavior"></a>預設行為

工具的預設行為 `require-mssql` 是安裝 SQL server。

### <a name="built-in-options"></a>內建選項

此 `require-mssql` 工具會設定一些安裝程式命令列引數，以確保安裝程式可以執行無周邊。 以下列出這些引數，您可以在 [SQL 安裝檔](/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15&preserve-view=true)中找到這些引數的相關檔。

| 名稱                                                               | 描述 |
|--------------------------------------------------------------------|-------------|
| /q                                                                 |             |
| /ACTION = 安裝                                                    |             |
| /FEATURES = SQLEngine、LocalDB                                       |             |
| /UpdateEnabled                                                     |             |
| /UpdateSource = MU                                                   |             |
| /X86 = false                                                         |             |
| /INSTANCENAME = MSSQLSERVER                                          |             |
| /INSTALLSHAREDDIR = "C:\Program Files\Microsoft SQL Server"          |             |
| /INSTALLSHAREDWOWDIR = "C:\Program Files (x86) \Microsoft SQL Server" |             |
| /SQLSVCINSTANTFILEINIT = True                                        |             |
| 支援/INSTANCEDIR = "C:\Program Files\Microsoft SQL Server"               |             |
| /AGTSVCACCOUNT = "NT Service\SQLSERVERAGENT"                         |             |
| /AGTSVCSTARTUPTYPE = 手動                                          |             |
| /SQLSVCSTARTUPTYPE = 自動                                       |             |
| /SQLCOLLATION = "SQL_Latin1_General_CP1_CI_AS"                       |             |
| /SQLSVCACCOUNT = "NT Service\MSSQLSERVER"                            |             |
| 使用/SQLSYSADMINACCOUNTS = 系統管理員                                |             |
| /IACCEPTSQLSERVERLICENSETERMS                                      |             |

## <a name="example-usage"></a>使用方式範例
以下是如何使用執行的範例 `require-msssql` `.devinit.json` 。

#### <a name="devinitjson-that-will-install-mssql"></a>.devinit.js將會安裝 MSSQL：
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-mssql",
            "input": "install",
        }
    ]
}
```