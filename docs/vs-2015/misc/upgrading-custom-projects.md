---
title: 升級自訂專案 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 5c3fd31cfc7cfbf3f7dd687d38483f5bb62703ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491406"
---
# <a name="upgrading-custom-projects"></a>升級自訂專案
若您變更保存於產品不同 Visual Studio 版本間的專案檔資訊，則需要支援將舊版專案檔升級為新版。 若要支援升級，可讓您參與**Visual Studio 轉換精靈**，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面。 此介面包含僅適用於複本升級的機制。 專案升級會在解決方案開啟時發生。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面由 project factory 實作，或至少應取得從 project factory。  
  
 使用的舊機制<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>介面仍支援，但在概念上開啟專案的過程中升級專案系統。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>因此會呼叫介面[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境，即使<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面已呼叫或實作。 這種方法可讓您使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>實作複製專案只有部分升級，並藉由委派的工作進行就地升級 （可能是在新的位置） 的其餘部分<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>介面。  
  
 實作範例<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，請參閱 < [VSSDK 範例](../misc/vssdk-samples.md)。  
  
 下列情節會伴隨專案升級發生：  
  
-   若檔案是專案無法支援的較新格式，則專案必需傳回錯誤以說明此狀況。 此處假設您的產品較舊版本 (例如 Visual Studio .NET 2003) 包含用以檢查版本的程式碼。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>中所指定的旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法，升級會實作為進行就地升級之前在專案開啟。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>中所指定的旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法，升級會實作為複製升級。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>中所指定的旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼叫，則環境以就地升級，升級專案檔，開啟專案後提示使用者。 例如，環境會在使用者開啟舊版解決方案時，提示使用者進行升級。  
  
-   如果<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>中未指定旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼叫，則您必須提示使用者進行升級專案檔。  
  
     下列為升級提示訊息的範例。  
  
     「專案 '%1' 是由舊版 Visual Studio 建立。 若您使用此版本的 Visual Studio 開啟專案，可能無法再使用舊版 Visual Studio 加以開啟。 仍要繼續開啟此專案嗎？」  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>實作 IVsProjectUpgradeViaFactory  
  
1.  實作的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面，特別是<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法在您的 project factory 實作，或讓實作可從您的 project factory 實作呼叫。  
  
2.  如果您想要開啟方案的一部分進行就地升級，請提供旗標<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>作為`VSPUVF_FLAGS`參數，在您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>實作。  
  
3.  如果您想要開啟方案的一部分進行就地升級，請提供旗標<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>作為`VSPUVF_FLAGS`參數，在您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>實作。  
  
4.  如需這兩個步驟 2 和 3，實際的檔案升級步驟，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>，可以在中所述實作 「 實作`IVsProjectUpgade`」 章節，了解，或您可以將實際的檔案升級委派給<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  
  
5.  使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>張貼升級相關的使用者使用 Visual Studio 移轉精靈 」 的訊息。  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> 介面用來實作任何一種升級專案升級過程中發生需要的檔案。 此介面不會從呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>，但會用作升級專案系統，但主要專案系統的組件檔案的機制可能不會直接察覺。 比方說，若處理編譯器相關檔案和內容的開發小組與處理其餘專案系統的開發小組不同，就會發生此狀況。  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade 實作  
 如果您的專案系統會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，它不能參與**Visual Studio 轉換精靈**。 不過，即使您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面，您可以仍然檔案升級委派給<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>實作。  
  
#### <a name="to-implement-ivsprojectupgrade"></a>實作 IVsProjectUpgrade  
  
1.  當使用者嘗試開啟專案，<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>開啟專案，並在任何其他使用者之前採取動作的專案之後，方法由環境呼叫。 如果已提示使用者升級解決方案，則<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>旗標傳入`grfUpgradeFlags`參數。 如果使用者直接開啟專案，這類可藉由使用**加入現有專案**命令，然後在<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS>旗標不會傳遞，且專案需提示使用者進行升級。  
  
2.  以回應<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>呼叫時，專案必須評估是否已升級專案檔。 如果專案不需要將專案類型升級至新的版本，則可以只傳回<xref:Microsoft.VisualStudio.VSConstants.S_OK>旗標。  
  
3.  如果專案需要將專案類型升級至新的版本，則必須判斷是否可以修改專案檔藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>方法並傳入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>如`rgfQueryEdit`參數。 專案接著需執行下列動作：  
  
    -   如果`VSQueryEditResult`中傳回的值`pfEditCanceled`參數是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>，則升級可以繼續進行，因為專案檔可寫入。  
  
    -   如果`VSQueryEditResult`中傳回的值`pfEditCanceled`參數是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>並`VSQueryEditResult`值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>位元集，然後<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>必需傳回失敗，因為使用者應該解析權限問題本身。 專案接著應執行下列動作：  
  
         向使用者回報錯誤，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>。 並傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>錯誤碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。  
  
    -   如果`VSQueryEditResult`值是<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>並`VSQueryEditResultFlags`值具有<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>位元集，則專案檔應該藉由呼叫簽出<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>， <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>，...)。  
  
