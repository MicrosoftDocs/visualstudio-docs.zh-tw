---
title: 升級專案 |Microsoft Docs
description: 瞭解 Visual Studio SDK 提供的介面，以在您的專案中執行升級支援。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b399feb80da56ef70b18a1b11b05c7f6cc3795f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883151"
---
# <a name="upgrading-projects"></a>升級專案

從某個 Visual Studio 版本到下一個版本的專案模型變更可能需要升級專案和方案，才能在較新的版本上執行。 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]提供介面，可用來在您自己的專案中執行升級支援。

## <a name="upgrade-strategies"></a>升級策略

若要支援升級，您的專案系統實行必須定義和實行升級策略。 在決定您的策略時，您可以選擇支援並存 (SxS) 備份、複本備份或兩者。

- SxS 備份表示專案只會複製需要就地升級的檔案，並新增適當的檔案名尾碼，例如「.old」。

- 複本備份表示專案會將所有專案專案複製到使用者提供的備份位置。 然後會升級原始專案位置的相關檔案。

## <a name="how-upgrade-works"></a>升級的運作方式

在舊版 Visual Studio 中建立的方案會在較新版本中開啟時，IDE 會檢查方案檔，以判斷是否需要升級方案檔。 如果需要升級，則會自動啟動 **升級嚮導** ，以引導使用者進行升級程式。

當解決方案需要升級時，它會查詢每個專案 factory 的升級策略。 此策略會決定專案 factory 是否支援複本備份或 SxS 備份。 這項資訊會傳送至 [ **升級嚮導]**，以收集備份所需的資訊，並向使用者呈現適用的選項。

### <a name="multi-project-solutions"></a>多專案方案

如果解決方案包含多個專案，而且升級策略不同，例如，當僅支援 SxS 備份的 c + + 專案，以及僅支援複本備份的 Web 專案時，專案處理站必須協調升級策略。

方案會查詢的每個專案 factory <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 。 然後，它會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> 以查看全域專案檔是否需要升級，以及判斷支援的升級策略。 接著會叫用 **Upgrade Wizard** 。

當使用者完成嚮導之後， <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 會在每個專案 factory 上呼叫，以執行實際的升級。 為了加速備份，IVsProjectUpgradeViaFactory 方法會提供 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 服務來記錄升級程式的詳細資料。 這是無法快取的服務。

更新所有相關的全域檔案之後，每個專案 factory 都可以選擇具現化專案。 專案執行必須支援 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>接著會呼叫方法來升級所有相關的專案專案。

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法不提供 SVsUpgradeLogger 服務。 這項服務可以藉由呼叫來取得 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 。

## <a name="best-practices"></a>最佳做法

您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 服務來檢查是否可以編輯檔案，然後儲存檔案。 這可協助您的備份和升級程式處理原始檔控制下的專案檔案、許可權不足的檔案等等。

在 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 備份和升級的所有階段中使用服務，以提供升級程式成功或失敗的相關資訊。

如需有關備份和升級專案的詳細資訊，請參閱 vsshell2 中的 IVsProjectUpgrade 批註。

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a> 升級自訂專案

若您變更保存於產品不同 Visual Studio 版本間的專案檔資訊，則需要支援將舊版專案檔升級為新版。 若要支援可讓您參與 **Visual Studio 轉換向導** 的升級，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面。 此介面包含僅適用於複本升級的機制。 專案升級會在解決方案開啟時發生。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面應由 Project Factory 實作，或至少從 Project Factory 取得。

使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面的舊機制仍受支援，但就概念而言，則是在專案開啟時升級專案系統。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>因此，即使 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 呼叫或執行介面，Visual Studio 環境仍會呼叫介面。 此方法可讓您使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 只實作升級的複本與專案部分，並委派 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面就地完成其餘的工作 (可能在新的位置)。

如需的範例執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> ，請參閱 [VSSDK 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

下列情節會伴隨專案升級發生：

- 若檔案是專案無法支援的較新格式，則專案必需傳回錯誤以說明此狀況。 這會假設您的產品較舊版本包含檢查版本的程式碼。

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

如果您的專案系統 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 只執行，它無法參與 **Visual Studio 轉換向導**。 不過，即使您實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面，仍可將檔案升級委派給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 實作。

#### <a name="to-implement-ivsprojectupgrade"></a>實作 IVsProjectUpgrade

1. 當使用者嘗試開啟專案時，環境會在專案開啟後、使用者可對專案進行任何動作前，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 方法 若已提示使用者升級解決方案，則會將 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 旗標傳入 `grfUpgradeFlags` 參數。 如果使用者直接開啟專案，例如使用 [ **加入現有專案** ] 命令，則 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 不會傳遞旗標，且專案需要提示使用者進行升級。

2. 為了回應 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼叫，專案必須評估專案檔是否已升級。 若專案不需要將專案類型升級至新版，則可以只傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 旗標。

3. 若專案需要將專案類型升級至新版，則必須判斷是否可以透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法並傳入 `rgfQueryEdit` 參數的 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 值來修改專案檔。 專案接著需執行下列動作：

    - 若 `pfEditCanceled` 參數中傳回的 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>，即表示專案檔可寫入，所以可繼續更新。

    - 若 `pfEditCanceled` 參數中傳回的 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>，且 `VSQueryEditResult` 值有 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> 位元集，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 會因為使用者必須自行解決權限問題，而必需傳回失敗。 專案接著應執行下列動作：

         藉由呼叫並將錯誤碼傳回給使用者，向使用者 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 回報錯誤 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 。

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

- 若您未處理自己的專案重新載入，則為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) 傳回 `false`。 在此情況下， <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> QEF_DisallowInMemoryEdits) 傳回 (QEF_ForceEdit_NoPrompting 之前，環境會為您的專案建立另一個新的實例，例如 Project2，如下所示：

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

如果您在未執行的專案系統中加入或管理專案，您可能需要參與專案升級程式。 Crystal Reports 是可以加入至專案系統的專案範例。

專案專案實施者通常會想要利用已經完全具現化和升級的專案，因為它們需要知道專案參考的專案，以及要進行升級決策的其他專案屬性。

### <a name="to-get-the-project-upgrade-notification"></a>取得專案升級通知

1. <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>在專案專案執行的 vsshell80) 中，將旗標 (定義。 當 Visual Studio shell 判斷專案系統正在進行升級時，這會導致您的專案專案 VSPackage 自動載入。

2. 透過方法來建議 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 介面 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> 。

3. 此 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 介面會在專案系統執行完成其升級作業之後引發，而且會建立新的升級專案。 視案例而定， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 介面會在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> 、或方法之後引發 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> 。

### <a name="to-upgrade-the-project-item-files"></a>升級專案專案檔

1. 您必須在專案專案執行中小心地管理檔案備份程式。 這特別適用于並存備份，其中 `fUpgradeFlag` 方法的參數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 會設定為 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> ，而已備份的檔案會放置在指定為 ".old" 的端檔案中。 已備份的檔案若早于升級專案的系統時間，可以指定為過時。 此外，除非您採取特定的步驟來防止這種情況，否則可能會覆寫它們。

2. 當您的專案專案收到專案升級的通知時，仍會顯示 **Visual Studio 轉換向導** 。 因此，您應該使用介面的方法，將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> 升級訊息提供給嚮導 UI。

## <a name="see-also"></a>另請參閱

- [專案](../../extensibility/internals/projects.md)
