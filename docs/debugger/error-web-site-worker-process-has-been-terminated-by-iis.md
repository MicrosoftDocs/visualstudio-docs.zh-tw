---
title: 錯誤：網站背景工作處理序已被 IIS 終止 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.web_server_process_terminated
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
ms.openlocfilehash: 2d89eabec0c199b1b8df7eeb78d0e629d4a70b2e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072652"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>錯誤：網站背景工作處理序已被 IIS 終止
偵錯工具停止執行網站上的程式碼。 如此一來，可能會使網際網路資訊服務 (IIS) 認為背景工作處理序已停止回應。 因此，IIS 會結束背景工作處理序。

 若要繼續偵錯，您必須設定 IIS 以允許背景工作處理序繼續進行。 這個錯誤訊息不會出現在 IIS 7 (含) 以前版本中。

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>若要設定 IIS 7 允許背景工作處理序繼續進行

1. 開啟 [系統管理工具] 視窗。

   1. 按一下 [開始]，然後選擇 [控制台]。

   2. 在 [控制台] 中依需要選擇 [切換到傳統檢視]，然後按兩下 [系統管理工具]。

2. 在 [系統管理工具] 視窗中，按兩下 [Internet Information Services (IIS) 管理員]。

    [IIS 管理員] 隨即開啟。

3. 在 [連線] 窗格中，展開 [\<電腦名稱>] 節點 (如有需要)。

4. 按一下 [\<電腦名稱>] 節點下的 [應用程式集區]。

5. 在 [應用程式集區] 清單內，以滑鼠右鍵按一下應用程式執行位置所在的集區名稱，然後按一下 [進階設定]。

6. 在 [進階設定] 對話方塊中，找出 [處理模型] 區段，並執行下列其中一個動作：

   - 將 [已啟用 Ping] 設定為 [False]。

   - 將 [Ping 回應時間上限] 設定為大於 90 秒的值。

     將 [已啟用 Ping] 設定為 [False]，可使 IIS 停止檢查背景工作處理序是否仍在執行，並使背景工作處理序保持為執行狀態，直到停止已偵錯的處理序為止。 將 [Ping 回應時間上限] 設定為大數值，可讓 IIS 繼續監視背景工作處理序。

7. 按一下 [確定]，關閉 [進階設定] 對話方塊。

8. 關閉 [IIS 管理員] 和 [系統管理工具] 視窗。

## <a name="see-also"></a>另請參閱
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)