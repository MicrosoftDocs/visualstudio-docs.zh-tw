---
title: 錯誤-Transact-sql 執行已結束，但未進行調試 |Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e141fac7fba1939811c722d8e08f49531111ff7e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460243"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>錯誤：Transact-SQL 執行未經偵錯即結束

當您嘗試調試 Transact-sql 或 SQLCLR 程式，而偵錯工具未收到來自 SQL Server 的偵錯工具訊息時，就會發生此錯誤。

此問題可能是因為網路問題或 SQL Server 的問題，但最有可能的原因是許可權問題。

有兩個相關的帳戶：

- 應用程式帳戶是正在執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的使用者帳戶。

- 連接帳戶是用來建立 SQL Server 連接的識別。 此帳戶不一定要與 Visual Studio 執行的身分識別相同，如同連接使用 SQL 驗證一樣。

  SQL 偵錯工具要求應用程式帳戶必須符合連接帳戶，或必須是系統管理員（sysadmin）。

  如果您使用類似 sa 的 SQL 帳戶名稱，則必須在 SQL Server 上將應用程式帳戶設定為系統管理員（sysadmin）。 根據預設，執行 SQL server 之電腦上的系統管理員是 SQL Server sysadmin。

  若要更正這個錯誤，您可能需要：

  - 驗證使用權限設定。 如需詳細資訊，請參閱[如何：設定偵錯工具的 SQL Server 許可權](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)。

  - 如果設定正確，請確定 SQL 偵錯作業。

  - 請連絡網路或資料庫管理員。

## <a name="see-also"></a>另請參閱

- [設定 SQL 調試](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [如何：設定偵錯的 SQL Server 權限](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [偵錯設定及準備](../debugger/debugger-settings-and-preparation.md)
- [遠端偵錯](../debugger/remote-debugging.md)