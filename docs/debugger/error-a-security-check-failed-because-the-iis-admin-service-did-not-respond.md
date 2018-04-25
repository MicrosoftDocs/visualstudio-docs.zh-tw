---
title: 錯誤： 安全性檢查失敗，因為 IIS Admin Service 未回應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3b0b3412c450976cb15211813de32ab6e78eaa9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>錯誤：安全性檢查失敗，因為 IIS 管理服務沒有回應
當 IIS 管理服務沒有回應時，就會發生這個錯誤。 這通常表示 IIS 安裝有問題。 首先，請確認服務正在執行使用**服務**工具**系統管理工具**。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   重新安裝 IIS，使用**新增或移除程式**控制台。  
  
-   -或-  
  
-   使用新增或移除程式控制台來移除電腦中的 IIS。 如果移除 IIS 後仍有問題，請檢查登錄，確定這個機碼已不存在：  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     -或-  
  
-   使用系統管理工具控制台以停用 IIS 管理服務。 這個動作將停用電腦中的 IIS。  
  
     在執行其中任何三個步驟後，請重新啟動電腦。  
  
     如需其他資訊，請參閱 IIS 文件。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)