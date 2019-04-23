---
title: 將專案升級 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5aac06c9d06145f288a64deb210e3c8cb1bd2bd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111073"
---
# <a name="upgrading-projects"></a>升級專案

從一個版本的 Visual Studio，到下一個專案模型的變更可能需要專案和方案，會升級，使它們可以較新版本上執行。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]提供可用來實作您自己的專案中的升級支援的介面。

## <a name="upgrade-strategies"></a>升級策略

若要支援升級，您的專案系統實作必須定義和實作的升級策略。 在決定您的策略時，您可以選擇支援的並存 (SxS) 備份、 複製備份，或兩者。

- SxS 備份表示專案會複製那些需要升級的位置，新增適當的檔案名稱尾碼，例如，".old"的檔案。

- 複製專案將所有的專案項目複製到使用者所提供的備份位置的備份方式。 然後會升級原始專案位置的相關檔案。

## <a name="how-upgrade-works"></a>如何升級的運作方式

較新版本中開啟在舊版的 Visual Studio 中建立的方案時，IDE 會檢查以判斷它是否需要升級的方案檔。 如果升級為必要項，**升級精靈**引導使用者完成升級程序時，就會自動啟動。

當升級需求的解決方案時，它會查詢每個專案處理站，其升級策略。 策略會決定 project factory 支援複製備份 」 或 「 SxS 備份。 將資訊傳送至**升級精靈**，其可收集備份所需的資訊，並向使用者呈現的適用選項。

### <a name="multi-project-solutions"></a>多專案的方案

如果方案包含多個專案，而且不同的升級策略，例如當C++專案，只支援 SxS 備份和 Web 專案，只支援複製備份，project factory 必須交涉的升級策略。

解決方案會查詢每個專案 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>。 然後它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>看看通用專案檔是否需要升級，並判斷支援的升級策略。 **升級精靈**接著叫用。

使用者完成精靈之後<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>執行實際升級每個專案 factory 上呼叫。 若要簡化備份，提供 IVsProjectUpgradeViaFactory 方法<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服務記錄檔的升級程序的詳細資料。 此服務無法快取。

更新所有相關的通用檔案之後, 每個專案的處理站可以具現化專案。 專案的實作必須支援<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>然後呼叫方法來升級所有相關的專案項目。

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法不提供 SVsUpgradeLogger 服務。 這項服務，可由呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>。

## <a name="best-practices"></a>最佳作法

使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>來檢查是否可以編輯檔案，再加以編輯，以及可以將它儲存在儲存它之前的服務。 這可協助您的備份和升級的實作會處理原始檔控制下的專案檔案、 檔案為權限不足，依此類推。

使用<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>服務備份的所有階段期間，並升級成功或失敗的升級程序提供相關資訊。

如需有關備份和升級專案的詳細資訊，請參閱註解 IVsProjectUpgrade vsshell2.idl 中。

## <a name="upgrading-custom-projects"></a> 升級自訂專案

若您變更保存於產品不同 Visual Studio 版本間的專案檔資訊，則需要支援將舊版專案檔升級為新版。 若要支援升級，可讓您參與**Visual Studio 轉換精靈**，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面。 此介面包含僅適用於複本升級的機制。 專案升級會在解決方案開啟時發生。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面應由 Project Factory 實作，或至少從 Project Factory 取得。

使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面的舊機制仍受支援，但就概念而言，則是在專案開啟時升級專案系統。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>介面會因此呼叫 Visual Studio 環境即使<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>介面已呼叫或實作。 此方法可讓您使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 只實作升級的複本與專案部分，並委派 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面就地完成其餘的工作 (可能在新的位置)。

