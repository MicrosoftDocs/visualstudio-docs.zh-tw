---
description: 當您嘗試對 Transact-sql 或 SQLCLR 程式進行偵錯工具，而偵錯工具未收到來自 SQL Server 的偵錯工具時，就會發生這個錯誤。
title: Transact-sql 執行已結束，但未進行調試 |Microsoft 檔
ms.date: 11/08/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
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
ms.openlocfilehash: 40b0b89474b24e53c69df14894e50ee502c6eb9b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146492"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>錯誤：Transact-SQL 執行未經偵錯即結束

當您嘗試對 Transact-sql 或 SQLCLR 程式進行偵錯工具，而偵錯工具未收到來自 SQL Server 的偵錯工具時，就會發生這個錯誤。

發生此問題的原因可能是網路問題或 SQL Server 上的問題，但是最可能的原因是許可權問題。

有兩個相關的帳戶：

- 應用程式帳戶是正在執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的使用者帳戶。

- 連接帳戶是用來建立 SQL Server 連接的識別。 此帳戶不一定會與 Visual Studio 執行的身分識別相同，如同連接使用 SQL 驗證一樣。

  SQL 偵錯工具要求應用程式帳戶必須符合線上帳戶或系統管理員（sysadmin）。

  如果您使用的是 SQL 帳戶名稱（例如 sa），則必須在 SQL Server 上將應用程式帳戶設定為系統管理員（sysadmin）。 依預設，執行 SQL server 的電腦上的系統管理員為 SQL Server sysadmin。

  若要更正這個錯誤，您可能需要：

  - 驗證使用權限設定。 如需詳細資訊，請參閱 [如何：設定 SQL Server 的偵錯工具許可權](/previous-versions/w1bhybwz(v=vs.100))。

  - 如果設定正確，請確定 SQL 偵錯作業。

  - 請連絡網路或資料庫管理員。

## <a name="see-also"></a>另請參閱

- [設定 SQL 調試](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [如何：設定偵錯的 SQL Server 權限](/previous-versions/w1bhybwz(v=vs.100))
- [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)
- [遠端偵錯](../debugger/remote-debugging.md)
