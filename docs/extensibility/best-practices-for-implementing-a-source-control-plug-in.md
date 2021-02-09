---
title: 執行原始檔控制外掛程式-最佳作法
description: 請參閱這些技術詳細資料，以協助您在 Visual Studio 中可靠地執行原始檔控制外掛程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80a944c077d520d6d9ecac9557179311ecf20281
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893070"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>執行原始檔控制外掛程式的最佳作法
下列技術詳細資料可協助您在中可靠地執行原始檔控制外掛程式 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

## <a name="memory-management-issues"></a>記憶體管理問題
 在大部分的情況下，整合式開發環境 (IDE) ，也就是呼叫端、釋放和配置記憶體。 原始檔控制外掛程式會在呼叫端配置的緩衝區中傳回字串和其他專案。 例外狀況會在其發生所在的特定函式說明中注明。

## <a name="arrays-of-file-names"></a>檔案名陣列
 傳遞檔案的陣列時，不會以連續的檔案名陣列形式傳遞。 它會以指標陣列的形式傳遞至檔案名。 例如，在 [SccGet](../extensibility/sccget-function.md)中，檔案名是由 `lpFileNames` 參數傳遞，其中實際上是的 `lpFileNames` 指標 `char **` 。 `lpFileNames`[0] 是第一個名稱的指標， `lpFileNames` [1] 是第二個名稱的指標，依此類推。

## <a name="large-model"></a>大型模型
 所有指標都是32位，甚至是在16位的作業系統上。

## <a name="fully-qualified-paths"></a>完整路徑
 當檔案名或目錄指定為引數時，它們必須是完整路徑或 UNC 路徑，不含結尾的反斜線。 如果這是基礎原始檔控制系統的需求，則原始檔控制外掛程式必須負責將它們轉譯為相對路徑。

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>指定已註冊 DLL 的完整路徑
 IDE 不再從相對路徑載入 Dll (例如 *.\NewProvider.dll*) 。 必須指定 DLL 的完整路徑 (例如 *C:\Providers\NewProvider.dll*) 。 這項需求會防止載入未授權或模擬的原始檔控制 Dll，藉此增強 IDE 的安全性。

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>當您安裝原始檔控制外掛程式時，檢查現有的 VSSCI 外掛程式
 計畫安裝原始檔控制外掛程式的使用者可能已在電腦上安裝現有的原始檔控制外掛程式。 您所建立之外掛程式的安裝 (安裝) 程式應判斷相關登錄機碼是否有現有的值。 如果已設定這些金鑰，您的安裝程式應該會詢問使用者是否要將外掛程式註冊為預設的原始檔控制外掛程式，並取代已安裝的外掛程式。

## <a name="error-result-codes-and-reporting"></a>錯誤結果碼和報告
 `SCC_OK`原始檔控制函數的傳回碼會指出所有檔案的作業都已成功。 如果作業失敗，則預期會傳回最後一個遇到的錯誤碼。

 報告的規則是，如果 IDE 中發生錯誤，IDE 會負責報告它。 如果原始檔控制系統中發生錯誤，則原始檔控制外掛程式負責報告它。 比方說，IDE **目前未選取任何** 檔案，而此檔案已 **簽出** 會由外掛程式回報。

## <a name="the-context-structure"></a>內容結構
 呼叫 [SccInitialize](../extensibility/sccinitialize-function.md)時，呼叫端 `ppvContext` 會傳遞參數，這是 void 的未初始化控制碼。 原始檔控制外掛程式可以忽略這個參數，也可以配置任何種類的結構，並將該結構的指標放到傳遞的指標中。 IDE 不了解此結構，但它會將此結構的指標傳遞至外掛程式中的每個其他呼叫。 這會提供重要的內容快取資訊給外掛程式，以便在不使用全域變數的情況下，用來維護跨函式呼叫持續存在的全域狀態資訊。 外掛程式會負責釋放 [SccUninitialize](../extensibility/sccuninitialize-function.md)呼叫的結構。

 如果外掛程式在 `SCC_CAP_REENTRANT` [SccInitialize](../extensibility/sccinitialize-function.md) 中設定位 (明確地說，在 `lpSccCaps` 參數) 中，會使用多個內容結構來追蹤所有開啟的專案。

## <a name="bitflags-and-other-command-options"></a>位旗標和其他命令選項
 針對每個命令（例如 [SccGet](../extensibility/sccget-function.md)），IDE 可以指定許多選項來變更命令的行為。

 API 支援 IDE 透過參數設定某些選項 `fOptions` 。 這些選項會在 [特定命令所使用的位旗標](../extensibility/bitflags-used-by-specific-commands.md) 中描述，以及它們所影響的命令。 一般而言，這些是不會提示使用者的選項。

 大部分使用者可設定的設定選項都不會以這種方式定義，因為它們在原始檔控制外掛程式之間會有很大的差異。因此，建議的機制是 [ **Advanced** ] 按鈕。 例如，在 [ **取得** ] 對話方塊中，IDE 只會顯示其瞭解的資訊，但如果外掛程式具有此命令的選項，也會顯示 [ **Advanced** ] 按鈕。 當使用者按一下 [ **Advanced （Advanced** ）] 按鈕時，IDE 會呼叫 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) ，讓原始檔控制外掛程式提示使用者輸入資訊，例如位旗標或日期/時間。 外掛程式會在命令期間傳回的結構中傳回這項資訊 `SccGet` 。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)