實作範例<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，請參閱 < [VSSDK 範例](https://aka.ms/vs2015sdksamples)。

下列情節會伴隨專案升級發生：

- 若檔案是專案無法支援的較新格式，則專案必需傳回錯誤以說明此狀況。 這是假設您的產品較舊的版本，包含用以檢查版本程式碼。

- 若在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法中指定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> 旗標，會在專案開啟前以就地升級的方式實作升級。

- 若在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法中指定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> 旗標，會以複本升級的方式實作升級。

- 若在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼叫中指定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 旗標，環境則會在專案開啟後提示使用者，以就地升級方式來升級專案檔。 例如，環境會在使用者開啟舊版解決方案時，提示使用者進行升級。

- 若未在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼叫中指定 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 旗標，則您必須提示使用者升級專案檔。

     下列為升級提示訊息的範例。

     「專案 '%1' 是由舊版 Visual Studio 建立。 若您使用此版本的 Visual Studio 開啟專案，可能無法再使用舊版 Visual Studio 加以開啟。 仍要繼續開啟此專案嗎？」

### <a name="to-implement-ivsprojectupgradeviafactory"></a>實作 IVsProjectUpgradeViaFactory

1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面的方法 (尤其是您 Project Factory 實作中的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法)，或讓實作可從您的 Project Factory 實作加以呼叫。

2. 若您想在解決方案開啟時執行就地升級，請提供旗標 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> 作為您 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 實作中的 `VSPUVF_FLAGS` 參數。

3. 若您想在解決方案開啟時執行就地升級，請提供旗標 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> 作為您 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 實作中的 `VSPUVF_FLAGS` 參數。

4. 若是使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 的步驟 2 與 3 (實際的檔案升級步驟)，可依下方＜實作 `IVsProjectUpgade`＞章節所述加以實作，也可將實際的檔案升級委派給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。

5. 使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> 的方法，為 [Visual Studio 移轉精靈] 的使用者張貼升級相關訊息。

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> 介面的用途是實作任何需要在專案升級時發生的檔案升級種類。 此介面並非從 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 呼叫，但會用作升級專案系統內檔案的機制，而主要專案系統可能不會直接察覺到。 比方說，若處理編譯器相關檔案和內容的開發小組與處理其餘專案系統的開發小組不同，就會發生此狀況。

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade 實作

如果您的專案系統會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，它不能參與**Visual Studio 轉換精靈**。 不過，即使您實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面，仍可將檔案升級委派給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 實作。

#### <a name="to-implement-ivsprojectupgrade"></a>實作 IVsProjectUpgrade

1. 當使用者嘗試開啟專案時，環境會在專案開啟後、使用者可對專案進行任何動作前，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 方法 若已提示使用者升級解決方案，則會將 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 旗標傳入 `grfUpgradeFlags` 參數。 如果使用者直接開啟專案，這類可藉由使用**加入現有專案**命令，然後在<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>旗標不會傳遞，且專案需提示使用者進行升級。

2. 為了回應 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼叫，專案必須評估專案檔是否已升級。 若專案不需要將專案類型升級至新版，則可以只傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 旗標。

3. 若專案需要將專案類型升級至新版，則必須判斷是否可以透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法並傳入 `rgfQueryEdit` 參數的 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 值來修改專案檔。 專案接著需執行下列動作：

    - 若 `pfEditCanceled` 參數中傳回的 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>，即表示專案檔可寫入，所以可繼續更新。

    - 若 `pfEditCanceled` 參數中傳回的 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>，且 `VSQueryEditResult` 值有 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> 位元集，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 會因為使用者必須自行解決權限問題，而必需傳回失敗。 專案接著應執行下列動作：

         向使用者回報錯誤，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>，並傳回<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>錯誤碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。

    - 若 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>，且 `VSQueryEditResultFlags` 值有 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> 位元集，則應透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 簽出專案檔(<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>、...)。

4. 若對專案檔的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 呼叫導致檔案簽出，並擷取到最新版本，則會先將專案卸載再將其重新載入。 一旦建立專案的另一個執行個體，就會再次呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 方法。 在第二次呼叫時，專案檔即可寫入磁碟。建議專案使用 .OLD 副檔名以先前格式儲存專案檔複本，變更其必要升級，然後以新格式儲存專案檔。 同樣地，若升級程序的任一部分失敗，此方法必須傳回 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> 以表示失敗。 這會導致專案從方案總管卸載。

     請務必了解在對 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法 (指定 ReportOnly 的值) 的呼叫傳回 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> 與 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> 旗標的案例中，該環境發生的完整程序。

5. 使用者嘗試開啟專案檔。

6. 環境呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 實作。

7. 若 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 傳回 `true`，則環境會呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 實作。

8. 環境呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> 實作，以開啟檔案並將專案物件初始化，例如 Project1。

9. 環境呼叫您的 `IVsProjectUpgrade::UpgradeProject` 實作，以判斷是否需要升級專案檔。

10. 您呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>，並傳入 `rgfQueryEdit` 參數的 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> 值。

11. 環境為 `VSQueryEditResult` 傳回 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>，且 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> 位元設定於 `VSQueryEditResultFlags`。

12. 您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 實作呼叫 `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>、<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>)。

此呼叫可能導致您的專案檔新複本簽出、擷取到最新版本，且需要重新載入您的專案檔。 此時會發生下列兩種情況之一：

- 若您處理自己的專案重新載入，則環境會呼叫您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) 實作。 當您收到此呼叫時，請重新載入專案的第一個執行個體 (Project1)，並繼續升級專案檔。 若您為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) 傳回 `true`，環境便知道您會處理自己的專案重新載入。

- 若您未處理自己的專案重新載入，則為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) 傳回 `false`。 在此情況下之前, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>（QEF_ForceEdit_NoPrompting、 QEF_DisallowInMemoryEdits） 傳回時，環境就會建立另一個您的專案，例如 Project2 的新執行個體，如下所示：

    1. 環境對您的第一個專案物件 (Project1) 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>，讓此物件處於非使用中狀態。

    2. 環境呼叫您的 `IVsProjectFactory::CreateProject` 實作，以建立您的專案的第二個執行個體 (Project2)。

    3. 環境呼叫您的 `IPersistFileFormat::Load` 實作，以開啟檔案並將第二個專案物件 (Project2) 初始化。

    4. 環境第二次呼叫 `IVsProjectUpgrade::UpgradeProject` ，以判斷是否應升級專案物件。 不過，此呼叫會在專案新的第二個執行個體 (Project2) 執行。 此為在解決方案中開啟的專案。

        > [!NOTE]
        > 您的第一個專案執行個體 (Project1) 處於非使用中狀態，因此必須從 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 實作的第一個呼叫傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK>。

    5. 您呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>，並傳入 `rgfQueryEdit` 參數的 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> 值。

    6. 環境傳回 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>，並因為專案檔可寫入，所以可繼續更新。

若您無法升級，請從 `IVsProjectUpgrade::UpgradeProject` 傳回 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>。 若不需要升級或您選擇不升級，請將 `IVsProjectUpgrade::UpgradeProject` 呼叫視為無作業。 若您傳回 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>，預留位置節點就會加入專案的解決方案中。

## <a name="upgrading-project-items"></a>升級專案項目

如果您新增或管理您不會實作的專案系統內的項目時，您可能需要參與專案的升級程序。 Crystal Reports 是可以加入至專案系統的項目範例。

一般而言，專案項目實作者想要運用已經完全具現化和升級的專案，因為他們需要知道哪些參考的專案還有哪些其他專案屬性有進行升級的決策。

### <a name="to-get-the-project-upgrade-notification"></a>若要取得專案的升級通知

1. 設定<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>旗標 （定義於 vsshell80.idl） 在您的專案項目實作中。 Visual Studio shell 可讓您判斷專案系統正在升級時，就會自動載入您的專案項目 VSPackage。

2. 宣布<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>透過介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>方法。

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>之後的專案系統實作完成升級作業，並建立新的升級的專案，就會引發介面。 此案例中，根據<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>介面之後引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>，則<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>，或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>方法。

### <a name="to-upgrade-the-project-item-files"></a>若要升級專案項目檔

1. 您必須仔細管理檔案的備份程序，專案項目實作中。 這特別適用於並排顯示備份，其中`fUpgradeFlag`的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法會設定為<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>、 側邊的檔案被指定為".old"沿著放置已經備份的檔案。 當專案已升級的系統時間比舊的備份的檔案指定為過時。 此外，它們可能會覆寫除非您採取特定步驟，以避免這個問題。

2. 在您的專案項目取得的專案升級時，通知**Visual Studio 轉換精靈**仍會顯示。 因此，您應該使用的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>介面，以提供精靈使用者介面升級的訊息。

## <a name="see-also"></a>另請參閱

- [專案](../../extensibility/internals/projects.md)