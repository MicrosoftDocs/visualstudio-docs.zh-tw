---
title: 您沒有檢查進程身分識別的許可權 &apos; |Microsoft Docs
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
ms.openlocfilehash: 6903cba8d048d5ed2969d5aa7436fc6eca17561e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870803"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>錯誤：您沒有許可權可檢查進程&#39;s 的身分識別
您沒有檢查此處理序識別的權限。 這很可能是因為系統組態所造成。

 偵錯工具無法檢查處理序識別，而這是進行偵錯的必要資訊。 最可能的原因是已停用終端機服務 (Terminal Service)。 預設狀況下會啟用終端機服務。 請依照下列步驟重新啟用終端機服務。

### <a name="to-enable-terminal-services"></a>啟用終端機服務

1. 按一下 [開始]，然後選擇 [控制台]。

2. 在 [控制台] 中依需求選擇 [切換到傳統檢視]，然後按兩下 [系統管理工具]。

3. 在 [系統管理工具] 視窗中，按兩下 [電腦管理]。

4. 在 [電腦管理] 視窗中，展開 [服務及應用程式] 節點。

5. 在 [服務及應用程式] 下，按一下 [服務]。

     服務清單隨即出現在右窗格中。

6. 在 [服務] 清單中，以滑鼠右鍵按一下 [終端機服務]，然後選擇 [屬性]。

7. 在 [**終端機服務屬性**] 視窗中，移至 [一般] 索引標籤，並將 **啟動類型** 設定為 **[** **手動**]

8. 按一下 [確定]  。

9. 重新啟動電腦。

     這個程序不會自動啟用遠端桌面。 如果要啟用電腦上的遠端桌面，請再執行下列程序。

### <a name="to-enable-remote-desktop"></a>啟用遠端桌面

1. 按一下 [開始]，然後以滑鼠右鍵按一下 [我的電腦]。

2. 選擇 [內容]。

     [系統屬性] 視窗隨即顯示。

3. 按一下 [遠端] 。

4. 在 [遠端桌面] 下，選取 [允許使用者遠端連線到這部電腦]。

5. 按一下 [確定]  。

## <a name="see-also"></a>另請參閱
- [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)