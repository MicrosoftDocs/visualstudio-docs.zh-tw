---
title: 錯誤：TRANSACT-SQL 執行未經偵錯即結束 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 910b84e7a024547208ea2e7ae1d6a6897cf60893
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58946074"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>錯誤：Transact-SQL 執行未經偵錯即結束
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您嘗試偵錯 Transact-SQL 或 SQLCLR 程序，而且偵錯工作沒有從 SQL Server 接收偵錯訊息時，便會發生這個錯誤。  
  
 這可能是因為網路問題或 SQL Server 上的問題，不過最有可能是使用權限的問題。  
  
 有兩個相關的帳戶：  
  
- 應用程式帳戶是正在執行 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的使用者帳戶。  
  
- 連接帳戶是用來建立 SQL Server 連接的識別。 如果連接使用 SQL 驗證 (Authentication)，則不需要與正在執行 Visual Studio 的識別一樣。  
  
  SQL 偵錯需要應用程式帳戶符合連接帳戶或者是 sysadmin。  
  
  如果您正在使用 SQL 登入 (例如 sa)，必須在 SQL Server 上將應用程式帳戶設定為 sysadmin。 根據預設，SQL Server sysadmin 是執行 SQL Server 之電腦上的系統管理員。  
  
  若要更正這個錯誤，您可能需要：  
  
- 驗證使用權限設定。 如需詳細資訊，請參閱[如何：設定 SQL Server 權限偵錯](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)。  
  
- 如果設定正確，請確定 SQL 偵錯作業。  
  
- 請連絡網路或資料庫管理員。  
  
## <a name="see-also"></a>另請參閱  
 [設定 SQL 偵錯](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [如何：設定 SQL Server 權限偵錯](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
