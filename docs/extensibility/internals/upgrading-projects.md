---
title: 升級專案 |微軟文檔
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9170532746dfc61cdec6636fb669676a94535de1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303229"
---
# <a name="upgrading-projects"></a>升級專案

對專案模型的更改從 Visual Studio 的一個版本更改為下一個版本可能需要升級專案和解決方案，以便它們可以在較新版本上運行。 提供[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]可用於在您自己的專案中實現升級支援的介面。

## <a name="upgrade-strategies"></a>升級策略

要支援升級，專案系統實施必須定義並實施升級策略。 在確定策略時，您可以選擇支援並行 （SxS） 備份、複本備份或兩者。

- SxS 備份意味著專案僅複製需要升級的檔，添加適當的檔案名尾碼，例如".old"。

- 複本備份意味著專案將所有專案項複製到使用者提供的備份位置。 然後升級原始專案位置的相關檔。

## <a name="how-upgrade-works"></a>升級的工作原理

在較新版本的 Visual Studio 中創建的解決方案時，IDE 會檢查解決方案檔以確定是否需要升級。 如果需要升級，將自動啟動**升級嚮導**以引導使用者完成升級過程。

當解決方案需要升級時，它會查詢每個專案工廠的升級策略。 該策略確定專案工廠是支援複本備份還是 SxS 備份。 資訊將發送到**升級嚮導**，該嚮導收集備份所需的資訊，並將適用的選項呈現給使用者。

### <a name="multi-project-solutions"></a>多專案解決方案

如果解決方案包含多個專案，並且升級策略不同，例如當僅支援 SxS 備份C++專案和僅支援複本備份的 Web 專案時，專案工廠必須協商升級策略。

解決方案查詢每個專案工廠<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>。 然後，它會<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>調用以查看全域專案檔案是否需要升級並確定支援的升級策略。 然後調用**升級嚮導**。

使用者完成嚮導後，<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>在每個專案工廠調用執行實際升級。 為了便於備份，IVsProjectUpgradeViaFactory 方法提供服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>來記錄升級過程的詳細資訊。 無法緩存此服務。

更新所有相關通用檔案後，每個專案工廠可以選擇具現化專案。 專案實施必須支援<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>。 然後<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>調用 該方法以升級所有相關專案項。

> [!NOTE]
> 該方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>不提供 SV 升級記錄器服務。 此服務可以通過調用<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>獲得。

## <a name="best-practices"></a>最佳做法

使用該服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>檢查是否可以在編輯檔之前對其進行編輯，並且可以在保存檔之前保存它。 這將有助於備份和升級實現在原始程式碼管理下處理專案檔案、許可權不足的檔等。

在<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>備份和升級的所有階段使用該服務，提供有關升級過程成功或失敗的資訊。

有關備份和升級專案的詳細資訊，請參閱 vsshell2.idl 中的 IVProjectUpgrade 注釋。

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>升級自訂專案

若您變更保存於產品不同 Visual Studio 版本間的專案檔資訊，則需要支援將舊版專案檔升級為新版。 要支援升級，允許您參與**視覺化工作室轉換向導**，實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>該介面。 此介面包含僅適用於複本升級的機制。 專案升級會在解決方案開啟時發生。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面應由 Project Factory 實作，或至少從 Project Factory 取得。

使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面的舊機制仍受支援，但就概念而言，則是在專案開啟時升級專案系統。 因此<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，即使調用或實現了該介面，Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Studio 環境也會調用該介面。 此方法可讓您使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 只實作升級的複本與專案部分，並委派 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 介面就地完成其餘的工作 (可能在新的位置)。

有關 的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>實現示例，請參閱[VSSDK 示例](https://github.com/Microsoft/VSSDK-Extensibility-Samples)。

下列情節會伴隨專案升級發生：

- 若檔案是專案無法支援的較新格式，則專案必需傳回錯誤以說明此狀況。 這假定產品的舊版本包含用於檢查版本的代碼。

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

如果專案系統僅實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>，則無法參與**視覺化工作室轉換向導**。 不過，即使您實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 介面，仍可將檔案升級委派給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 實作。

#### <a name="to-implement-ivsprojectupgrade"></a>實作 IVsProjectUpgrade

1. 當使用者嘗試開啟專案時，環境會在專案開啟後、使用者可對專案進行任何動作前，呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 方法 若已提示使用者升級解決方案，則會將 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 旗標傳入 `grfUpgradeFlags` 參數。 如果使用者直接打開專案（例如使用 **"添加現有專案"** 命令），則不會傳遞<xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE>標誌，並且專案需要提示使用者升級。

2. 為了回應 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 呼叫，專案必須評估專案檔是否已升級。 若專案不需要將專案類型升級至新版，則可以只傳回 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 旗標。

3. 若專案需要將專案類型升級至新版，則必須判斷是否可以透過呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 方法並傳入 `rgfQueryEdit` 參數的 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 值來修改專案檔。 專案接著需執行下列動作：

    - 若 `pfEditCanceled` 參數中傳回的 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>，即表示專案檔可寫入，所以可繼續更新。

    - 若 `pfEditCanceled` 參數中傳回的 `VSQueryEditResult` 值為 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>，且 `VSQueryEditResult` 值有 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> 位元集，則 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 會因為使用者必須自行解決權限問題，而必需傳回失敗。 專案接著應執行下列動作：

         通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>並將<xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>錯誤代碼返回給<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>使用者，向使用者報告錯誤。

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

- 若您未處理自己的專案重新載入，則為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) 傳回 `false`。 在這種情況下，在返回（QEF_ForceEdit_NoPrompting、QEF_DisallowInMemoryEdits）之前<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>，環境將創建專案的另一個新實例，例如 Project2，如下所示：

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

如果在未實現的專案系統內添加或管理專案，則可能需要參與專案升級過程。 Crystal 報表是可添加到專案系統的項的示例。

通常，專案項實施者希望利用已完全具現化並升級的專案，因為他們需要知道專案引用是什麼以及哪些其他專案屬性可以做出升級決策。

### <a name="to-get-the-project-upgrade-notification"></a>獲取專案升級通知

1. 在<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading>專案項實現中設置標誌（在 vsshell80.idl 中定義）。 當 Visual Studio 外殼確定專案系統正在升級時，這將導致專案項 VSPackage 自動載入。

2. 通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade><xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>該方法通知介面。

3. 在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>專案系統實現完成其升級操作並創建新的升級專案後，將觸發該介面。 根據方案<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>，介面在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>後觸發 ， 或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>方法。

### <a name="to-upgrade-the-project-item-files"></a>升級專案專案檔案

1. 您必須在專案項實現中仔細管理檔案備份過程。 這尤其適用于並排備份，其中`fUpgradeFlag`<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>方法的參數設置為<xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>，其中已備份的檔沿指定為".old"的側檔放置。 備份的檔早于升級專案時的系統時間，可以指定為過時檔。 此外，除非採取特定步驟來防止這種情況，否則它們可能會被覆蓋。

2. 當專案專案收到專案升級通知時，**仍顯示視覺化工作室轉換向導**。 因此，應使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>介面的方法向嚮導 UI 提供升級消息。

## <a name="see-also"></a>另請參閱

- [專案](../../extensibility/internals/projects.md)
