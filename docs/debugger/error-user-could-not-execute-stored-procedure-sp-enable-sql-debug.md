---
title: 錯誤： 使用者無法執行預存程序 sp_enable_sql_debug |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f13eb0b7deb9295ac20e04f4ba1111e128efa0c0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903981"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>錯誤：使用者無法執行預存程序 sp_enable_sql_debug
預存程序 sp_enable_sql_debug 無法在伺服器上執行。 可能的原因如下：  
  
- 連接問題。 您需要穩定的連接到伺服器。  
  
- 沒有必要的伺服器使用權限。 若要在 SQL Server 2005 上進行偵錯，執行 Visual Studio 的帳戶和用來連接至 SQL Server 的帳戶都必須是系統管理員角色的成員。 用來連接至 SQL Server 的帳戶就是您的 Windows 使用者帳戶 (如果您使用 Windows 驗證)，或具有使用者 ID 和密碼的帳戶 (如果您使用 SQL 驗證)。  
  
  如需詳細資訊，請參閱 <<c0> [ 如何： 設定 SQL Server 權限進行偵錯](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 設定 SQL Server 權限偵錯](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [設定 SQL 偵錯](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)