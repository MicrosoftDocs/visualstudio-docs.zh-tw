---
title: 錯誤： 安全性檢查失敗，因為 IIS Admin Service 未回應 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6215648cba97e17ab143538afb4936a480adae4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769026"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>錯誤：安全性檢查失敗，因為 IIS 管理服務沒有回應
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當 IIS 管理服務沒有回應時，就會發生這個錯誤。 這通常表示 IIS 安裝有問題。 首先，請確認服務正在執行使用**Services**工具**系統管理工具**。  
  
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



