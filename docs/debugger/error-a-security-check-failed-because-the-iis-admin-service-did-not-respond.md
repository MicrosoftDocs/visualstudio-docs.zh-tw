---
title: 安全性檢查失敗，因為 IIS 管理服務沒有回應 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e64947beb30b5abc4649fc65d8d566a7dedb55a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871828"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>錯誤：安全性檢查失敗，因為 IIS 管理服務沒有回應
當 IIS 管理服務沒有回應時，就會發生這個錯誤。 這通常表示 IIS 安裝有問題。 首先，確認使用 [系統管理工具] 的 [服務] 工具驗證服務是否在執行。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 使用 [新增或移除程式] 控制台來重新安裝 IIS。

- -或-

- 使用新增或移除程式控制台來移除電腦中的 IIS。 如果移除 IIS 後仍有問題，請檢查登錄，確定這個機碼已不存在：

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     -或-

- 使用系統管理工具控制台以停用 IIS 管理服務。 這個動作將停用電腦中的 IIS。

     在執行其中任何三個步驟後，請重新啟動電腦。

     如需其他資訊，請參閱 IIS 文件。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)