4.  如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>專案檔的呼叫會導致檔案簽出和要擷取的最新版本，然後卸載並重新載入專案。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>一旦建立專案的另一個執行個體一次呼叫方法。 在第二次呼叫時，專案檔即可寫入磁碟。建議專案使用 .OLD 副檔名以先前格式儲存專案檔複本，變更其必要升級，然後以新格式儲存專案檔。 同樣地，如果升級程序的任何部分失敗，此方法必須藉由指出失敗傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>。 這會導致專案從方案總管卸載。  
  
     請務必了解環境中的情況中，就會發生的完整程序呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>（指定 ReportOnly 的值） 的方法會傳回<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>而<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>旗標。  
  
5.  使用者嘗試開啟專案檔。  
  
6.  環境呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>實作。  
  
7.  如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>會傳回`true`，則環境會呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>實作。  
  
8.  環境呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>實作，以開啟檔案，並初始化專案物件，例如 Project1。  
  
9. 環境呼叫您的 `IVsProjectUpgrade::UpgradeProject` 實作，以判斷是否需要升級專案檔。  
  
10. 您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>，並傳入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>如`rgfQueryEdit`參數。  
  
11. 環境傳回<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>for`VSQueryEditResult`並<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags>中設定位元`VSQueryEditResultFlags`。  
  
12. 您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>實作會呼叫`IVsQueryEditQuerySave::QueryEditFiles`(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>， <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>)。  
  
 此呼叫可能導致您的專案檔新複本簽出、擷取到最新版本，且需要重新載入您的專案檔。 此時會發生下列兩種情況之一：  
  
-   如果您處理您自己的專案重新載入，則環境會呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>(VSITEMID_ROOT) 實作。 當您收到此呼叫時，請重新載入專案的第一個執行個體 (Project1)，並繼續升級專案檔。 環境可讓您知道，是否您傳回處理您自己的專案重新載入`true`for <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。  
  
-   如果您不會處理您自己的專案重新載入，則傳回`false`for <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)。 在此情況下前, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True)， [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True)，) 傳回時，環境就會建立另一個新專案，例如 Project2 執行個體為如下所示：  
  
    1.  環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>您第一個專案，在物件上 Project1，因此置於此物件的非作用中狀態。  
  
    2.  環境呼叫您的 `IVsProjectFactory::CreateProject` 實作，以建立您的專案的第二個執行個體 (Project2)。  
  
    3.  環境呼叫您的 `IPersistFileFormat::Load` 實作，以開啟檔案並將第二個專案物件 (Project2) 初始化。  
  
    4.  環境第二次呼叫 `IVsProjectUpgrade::UpgradeProject` ，以判斷是否應升級專案物件。 不過，此呼叫會在專案新的第二個執行個體 (Project2) 執行。 此為在解決方案中開啟的專案。  
  
        > [!NOTE]
        >  第一個專案，Project1 會變成非使用中的狀態，則您必須傳回的執行個體中<xref:Microsoft.VisualStudio.VSConstants.S_OK>從第一次呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>實作。 請參閱[基本專案](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36)實作`IVsProjectUpgrade::UpgradeProject`。  
  
    5.  您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>，並傳入的值<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>如`rgfQueryEdit`參數。  
  
    6.  環境傳回<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>和升級可以繼續進行，因為專案檔可寫入。  
  
 如果您無法升級，則傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>從`IVsProjectUpgrade::UpgradeProject`。 若不需要升級或您選擇不升級，請將 `IVsProjectUpgrade::UpgradeProject` 呼叫視為無作業。 如果您傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>，預留位置節點加入至您的專案的方案。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 轉換精靈](http://msdn.microsoft.com/en-us/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [升級專案項目](../misc/upgrading-project-items.md)   
 [專案](../extensibility/internals/projects.md)