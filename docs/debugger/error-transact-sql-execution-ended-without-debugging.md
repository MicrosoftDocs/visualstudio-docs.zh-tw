---
title: 錯誤：TRANSACT-SQL 執行未經偵錯即結束 |Microsoft Docs
ms.date: 11/08/2018
ms.topic: troubleshooting
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
ms.openlocfilehash: 17c1854826de2314dfe8124d99f6ec6c8899ee70
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011217"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>錯誤：Transact-SQL 執行未經偵錯即結束

當您嘗試偵錯 TRANSACT-SQL 或 SQLCLR 程序，且偵錯工具不會接收 SQL Server 偵錯的訊息時，就會發生此錯誤。  
  
此問題可能是由於網路問題或 SQL Server 上的問題，但最可能的原因是權限問題。  
  
有兩個相關的帳戶：  
  
- 應用程式帳戶是正在執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的使用者帳戶。  
  
- 連接帳戶是用來建立 SQL Server 連接的識別。 此帳戶不一定是與 Visual Studio 正在執行，如同的連線使用 SQL 驗證的身分識別相同。  
  
  SQL 偵錯需要應用程式帳戶必須符合連接帳戶，或者是 sysadmin。  
  
  如果您使用的 SQL 帳戶名稱，例如 sa，應用程式帳戶必須設定 SQL Server 上為系統管理員。 根據預設，SQL server 執行的電腦上的系統管理員會是 SQL Server sysadmin。  
  
  若要更正這個錯誤，您可能需要：  
  
  - 驗證使用權限設定。 如需詳細資訊，請參閱[＜How to：設定 SQL Server 權限偵錯](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)。  
  
  - 如果設定正確，請確定 SQL 偵錯作業。  
  
  - 請連絡網路或資料庫管理員。  
  
## <a name="see-also"></a>請參閱

- [設定 SQL 偵錯](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [如何：設定 SQL Server 權限偵錯](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)