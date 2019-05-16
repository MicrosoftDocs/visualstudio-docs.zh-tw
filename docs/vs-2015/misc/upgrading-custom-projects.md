---
title: 升級自訂專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 5046a35cbc681ede4aff85023feeccd71a61b5b2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693831"
---
# <a name="upgrading-custom-projects"></a>升級自訂專案
若您變更保存於產品不同 Visual Studio 版本間的專案檔資訊，則需要支援將舊版專案檔升級為新版。 若要支援升級，可讓您參與**Visual Studio 轉換精靈**，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面。 此介面包含僅適用於複本升級的機制。 專案升級會在解決方案開啟時發生。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面應由 Project Factory 實作，或至少從 Project Factory 取得。  
  
 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面的舊機制仍受支援，但就概念而言，則是在專案開啟時升級專案系統。 因此即使已呼叫或實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面，<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面仍是由[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 環境呼叫。 此方法可讓您使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 只實作升級的複本與專案部分，並委派 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面就地完成其餘的工作 (可能在新的位置)。  
  
 實作範例<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，請參閱 < [VSSDK 範例](../misc/vssdk-samples.md)。  
  
 下列情節會伴隨專案升級發生：  
  
- 若檔案是專案無法支援的較新格式，則專案必需傳回錯誤以說明此狀況。 此處假設您的產品較舊版本 (例如 Visual Studio .NET 2003) 包含用以檢查版本的程式碼。  
  
- 若在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法中指定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> 旗標，會在專案開啟前以就地升級的方式實作升級。  
  
- 若在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法中指定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> 旗標，會以複本升級的方式實作升級。  
  
- 若在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼叫中指定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> 旗標，環境則會在專案開啟後提示使用者，以就地升級方式來升級專案檔。 例如，環境會在使用者開啟舊版解決方案時，提示使用者進行升級。  
  
- 若未在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼叫中指定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> 旗標，則您必須提示使用者升級專案檔。  
  
     下列為升級提示訊息的範例。  
  
     「專案 '%1' 是由舊版 Visual Studio 建立。 若您使用此版本的 Visual Studio 開啟專案，可能無法再使用舊版 Visual Studio 加以開啟。 仍要繼續開啟此專案嗎？」  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>實作 IVsProjectUpgradeViaFactory  
  
1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面的方法 (尤其是您 Project Factory 實作中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法)，或讓實作可從您的 Project Factory 實作加以呼叫。  
  
2. 若您想在解決方案開啟時執行就地升級，請提供旗標 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> 作為您 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 實作中的 `VSPUVF_FLAGS` 參數。  
  
3. 若您想在解決方案開啟時執行就地升級，請提供旗標 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> 作為您 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 實作中的 `VSPUVF_FLAGS` 參數。  
  
4. 若是使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 的步驟 2 與 3 (實際的檔案升級步驟)，可依下方＜實作 `IVsProjectUpgade`＞章節所述加以實作，也可將實際的檔案升級委派給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  
  
5. 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> 的方法，為 [Visual Studio 移轉精靈] 的使用者張貼升級相關訊息。  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> 介面的用途是實作任何需要在專案升級時發生的檔案升級種類。 此介面並非從 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 呼叫，但會用作升級專案系統內檔案的機制，而主要專案系統可能不會直接察覺到。 比方說，若處理編譯器相關檔案和內容的開發小組與處理其餘專案系統的開發小組不同，就會發生此狀況。  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade 實作  
 如果您的專案系統會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，它不能參與**Visual Studio 轉換精靈**。 不過，即使您實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面，仍可將檔案升級委派給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 實作。  
  
#### <a name="to-implement-ivsprojectupgrade"></a>實作 IVsProjectUpgrade  
  
1. 當使用者嘗試開啟專案時，環境會在專案開啟後、使用者可對專案進行任何動作前，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 方法 若已提示使用者升級解決方案，則會將 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> 旗標傳入 `grfUpgradeFlags` 參數。 如果使用者直接開啟專案，這類可藉由使用**加入現有專案**命令，然後在<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>旗標不會傳遞，且專案需提示使用者進行升級。  
  
2. 為了回應 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼叫，專案必須評估專案檔是否已升級。 若專案不需要將專案類型升級至新版，則可以只傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 旗標。  
  
3. 若專案需要將專案類型升級至新版，則必須判斷是否可以透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法並傳入 `rgfQueryEdit` 參數的 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 值來修改專案檔。 專案接著需執行下列動作：  
  
   - 若 `pfEditCanceled` 參數中傳回的 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>，即表示專案檔可寫入，所以可繼續更新。  
  
   - 若 `pfEditCanceled` 參數中傳回的 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>，且 `VSQueryEditResult` 值有 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> 位元集，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 會因為使用者必須自行解決權限問題，而必需傳回失敗。 專案接著應執行下列動作：  
  
        透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 向使用者回報錯誤， 並將 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> 錯誤碼傳回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  
  
   - 若 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>，且 `VSQueryEditResultFlags` 值有 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> 位元集，則應透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 簽出專案檔(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>、...)。  
  
4. 若對專案檔的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 呼叫導致檔案簽出，並擷取到最新版本，則會先將專案卸載再將其重新載入。 一旦建立專案的另一個執行個體，就會再次呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 方法。 在第二次呼叫時，專案檔即可寫入磁碟。建議專案使用 .OLD 副檔名以先前格式儲存專案檔複本，變更其必要升級，然後以新格式儲存專案檔。 同樣地，若升級程序的任一部分失敗，此方法必須傳回 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> 以表示失敗。 這會導致專案從方案總管卸載。  
  
    請務必了解在對 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法 (指定 ReportOnly 的值) 的呼叫傳回 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> 與 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> 旗標的案例中，該環境發生的完整程序。  
  
5. 使用者嘗試開啟專案檔。  
  
6. 環境呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 實作。  
  
7. 若 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 傳回 `true`，則環境會呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 實作。  
  
8. 環境呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> 實作，以開啟檔案並將專案物件初始化，例如 Project1。  
  
9. 環境呼叫您的 `IVsProjectUpgrade::UpgradeProject` 實作，以判斷是否需要升級專案檔。  
  
10. 您呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>，並傳入 `rgfQueryEdit` 參數的 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 值。  
  
11. 環境為 `VSQueryEditResult` 傳回 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>，且 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> 位元設定於 `VSQueryEditResultFlags`。  
  
12. 您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 實作呼叫 `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>)。  
  
    此呼叫可能導致您的專案檔新複本簽出、擷取到最新版本，且需要重新載入您的專案檔。 此時會發生下列兩種情況之一：  
  
- 若您處理自己的專案重新載入，則環境會呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) 實作。 當您收到此呼叫時，請重新載入專案的第一個執行個體 (Project1)，並繼續升級專案檔。 若您為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) 傳回 `true`，環境便知道您會處理自己的專案重新載入。  
  
- 若您未處理自己的專案重新載入，則為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) 傳回 `false`。 在此情況下前, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True)， [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True)，) 傳回時，環境就會建立另一個新專案，例如 Project2 執行個體為如下所示：  
  
  1. 環境對您的第一個專案物件 (Project1) 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>，讓此物件處於非使用中狀態。  
  
  2. 環境呼叫您的 `IVsProjectFactory::CreateProject` 實作，以建立您的專案的第二個執行個體 (Project2)。  
  
  3. 環境呼叫您的 `IPersistFileFormat::Load` 實作，以開啟檔案並將第二個專案物件 (Project2) 初始化。  
  
  4. 環境第二次呼叫 `IVsProjectUpgrade::UpgradeProject` ，以判斷是否應升級專案物件。 不過，此呼叫會在專案新的第二個執行個體 (Project2) 執行。 此為在解決方案中開啟的專案。  
  
      > [!NOTE]
      > 您的第一個專案執行個體 (Project1) 處於非使用中狀態，因此必須從 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 實作的第一個呼叫傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。 請參閱[基本專案](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36)實作`IVsProjectUpgrade::UpgradeProject`。  
  
  5. 您呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>，並傳入 `rgfQueryEdit` 參數的 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 值。  
  
  6. 環境傳回 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>，並因為專案檔可寫入，所以可繼續更新。  
  
  若您無法升級，請從 `IVsProjectUpgrade::UpgradeProject` 傳回 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>。 若不需要升級或您選擇不升級，請將 `IVsProjectUpgrade::UpgradeProject` 呼叫視為無作業。 若您傳回 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>，預留位置節點就會加入專案的解決方案中。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 轉換精靈](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [升級專案項目](../misc/upgrading-project-items.md)   
 [專案](../extensibility/internals/projects.md)