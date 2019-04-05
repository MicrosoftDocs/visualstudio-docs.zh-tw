---
title: 實作原始檔控制外掛程式的最佳作法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99166c8bf9a76deaa3805bfd8f5ac6db35e5c0a0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941933"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>實作原始檔控制外掛程式的最佳做法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下列的技術詳細資料可協助您可靠地實作原始檔控制外掛程式在[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
## <a name="memory-management-issues"></a>記憶體管理問題  
 在大部分情況下，整合式的開發環境 (IDE)，也就是呼叫端，會釋放，並將記憶體配置。 原始檔控制外掛程式傳回呼叫端配置的緩衝區中的字串和其他項目。 例外狀況會在其發生的特定函數的描述中註明。  
  
## <a name="arrays-of-file-names"></a>檔案名稱的陣列  
 傳遞陣列的檔案時，不會傳遞為連續的檔案名稱陣列。 它會當做指標陣列傳遞至檔案名稱。 例如，在[SccGet](../extensibility/sccget-function.md)，所傳遞的檔案名稱`lpFileNames`參數，其中`lpFileNames`實際上是指向`char **`。 `lpFileNames`[0] 是第一個名稱，指向`lpFileNames`[1] 是第二個名稱和等等的指標。  
  
## <a name="large-model"></a>大型模型  
 所有指標都是 32 位元，即使在 16 位元作業系統上。  
  
## <a name="fully-qualified-paths"></a>完整的路徑  
 其中的檔案名稱，或做為引數會指定目錄，它們必須是完整的路徑或 UNC 路徑，不含結束的反斜線。 它是原始檔控制外掛程式，以便在轉譯為相對路徑，如果也就是，需求為基礎的原始檔控制系統的責任。  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>指定完整的路徑註冊 dll  
 IDE 不會再載入 Dll，從相對路徑 (例如.\NewProvider.dll)。 必須指定 DLL 的完整路徑 （例如 C:\Providers\NewProvider.dll）。 這項需求會加強安全性的 IDE，藉由防止未經授權或模擬的原始檔控制 Dll 的載入。  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>當您安裝您的原始檔控制外掛程式時檢查現有 VSSCI 外掛程式  
 若要安裝您的原始檔控制外掛程式計劃的使用者可能已經有現有原始檔控制外掛程式安裝在電腦上。 （安裝程式） 安裝程式的外掛程式，您建立應該判斷是否有相關的登錄機碼的現有值。 如果已經設定這些機碼，您的安裝程式應該詢問使用者是否為預設原始檔控制外掛程式註冊您的外掛程式，並取代的已安裝。  
  
## <a name="error-result-codes-and-reporting"></a>錯誤結果碼和報告  
 `SCC_OK`傳回原始檔控制函式程式碼指出作業已成功的所有檔案。 如果作業失敗，它預期會傳回發生的最後一個錯誤碼。  
  
 報告的規則是，如果在 IDE 中發生錯誤，IDE 會負責報告它。 如果在原始檔控制系統中發生錯誤，就有一個原始檔控制外掛程式負責報告它。 比方說，"目前沒有選取任何檔案 」 會報告在 IDE 中，而會報告 「 這個檔案已簽出 」 外掛程式。  
  
## <a name="the-context-structure"></a>內容結構  
 在呼叫期間[SccInitialize](../extensibility/sccinitialize-function.md)，呼叫端傳遞`ppvContext`參數，也就是未初始化的控制代碼設為 void。 原始檔控制外掛程式可以忽略這個參數或它可以配置的任何類型的結構，並將該結構的指標放入傳遞的指標。 IDE 不了解此結構中，但它會傳遞的指標，此結構在外掛程式中的每個其他呼叫。 這會提供有用的內容快取資訊的外掛程式，它可用來維護跨函式呼叫持續發生，而不使用全域變數的全域狀態資訊。 外掛程式會負責釋放呼叫上的結構[SccUninitialize](../extensibility/sccuninitialize-function.md)。  
  
 如果外掛程式設定`SCC_CAP_REENTRANT`位元[SccInitialize](../extensibility/sccinitialize-function.md) (特別是在`lpSccCaps`參數)，多個內容結構用來追蹤已開啟的所有專案。  
  
## <a name="bitflags-and-other-command-options"></a>位元旗標和其他命令選項  
 針對每個命令，例如[SccGet](../extensibility/sccget-function.md)，IDE 可以指定命令的行為變更的許多選項。  
  
 此 API 支援透過 ide 的某些選項的設定`fOptions`參數。 這些選項如下所述[特定的命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)以及它們會影響的命令。 一般情況下，這些是的選項，就不會提示使用者。  
  
 最使用者可設定的設定選項中未定義這種方式，因為它們在原始檔控制外掛程式相當廣泛。因此，建議的機制就**進階** 按鈕。 例如，在**取得** 對話方塊中，IDE 會顯示其了解，但它也會顯示資訊**進階**外掛程式都具有為這個命令的選項按鈕。 當使用者按一下**進階**按鈕，IDE 呼叫[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)啟用原始檔控制外掛程式，以提示使用者輸入位元旗標或日期/時間等資訊。 外掛程式會傳回此資訊傳遞時所傳回的結構中`SccGet`命令。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)
