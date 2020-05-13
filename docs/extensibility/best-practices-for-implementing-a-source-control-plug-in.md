---
title: 實現原始程式碼管理外掛程式的最佳做法 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740049"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>實現原始碼管理外掛程式的最佳做法
以下技術詳細資訊可以説明您可靠地實現中的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]原始程式碼管理外掛程式。

## <a name="memory-management-issues"></a>記憶體管理問題
 在大多數情況下,集成開發環境 (IDE),即調用方,釋放和分配記憶體。 原始程式碼管理外掛程式傳回呼叫方分配的緩衝區中的字串和其他項。 異常在特定函數發生的位置的說明中註明。

## <a name="arrays-of-file-names"></a>檔案名陣列
 傳遞文件陣列時,不會作為連續的檔名陣組傳遞。 它作為指向檔名的指標陣列傳遞。 例如,在[SccGet](../extensibility/sccget-function.md)中,檔`lpFileNames`名由 參數`lpFileNames`傳遞,其中 實際上是指向`char **`的指標。 `lpFileNames`{0} 是指向名字的指標,[1]`lpFileNames`是指向第二個名稱的指標,等等。

## <a name="large-model"></a>大模型
 所有指標都是 32 位元,即使在 16 位元作業系統上也是如此。

## <a name="fully-qualified-paths"></a>完全合格的路徑
 如果檔名或目錄被指定為參數,則它們必須是完全限定的路徑或 UNC 路徑,而不進行結束回斜杠。 如果是基礎原始程式碼管理系統的要求,原始程式碼管理外掛程式有責任將這些路徑轉換為相對路徑。

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>指定為註冊的 DLL 指定完全限定的路徑
 IDE 不再從相對路徑載入 DLL(例如 *,._NewProvider.dll*)。 必須指定 DLL 的完整路徑(例如 *,C:\提供程式\NewProvider.dll*)。 此要求通過防止載入未經授權的或類比的原始程式碼管理 DLL 來增強 IDE 的安全性。

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>安裝原始碼管理外掛程式時,請檢查現有 VSSCI 外掛程式
 計劃安裝原始程式碼管理外掛程式的使用者可能已經在電腦上安裝了現有的原始程式碼管理外掛程式。 您創建的外掛程式的安裝(設置)程式應確定是否存在相關註冊表項的現有值。 如果已設置這些金鑰,安裝程式應詢問使用者是否將外掛程式註冊為預設原始程式碼管理外掛程式,並替換已安裝的外掛程式。

## <a name="error-result-codes-and-reporting"></a>錯誤結果代碼和報告
 原始程式`SCC_OK`碼 控制函數的返回代碼指示所有檔的操作都已成功。 如果操作失敗,則預期將返回遇到的最後一個錯誤代碼。

 報告的規則是,如果 IDE 中發生錯誤,IDE 負責報告錯誤。 如果原始程式碼管理系統中出現錯誤,原始程式碼管理外掛程式負責報告它。 例如,IDE 不會報告**當前選定的任何檔**,而**此檔已簽出**,外掛程式將報告該檔。

## <a name="the-context-structure"></a>內容結構
 在調用[Scc 初始化](../extensibility/sccinitialize-function.md)期間,呼叫`ppvContext`方將參數 傳遞參數,參數是一個未初始化的句柄到 void。 源代碼管理外掛程式可以忽略此參數,也可以分配任何類型的結構,並將指向該結構的指標放入傳遞的指標中。 IDE 不理解此結構,但它將指向此結構的指標傳遞到外掛程式中的每個其他調用中。 這為外掛程式提供了有價值的上下文緩存資訊,它可用於維護在函數調用之間持續存在的全域狀態資訊,而無需使用全域變數。 該外掛程式負責在調用[SccUn初始化](../extensibility/sccuninitialize-function.md)時釋放結構。

 如果外掛程式`SCC_CAP_REENTRANT`在[Scc 初始化](../extensibility/sccinitialize-function.md)(特別是`lpSccCaps`參數中)中設置位,則使用多個上下文結構來跟蹤打開的所有專案。

## <a name="bitflags-and-other-command-options"></a>位元旗標和其他指令選項
 對於每個命令(如[SccGet),IDE](../extensibility/sccget-function.md)可以指定許多選項來更改命令的行為。

 API 支援 IDE 透過`fOptions`參數設定某些選項。 這些選項在[特定命令使用的 Bitflags](../extensibility/bitflags-used-by-specific-commands.md)中描述,以及它們影響的命令。 通常,這些選項不會提示使用者。

 大多數用戶可配置的設置選項不是以這種方式定義的,因為它們在原始程式碼管理外掛程式之間差別很大。因此,建議的機制是一個**高級**按鈕。 例如,在 **「獲取」** 對話方塊中,IDE 僅顯示它理解的資訊,但如果外掛程式具有此命令的選項,則該按鈕也會顯示 **「進階」** 按鈕。 當使用者按下 **「高級」** 按鈕時,IDE 會呼叫[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)以啟用原始程式碼管理外掛程式以提示使用者獲取資訊,例如位標誌或日期/時間。 外掛程式`SccGet`在命令期間傳遞回的結構中返回此資訊。

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
- [建立原始碼管理外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)
