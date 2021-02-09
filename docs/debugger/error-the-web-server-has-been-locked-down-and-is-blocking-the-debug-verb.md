---
title: Web 服務器已經鎖定，且正在封鎖 DEBUG 動詞命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
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
ms.openlocfilehash: e68ab09d7fc398d45a8942c3df4ca0dee5754d2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871205"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>錯誤：Web 伺服器已經鎖定，並會封鎖 DEBUG 動詞命令
逐步執行 Web 應用程式或 XML Web Service 失敗，因為已執行 IIS 鎖定工具，並已安裝啟動 URLScan。 這種情況會鎖定 IIS 而無法接收 DEBUG 動詞命令。

 URLScan 是與 IIS 鎖定工具搭配運作的安全工具，提供 IIS 網站管理員關閉非必要功能，並限制伺服器將處理 HTTP 要求類型的能力。 URLScan 安全工具藉鎖定特定的 HTTP 要求，防止可能具有危害性的要求到達伺服器，導致損壞。

 如果應用程式是在 Windows Server 2003 的 IIS 6.0 上執行，則不需要再執行 IIS Lockdown 工具，因為 IIS 6.0 有提供相同的功能。

### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>若要在已安裝 URLScan 的 Web 伺服器上啟用偵錯

1. 找出 Urlscan.ini 檔。 通常您會在類似如下的目錄中找到它：

     C:\WINNT\System32\Inetsrv\urlscan

2. 建立該檔案的複本，並命名為 **Urlscan.old**。

3. 使用 [記事本] 或您選擇的文字編輯器開啟 Urlscan.ini 檔的原始複本。

4. 在 Urlscan.ini 中，找出 [AllowVerbs] 區段。 將 DEBUG 加入至 [AllowVerbs] 區段。 如果您在 [AllowVerbs] 區段中看到 ;DEBUG，請移除分號以取消動詞命令的註解。

5. 找出 [DenyVerbs] 區段。 如果 DEBUG 出現在 [DenyVerbs] 區段中，請移除它。

6. 儲存檔案。

7. 重新啟動伺服器或重新啟動 IIS。

## <a name="see-also"></a>另請參閱
- [偵錯 Web 應用程式：錯誤和疑難排解](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [錯誤： Web 服務器找不到要求的資源](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)