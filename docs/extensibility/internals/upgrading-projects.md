---
title: "將專案升級 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 060823a04127480ef8de387200425a34c6ef1178
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="upgrading-projects"></a>升級專案
變更從一個版本的專案模型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]下可能需要的專案和方案升級，讓它們可以在較新版本上執行。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]提供可用來實作您自己的專案中的升級支援的介面。  
  
## <a name="upgrade-strategies"></a>升級策略  
 若要支援升級，您的專案系統的實作必須定義並實作升級的策略。 決定策略，您可以選擇支援的並存 (SxS) 備份、 複製備份，或兩者。  
  
-   SxS 備份表示專案複製只有在需要升級適當地加入適當的檔案名稱尾碼，例如，".old"的檔案。  
  
-   複製備份的方式，專案會將所有專案項目都複製到使用者提供的備份位置。 然後會升級原始專案的位置相關的檔案。  
  
## <a name="how-upgrade-works"></a>如何升級的運作方式  
 當較早的版本建立的方案[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]方案檔案來判斷是否需要進行升級的 IDE 檢查較新版本中開啟。 如果升級為必要項，**升級精靈**引導使用者進行升級程序就會自動啟動。  
  
 當升級需求的解決方案時，它會查詢每個專案 factory，其升級的策略。 策略會決定 project factory 是否支援複製備份 」 或 「 SxS 備份。 若要傳送的資訊**升級精靈**，收集備份所需的資訊以及對使用者呈現的適用選項。  
  
### <a name="multi-project-solutions"></a>多專案方案  
 如果方案包含多個專案的升級策略之間的差異，例如專案 factory 只支援 SxS 備份的 c + + 專案時，Web 專案僅支援複製備份，必須談判出升級的策略。  
  
 方案會查詢每個專案 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>。 然後它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>以查看是否需要升級通用專案的檔案，並決定支援的升級策略。 **升級精靈**然後叫用。  
  
 使用者完成精靈之後<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>執行實際升級每個專案 factory 上呼叫。 若要簡化備份，提供 IVsProjectUpgradeViaFactory 方法<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服務記錄檔的升級程序詳細資料。 此服務無法快取。  
  
 更新所有相關的通用檔案之後, 可以選擇每個專案 factory 具現化專案。 專案實作必須支援<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼叫方法，再升級所有相關的專案項目。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法不提供以下 SVsUpgradeLogger 服務。 您可以取得此服務呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>。  
  
## <a name="best-practices"></a>最佳作法  
 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>服務，以檢查是否可以編輯檔案，然後再編輯它，且可以將它儲存在儲存它之前。 這可協助您的備份和升級的實作會處理原始檔控制下的專案檔案、 檔案權限不足，等等。  
  
 使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服務備份的所有階段，並升級為提供成功或失敗的升級程序的相關資訊。  
  
 如需備份及將專案升級的詳細資訊，請參閱 < 註解的 IVsProjectUpgrade vsshell2.idl 中。  
  
