---
title: 偵錯工具安全性 |Microsoft Docs
description: 瞭解偵錯工具所造成的安全性風險，以及偵錯工具和所要進行的機器的風險。 遵循建議以將風險降至最低。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d204f99dd955609dcc082d5d9bd607cfad75bb1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873047"
---
# <a name="debugger-security"></a>偵錯工具安全性
偵錯其他處理序的功能可以讓您獲得在他處無法得到的多樣化功能，特別是在遠端偵錯時。 惡意偵錯工具可能會在被偵錯的電腦上散佈更廣泛的損害。

 然而，許多開發人員並不了解也可能會有反向的安全性威脅。 偵錯項目處理序中的惡意程式碼可能會危及偵錯電腦的安全性：有一些必須防範的安全性漏洞。

## <a name="security-best-practices"></a>安全性最佳做法
 在偵錯的程式碼和偵錯工具之間有隱含的信任關係。 如果您願意對其進行偵錯，應該也願意加以執行。 底限是您必須能夠信任要偵錯的項目。 如果不能信任它，則您不應該進行偵錯，或是應該在隔離環境中從能夠容忍危害的電腦上進行偵錯。

 為了降低潛在攻擊面，實際執行電腦上應該停用偵錯。 基於相同的原因，應該永遠不啟用偵錯。

### <a name="managed-debugging-security"></a>Managed 偵錯安全性
 以下列出幾項適用所有 Managed 偵錯的一般建議：

- 當附加至未受信任使用者的處理序時要小心：在執行這項動作時是假設它沒有任何問題的。 當您嘗試附加至未受信任使用者的處理序時，就會出現安全性警告對話方塊確認，詢問您是否想要附加至處理序。 「信任的使用者」包括您，以及安裝 .NET Framework 後電腦上通常會定義的標準使用者集，例如 **aspnet**、 **localsystem**、 **networkservice** 和 **localservice**。 如需詳細資訊，請參閱[安全性警告： 附加至不受信任的使用者所擁有的處理序可能會造成危險。如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)。

- 從網際網路下載專案並載入 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]時要小心。 即使不使用偵錯，這個動作也非常危險。 在執行這項動作時，是假設專案和其中包含的程式碼沒有任何問題。

  如需詳細資訊，請參閱 [Debugging Managed Code](../debugger/debugging-managed-code.md)。

### <a name="remote-debugging-security"></a>遠端偵錯安全性
 本機偵錯通常比遠端偵錯安全。 遠端偵錯會增加能夠探查的整體表面範圍。

 遠端偵錯會使用「Visual Studio 遠端偵錯監視」(msvsmon.exe)，並且在設定方面有幾個安全性建議。 設定驗證模式的慣用方法是「Windows 驗證」，因為「非驗證」模式並不安全。

 ![[記錄] 對話方塊](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")

 當使用 Windows 驗證模式時，請注意，授與不受信任的使用者連線到 msvsmon 的許可權是危險的，因為使用者會被授與裝載 msvsmon 之電腦上的擁有權限。

 請勿在遠端電腦上偵測到未知的進程：有可能會影響執行偵錯工具的機器，或可能會危害 msvsmon 的潛在攻擊。 如果您一定要偵錯未知的處理序，請嘗試在本機偵錯並使用防火牆以避免任何潛在的威脅。

 如需設定 msvsmon 的詳細資訊，請參閱 [設定遠端偵錯程式](../debugger/remote-debugging.md#bkmk_setup)。

### <a name="web-services-debugging-security"></a>Web 服務偵錯安全性
 在本機偵錯比較安全，但是因為在 Web 伺服器上可能並未安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，所以本機偵錯並不實用。 一般來說，偵錯 Web 服務會在遠端完成 (除了在開發期間以外)，因此遠端偵錯安全性的建議也適用於 Web 服務偵錯。 這裡有幾個額外的最佳作法。 如需詳細資訊，請參閱 [Debugging XML Web Services](/previous-versions/ms241873(v=vs.100))。

- 請勿在受到危害的 Web 伺服器上啟用偵錯

- 在偵錯前請確定 Web 伺服器是安全的。 如果不確定是否安全，請勿進行偵錯

- 如果要偵錯公開在網際網路上的 Web 服務要特別小心

### <a name="external-components"></a>外部元件
 請留意程式進行互動的外部元件之信任狀態，特別是如果您並未撰寫其程式碼。 同時留意 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 或偵錯工具會使用的元件。

### <a name="symbols-and-source-code"></a>符號和原始程式碼
 需要考慮安全性的兩個 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 工具如下所示：

- 來源伺服器，提供原始程式碼儲存機制的原始程式碼版本。 當您沒有程式之原始程式碼的最新版時，來源伺服器這就很有用。 [安全性警告：偵錯工具必須執行未受信任的命令](../debugger/security-warning-debugger-must-execute-untrusted-command.md)。

- 符號伺服器，用來提供偵錯系統呼叫期間之損毀所需的符號。

  請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>另請參閱
- [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [安全性警告附加至不受信任的使用者所擁有的處理序可能會造成危險。如果下面的資訊看起來有問題，或者您並不確定，請不要附加至此處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [安全性警告：偵錯工具必須執行未受信任的命令](../debugger/security-warning-debugger-must-execute-untrusted-command.md)