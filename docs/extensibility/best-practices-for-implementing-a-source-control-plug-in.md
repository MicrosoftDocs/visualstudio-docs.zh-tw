---
title: "實作原始檔控制外掛程式的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9099d652012fb8b45b7b79f9c620f4102e7af602
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>實作原始檔控制外掛程式的最佳作法
下列技術詳細資料可協助您能夠可靠地實作原始檔控制外掛程式[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="memory-management-issues"></a>記憶體管理問題  
 在大部分情況下，整合式的開發環境 (IDE)，也就是呼叫端，釋出，並會配置記憶體。 原始檔控制外掛程式傳回呼叫端配置的緩衝區中的字串和其他項目。 其發生的特定函數的描述中會標註例外狀況。  
  
## <a name="arrays-of-file-names"></a>檔案名稱的陣列  
 檔案的陣列傳遞時，它不會為連續的檔案名稱陣列。 它會當做指標的陣列傳遞至檔案名稱。 例如，在[SccGet](../extensibility/sccget-function.md)，檔案名稱傳遞的`lpFileNames`參數，其中`lpFileNames`實際上是指向`char **`。 `lpFileNames`[0] 是指向 first name `lpFileNames`[1] 是指向第二個名稱，等等。  
  
## <a name="large-model"></a>大型模型  
 所有指標都是 32 位元，即使在 16 位元作業系統上。  
  
## <a name="fully-qualified-paths"></a>完整的路徑  
 其中的檔案名稱或目錄指定做為引數，它們必須是完整的路徑或 UNC 路徑，不含結束的反斜線。 負責的原始檔控制外掛程式，以便在轉譯這些相對路徑，如果，這是基礎的原始檔控制系統的需求。  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>指定完整的路徑註冊 dll  
 IDE 會從相對路徑 (例如，.\NewProvider.dll)，不會再載入 Dll。 必須指定 DLL 的完整路徑 （例如 C:\Providers\NewProvider.dll）。 此需求可在 IDE 的安全性強化藉由防止未經授權或模擬的原始檔控制 Dll 的載入。  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>當您安裝您的原始檔控制外掛程式時檢查現有 VSSCI 外掛程式  
 安裝程式的原始檔控制外掛程式計劃的使用者可能已經有現有原始檔控制外掛程式在電腦上安裝。 安裝 （安裝程式） 程式外掛程式，您建立應該判斷是否有相關的登錄機碼的現有值。 如果已經設定這些機碼，您的安裝程式應該詢問使用者是否為預設原始檔控制外掛程式註冊您的外掛程式，並取代的已安裝。  
  
## <a name="error-result-codes-and-reporting"></a>錯誤結果碼和報告  
 `SCC_OK`傳回原始檔控制函式程式碼表示此作業已成功的所有檔案。 如果作業失敗，它預期會傳回發生的最後一個錯誤碼。  
  
 報告的規則是，如果在 IDE 中發生錯誤，IDE 會負責向它報告。 如果在原始檔控制系統中發生錯誤，原始檔控制外掛程式負責向它報告。 比方說，「 目前沒有選取任何檔案 」 會報告在 IDE 中，而會報告 「 此檔案已簽出 」 外掛程式。  
  
## <a name="the-context-structure"></a>內容結構  
 呼叫期間[SccInitialize](../extensibility/sccinitialize-function.md)，呼叫端傳遞`ppvContext`參數未初始化 void 的控制代碼。 原始檔控制外掛程式可以忽略此參數，或是配置任何種類的結構，然後將該結構的指標放入傳遞指標。 IDE 不了解此結構中，但此結構傳遞指標到每個其他外掛程式的呼叫。 這提供有價值的內容快取資訊的外掛程式，它可用來維護跨函式呼叫持續發生，而不使用全域變數的全域狀態資訊。 此外掛程式負責釋放在呼叫結構[SccUninitialize](../extensibility/sccuninitialize-function.md)。  
  
 如果外掛程式設定`SCC_CAP_REENTRANT`位元[SccInitialize](../extensibility/sccinitialize-function.md) (特別是，在`lpSccCaps`參數)，多個內容結構用來追蹤已開啟的所有專案。  
  
## <a name="bitflags-and-other-command-options"></a>位元旗標和其他命令選項  
 每個命令，例如[SccGet](../extensibility/sccget-function.md)，IDE 可以指定變更的命令行為的許多選項。  
  
 API 支援的某些選項，透過 ide 設定`fOptions`參數。 這些選項如下所述[特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)連同它們會影響的命令。 一般情況下，這些是的選項，就不會提示使用者。  
  
 最使用者可設定的設定選項中未定義這種方式，因為它們廣泛異原始檔控制外掛程式。因此，建議的機制是**進階** 按鈕。 例如，在**取得**對話方塊中，IDE 會顯示其了解，但它也會顯示資訊**進階**如果外掛程式都具有此命令的選項按鈕。 當使用者按一下**進階**按鈕，IDE 呼叫[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)啟用原始檔控制外掛程式，以提示使用者輸入資訊，例如位元旗標或日期/時間。 外掛程式會傳回這項資訊傳遞時所傳回的結構中`SccGet`命令。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)