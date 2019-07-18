---
title: 錯誤：使用者無法執行預存程序 sp_enable_sql_debug |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e051cd594ee26a57fdbb7dcdc5bdad81f06cf771
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850087"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>錯誤：使用者無法執行預存程序 sp_enable_sql_debug

預存程序 sp_enable_sql_debug 無法在伺服器上執行。 可能的原因如下：

- 連接問題。 您需要穩定的連接到伺服器。

- 沒有必要的伺服器使用權限。 若要在 SQL Server 2005 上進行偵錯，執行 Visual Studio 的帳戶和用來連接至 SQL Server 的帳戶都必須是系統管理員角色的成員。 用來連接至 SQL Server 的帳戶就是您的 Windows 使用者帳戶 (如果您使用 Windows 驗證)，或具有使用者 ID 和密碼的帳戶 (如果您使用 SQL 驗證)。

如需詳細資訊，請參閱[如何：設定 SQL Server 權限偵錯](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)。

## <a name="see-also"></a>另請參閱

- [如何：設定 SQL Server 權限偵錯](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [設定 SQL 偵錯](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))