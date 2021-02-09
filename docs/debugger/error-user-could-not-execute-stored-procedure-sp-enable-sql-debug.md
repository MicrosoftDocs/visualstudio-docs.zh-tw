---
title: 使用者無法執行預存程式 sp_enable_sql_debug |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 41576d83ecff9f501b56ecc3fef3878f7c8a00b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870905"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>錯誤：使用者無法執行預存程序 sp_enable_sql_debug

預存程序 sp_enable_sql_debug 無法在伺服器上執行。 可能的原因如下：

- 連接問題。 您需要穩定的連接到伺服器。

- 沒有必要的伺服器使用權限。 若要在 SQL Server 2005 上進行偵錯，執行 Visual Studio 的帳戶和用來連接至 SQL Server 的帳戶都必須是系統管理員角色的成員。 用來連接至 SQL Server 的帳戶就是您的 Windows 使用者帳戶 (如果您使用 Windows 驗證)，或具有使用者 ID 和密碼的帳戶 (如果您使用 SQL 驗證)。

如需詳細資訊，請參閱 [如何：設定偵錯工具的 SQL Server 許可權](/previous-versions/w1bhybwz(v=vs.100))。

## <a name="see-also"></a>另請參閱

- [如何：設定偵錯的 SQL Server 權限](/previous-versions/w1bhybwz(v=vs.100))
- [設定 SQL 調試](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))