---
title: 錯誤： 在 Web 伺服器找不到要求的資源 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 1e6fec89a151525a84349b7019c7569eb752172e
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454312"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>錯誤：Web 伺服器找不到要求的資源
基於安全性考量，IIS 已傳回泛型錯誤。  
  
 原因可能是伺服器的安全性組態。 IIS 6.0 (含) 以前版本中使用了一個稱為 URLScan 的附加元件程式，用於篩選出可疑和格式錯誤的要求。 IIS 7.0 內建了要求篩選功能，可達到相同的目的。 在這兩種情況下，太過嚴格的要求篩選可能會阻止 Visual Studio 對伺服器進行偵錯。  
  
 造成這個錯誤的原因可能有很多種。 其中幾個最常見的原因包括 IIS 的安裝或組態、網站組態或檔案系統的權限發生問題。 您可以嘗試使用瀏覽器存取資源。 根據 IIS 的設定方式，您可能需要在伺服器上使用本機瀏覽器或檢查 IIS 錯誤記錄檔，以取得詳細的錯誤訊息。  
  
 如需有關對 IIS 進行疑難排解的詳細資訊，請參閱[IIS 管理](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration)。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤：Web 伺服器已經鎖定，並會封鎖 DEBUG 動詞命令](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)