## <a name="upgrading-custom-projects"></a>升級自訂專案
若您變更保存於產品不同 Visual Studio 版本間的專案檔資訊，則需要支援將舊版專案檔升級為新版。 若要支援升級，可讓您參與**Visual Studio 轉換精靈**，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面。 此介面包含僅適用於複本升級的機制。 專案升級會在解決方案開啟時發生。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面實作由 project factory，或應該至少需要從 project factory。  
  
 使用的舊機制<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>介面仍支援，但在概念上開啟專案的一部分會升級專案系統。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>介面因此會呼叫[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境即使<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面已呼叫或實作。 這種方法可讓您使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>實作複製專案僅部分升級，並委派進行就地升級 （可能是在新的位置） 工作的其餘部分<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>介面。  
  
 如需範例實作的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，請參閱[VSSDK 範例](http://aka.ms/vs2015sdksamples)。  
  
 下列情節會伴隨專案升級發生：  
  
-   若檔案是專案無法支援的較新格式，則專案必需傳回錯誤以說明此狀況。 這是假設您的產品較舊的版本，包含要檢查版本的程式碼。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>中所指定的旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法，升級會實作為專案開啟之前就地升級。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>中所指定的旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法，升級會實作為複製升級。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>中所指定的旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼叫，然後開啟專案之後，以就地升級，升級專案檔的使用者提示環境。 例如，環境會在使用者開啟舊版解決方案時，提示使用者進行升級。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>中未指定旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼叫，則您必須提示使用者升級專案檔。  
  
     下列為升級提示訊息的範例。  
  
     「專案 '%1' 是由舊版 Visual Studio 建立。 若您使用此版本的 Visual Studio 開啟專案，可能無法再使用舊版 Visual Studio 加以開啟。 仍要繼續開啟此專案嗎？」  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>實作 IVsProjectUpgradeViaFactory  
  
1.  實作的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面，特別是<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法在您的 project factory 實作，或讓實作可從您 project factory 實作呼叫。  
  
2.  如果您想要開啟方案的一部分時執行就地升級，請提供旗標<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>為`VSPUVF_FLAGS`參數中的您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>實作。  
  
3.  如果您想要開啟方案的一部分時執行就地升級，請提供旗標<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>為`VSPUVF_FLAGS`參數中的您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>實作。  
  
4.  如需這兩個步驟 2 和 3，實際的檔案升級步驟，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>，可以實作中所述"實作`IVsProjectUpgade`」 區段下，或您可以將實際的檔案升級委派給<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  
  
5.  使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>張貼升級相關的使用者使用 Visual Studio 移轉精靈 」 的訊息。  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>介面用來實作任何一種檔案升級所需進行專案升級的一部分。 這個介面不會從呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>，但會用作升級檔案屬於的專案系統，但主要專案系統的機制可能不會直接察覺。 比方說，若處理編譯器相關檔案和內容的開發小組與處理其餘專案系統的開發小組不同，就會發生此狀況。  
  
### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade 實作  
 如果您的專案系統實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，它不能參與**Visual Studio 轉換精靈**。 不過，即使您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面，您可以仍然檔案升級委派給<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>實作。  
  
#### <a name="to-implement-ivsprojectupgrade"></a>實作 IVsProjectUpgrade  
  
1.  當使用者嘗試開啟專案，<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>專案開啟後可以在專案上採取動作之前的任何其他使用者環境所呼叫方法。 如果已提示使用者升級解決方案，然後在<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>旗標會傳遞中`grfUpgradeFlags`參數。 如果使用者直接開啟專案，這類可藉由使用**加入現有專案**命令，然後在<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>旗標不會傳遞，且專案需提示使用者進行升級。  
  
2.  以回應<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼叫時，專案必須評估是否已升級專案檔。 如果專案不需要將專案類型升級至新的版本，則可以只傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>旗標。  
  
3.  如果專案需要將專案類型升級至新的版本，則必須判斷是否可以修改專案檔藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>方法然後傳入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>如`rgfQueryEdit`參數。 專案接著需執行下列動作：  
  
    -   如果`VSQueryEditResult`中傳回值`pfEditCanceled`參數是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>，則升級可以繼續，因為專案檔可寫入。  
  
    -   如果`VSQueryEditResult`中傳回值`pfEditCanceled`參數是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和`VSQueryEditResult`值具有<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>設定位元，然後<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>必需傳回失敗，因為使用者應該解析權限問題本身。 專案接著應執行下列動作：  
  
         將錯誤回報給使用者，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>並傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>錯誤碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  
  
    -   如果`VSQueryEditResult`值是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和`VSQueryEditResultFlags`值具有<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>設定位元，則專案檔應該藉由呼叫簽出<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>， <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>，...)。  
  
4.  如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>專案檔上的呼叫導致檔案簽出和要擷取的最新版本，然後卸載再重新載入專案。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>一旦建立專案的另一個執行個體一次呼叫方法。 在第二次呼叫時，專案檔即可寫入磁碟。建議專案使用 .OLD 副檔名以先前格式儲存專案檔複本，變更其必要升級，然後以新格式儲存專案檔。 同樣地，如果升級程序的任何部分失敗，此方法必須指出失敗藉由傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>。 這會導致專案從方案總管卸載。  
  
     請務必了解環境中的情況中，就會發生的完整程序呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>（指定 ReportOnly 的值） 的方法會傳回<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>旗標。  
  
5.  使用者嘗試開啟專案檔。  
  
6.  環境呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>實作。  
  
7.  如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>傳回`true`，則環境呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>實作。  
  
8.  環境呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>實作，以開啟檔案並將專案物件初始化，例如 Project1。  
  
9. 環境呼叫您的 `IVsProjectUpgrade::UpgradeProject` 實作，以判斷是否需要升級專案檔。  
  
10. 您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>並傳入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>如`rgfQueryEdit`參數。  
  
11. 環境傳回<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>如`VSQueryEditResult`和<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>中設定位元`VSQueryEditResultFlags`。  
  
12. 您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>實作會呼叫`IVsQueryEditQuerySave::QueryEditFiles`(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>， <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>)。  
  
 此呼叫可能導致您的專案檔新複本簽出、擷取到最新版本，且需要重新載入您的專案檔。 此時會發生下列兩種情況之一：  
  
-   如果您處理自己的專案重新載入，則環境會呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>(VSITEMID_ROOT) 實作。 當您收到此呼叫時，請重新載入專案的第一個執行個體 (Project1)，並繼續升級專案檔。 環境便知道您處理自己的專案重新載入，是否您傳回`true`如<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。  
  
-   如果您不會處理自己的專案重新載入，則傳回`false`如<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。 在此情況下前, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>（QEF_ForceEdit_NoPrompting、 QEF_DisallowInMemoryEdits） 傳回時，環境就會建立您的專案，例如 Project2 的另一個新的執行個體，如下所示：  
  
    1.  環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>您第一個專案物件 （Project1） 上因此置於此物件的非作用中狀態。  
  
    2.  環境呼叫您的 `IVsProjectFactory::CreateProject` 實作，以建立您的專案的第二個執行個體 (Project2)。  
  
    3.  環境呼叫您的 `IPersistFileFormat::Load` 實作，以開啟檔案並將第二個專案物件 (Project2) 初始化。  
  
    4.  環境第二次呼叫 `IVsProjectUpgrade::UpgradeProject` ，以判斷是否應升級專案物件。 不過，此呼叫會在專案新的第二個執行個體 (Project2) 執行。 此為在解決方案中開啟的專案。  
  
        > [!NOTE]
        >  第一個專案，Project1 會放在非使用中狀態，則您必須在傳回的執行個體中<xref:Microsoft.VisualStudio.VSConstants.S_OK>從第一個呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>實作。  
  
    5.  您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>並傳入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>如`rgfQueryEdit`參數。  
  
    6.  環境傳回<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和升級可以繼續，因為專案檔可寫入。  
  
 如果您無法升級，傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>從`IVsProjectUpgrade::UpgradeProject`。 若不需要升級或您選擇不升級，請將 `IVsProjectUpgrade::UpgradeProject` 呼叫視為無作業。 如果您傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>，預留位置節點會加入至專案的方案。  
  
## <a name="upgrading-project-items"></a>升級專案項目
  
如果您新增或管理您不會實作專案系統內的項目，您可能需要參與專案升級程序。 採用的 Crystal Reports 是可以加入至專案系統中的項目範例。  
  
 一般而言，專案項目實作者想要利用已經完全具現化和升級的專案，因為它們必須知道哪些參考的專案，以及其他專案屬性為何要升級的決策。  
  
### <a name="to-get-the-project-upgrade-notification"></a>取得專案的升級通知  
  
1.  設定<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>旗標 （定義於 vsshell80.idl） 在您的專案項目實作。 這會導致您的專案項目 VSPackage 也可以自動載入時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]殼層決定專案系統正在升級。  
  
2.  建議<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>介面透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>方法。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>之後的專案系統實作完成升級作業，並建立新的升級的專案時，就會引發介面。 根據這種情況，<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>之後引發介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>，或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>方法。  
  
### <a name="to-upgrade-the-project-item-files"></a>若要升級專案項目檔案  
  
1.  您必須仔細管理檔案備份程序，在您的專案項目實作。 這特別適用於並行的備份，其中`fUpgradeFlag`參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法設定為<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>、 側邊檔案指定為".old"沿著放置先前備份的檔案。 當專案已升級的系統時間比舊的備份的檔案指定為過時。 此外，它們可能會覆寫除非您採取特定的步驟，為防止這個情況。  
  
2.  在您的專案項目取得的專案升級時，通知**Visual Studio 轉換精靈**仍會顯示。 因此，您應該使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>介面，以提供精靈使用者介面來升級的訊息。  
  
## <a name="see-also"></a>請參閱  
 [專案](../../extensibility/internals/projects.md)   
