---
title: 讓自訂專案成為版本感知 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 0b29728cffc962b5d09a5adc45f8cac2093b020a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825677"
---
# <a name="making-custom-projects-version-aware"></a>讓自訂專案成為版本感知
在自訂專案系統中，您可以允許在多個版本的 Visual Studio 中載入該類型的專案。 您也可以防止舊版本的 Visual Studio 中載入該類型的專案。 您也可以讓該專案能夠向較新版本識別自己，以防專案需要修復、轉換或取代。  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>允許在多個版本中載入專案  
 您可以修改在 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 或更新版本中所建立的大部分專案，以便在多個版本中運作。  
  
 在載入專案之前，Visual Studio 會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> 方法，以判斷是否可以升級專案。 如果可以升級專案，`UpgradeProject_CheckOnly` 方法會設定旗標，導致稍後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 方法來升級專案。 無法升級不相容的專案，因此 `UpgradeProject_CheckOnly` 必須先檢查專案相容性，如前一節中所述。  
  
 您身為專案系統的作者，實作 `UpgradeProject_CheckOnly` (從 `IVsProjectUpgradeViaFactory4` 介面) 為專案系統的使用者提供升級檢查。 當使用者開啟專案時，會呼叫這個方法來判斷專案是否必須在載入之前修復。 可能需要升級的情況列舉在 `VSPUVF_REPAIRFLAGS`中，其中包括下列可能性：  
  
1. `SPUVF_PROJECT_NOREPAIR`: 不需要修復。  
  
2. `VSPUVF_PROJECT_SAFEREPAIR`: 使專案與舊版相容，而沒有您可能在舊版產品中遇到的問題。  
  
3. `VSPUVF_PROJECT_UNSAFEREPAIR`: 使專案與舊版相容，但會有一些風險，可能會遇到您曾在舊版產品中遇到的問題。 例如，專案如果相依於不同的 SDK 版本，它將不相容。  
  
4. `VSPUVF_PROJECT_ONEWAYUPGRADE` 使專案與較舊版本不相容。  
  
5. `VSPUVF_PROJECT_INCOMPATIBLE`: 表示目前的版本不支援此專案。  
  
6. `VSPUVF_PROJECT_DEPRECATED`: 表示已不再支援此專案。  
  
> [!NOTE]
> 為了避免混淆，在設定升級旗標時請不要合併它們。 例如，不要建立模稜兩可的升級狀態，例如 `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`。  
  
 專案類別可能會從 `UpgradeProjectFlavor_CheckOnly` 介面實作函式 `IVsProjectFlavorUpgradeViaFactory2` 。 若要讓此函式運作，必須呼叫先前所述的 `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` 實作。 Visual Basic 或 C# 基礎專案系統中已實作此呼叫。 此函式的效果可讓專案類別除了基底專案系統已判斷的升級需求之外，也能判斷專案的升級需求。 相容性對話方塊會顯示最嚴重的兩項需求。  
  
 當 Visual Studio 執行升級檢查時，它會提供記錄器，而非像先前版本的 Visual Studio 一樣提供 NULL 值。 記錄器可讓專案系統和類別提供其他資訊，協助您了解讓舊專案能正確載入所需的變更本質。 我們建議您使用記錄器提供更多的資訊，而不要使用對話方塊。 如需詳細資訊，請參閱本主題稍後的 [The Upgrade Logger](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) 。  
  
 對於 Managed 實作，專案升級介面提供於 Microsoft.VisualStudio.Shell.Interop.11.0.dll Interop 組件中。  
  
 `UpgradeProject` 方法可以判斷它進行的變更是否會阻礙專案從舊版的 Visual Studio 載入。 如果是的話，方法會將專案標記為不相容。 若要了解如何將專案標記為不相容，請參閱本主題前面的 [Marking a Project as Incompatible](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) 。 我們建議，出現此對話方塊後，您藉由直接呼叫方法 `IVsAppCompat.BreakAssetCompatibility` 將專案標記為不相容，而不是先呼叫 `IVsAppCompat.AskForUserConsentToBreakAssetCompat` 方法，因為對話方塊不需要出現兩次。  
  
 以下範例可協助彙總使用者體驗到的相容性。 如果專案是在較早的版本建立，而目前版本判斷需要升級的話，Visual Studio 會顯示對話方塊，向使用者要求進行變更的權限。 如果使用者同意，便會修改專案，然後載入它。 如果方案接著關閉並在較早的版本重新開啟，單向升級的專案將會不相容且不會載入。 如果專案有只需要修復 (而非升級)，則修復後的專案仍會在兩個版本中開啟。  
  
## <a name="marking-a-project-as-incompatible"></a><a name="BKMK_Incompat"></a> 將專案標記為不相容  
 您可以將專案標記為與舊版 Visual Studio 不相容。  例如，假設您建立一個使用 .NET Framework 4.5 功能的專案。 因為無法在 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]建置此專案，您可以將它標記為不相容，以避免該版本嘗試載入它。  
  
 加入不相容功能的元件要負責將專案標記為不相容。 元件必須能夠存取代表相關專案的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 介面。  
  
#### <a name="to-mark-a-project-as-incompatible"></a>將專案標記為不相容  
  
1. 在元件中，從全域服務 SVsSolution 取得 `IVsAppCompat` 介面。  
  
     如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>。  
  
2. 在元件中，呼叫 `IVsAppCompat.AskForUserConsentToBreakAssetCompat`，並傳遞 `IVsHierarchy` 介面的陣列給它，這些介面代表相關的專案。  
  
     此方法具有下列簽章：  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     如果您實作此程式碼，會出現專案相容性對話方塊。 對話方塊會向使用者要求權限，以將所有指定的專案標記為不相容。 如果使用者同意， `AskForUserConsentToBreakAssetCompat` 會傳回 `S_OK`，否則 `AskForUserConsentToBreakAssetCompat` 會傳回 `OLE_E_PROMPTSAVECANCELLED`。  
  
    > [!WARNING]
    > 在最常見的情況下， `IVsHierarchy` 陣列將只包含一個項目。  
  
3. 如果 `AskForUserConsentToBreakAssetCompat` 傳回 `S_OK`，元件會標記或接受中斷相容性的變更。  
  
4. 在您的元件中，為您要標記為不相容的每個專案呼叫 `IVsAppCompat.BreakAssetCompatibility` 方法。 元件可以將參數 `lpszMinimumVersion` 的值設為特定的最小版本，而不需讓 Visual Studio 查閱登錄中的目前版本字串。 這個方法會降低未來根據當時在登錄中的內容，不小心設定較高值的風險。 如果已設定該較高的值，則 Visual Studio 無法開啟專案。  
  
     此方法具有下列簽章：  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     如果元件將 `lpszMinimumVersion` 設為 NULL， `BreakAssetCompatibility` 方法會呼叫 `IVsAppCompat.GetCurrentDesignTimeCompatVersion` 方法，以取得字串，代表 Visual Studio 的目前版本。  
  
     此方法具有下列簽章：  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     然後 BreakAssetCompatibility 方法會呼叫 `IVsHierarchy.SetProperty` 方法，以將根 `VSHPROPID_MinimumDesignTimeCompatVersion` 屬性設為您在上一個步驟中取得之版本字串的值。  
  
     如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>。  
  
> [!IMPORTANT]
> 您必須實作 `VSHPROPID_MinimumDesignTimeCompatVersion` 屬性，來將專案標記為相容或不相容。 比方說，如果專案系統使用 MSBuild 專案檔，請在專案檔加入 `<MinimumVisualStudioVersion>` 建置屬性，且值等於對應的 `VSHPROPID_MinimumDesignTimeCompatVersion` 屬性值。  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>偵測專案是否不相容  
 與 Visual Studio 目前版本不相容的專案必須避免載入。 此外，也不能升級或修復不相容的專案。 因此，必須檢查專案的相容性兩次：第一次是在考慮升級或修復它時，第二次則是在載入它之前。  
  
 若要啟用專案不相容性的偵測，您必須實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 方法。 如果專案不相容， `UpgradeProject_CheckOnly` 必須傳回成功碼 `VS_S_INCOMPATIBLEPROJECT`，且 `CreateProject` 必須傳回錯誤碼 `VS_E_INCOMPATIBLEPROJECT`。 針對指定類別的專案，您必須實作 `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` 而不是 `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`。  
  
 如果專案系統有 Web、Office (VSTO)、Silverlight 或在其上建置的其他專案類型，便會稱為指定類別 (flavored)。 已經實作 `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` 的較舊專案系統，和已經實作 `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` 指定類別的專案系統，會繼續受到支援。 舊版的 `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` 具有下列實作簽章：  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 如果這個方法將 `pUpgradeRequired` 設為 TRUE，並傳回 `S_OK`，結果會視為「升級」，且彷彿方式已將升級旗標設為值 `VSPUVF_PROJECT_ONEWAYUPGRADE`，如本主題稍後所述。 使用此較舊方法支援下列傳回值，但只有在 `pUpgradeRequired` 設為 TRUE 時：  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. 這個傳回值會將 `pUpgradeRequired` 值轉譯為 TRUE，相當於 `VSPUVF_PROJECT_SAFEREPAIR`，如本主題稍後所述。  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. 這個傳回值會將 `pUpgradeRequired` 值轉譯為 TRUE，相當於 `VSPUVF_PROJECT_UNSAFEREPAIR`，如本主題稍後所述。  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. 這個傳回值會將 `pUpgradeRequired` 值轉譯為 TRUE，相當於 `VSPUVF_PROJECT_ONEWAYUPGRADE`，如本主題稍後所述。  
  
   `IVsProjectUpgradeViaFactory4` 和 `IVsProjectFlavorUpgradeViaFactory2` 中的新實作能更精確地指定移轉類型。  
  
> [!NOTE]
> 您可以快取 `UpgradeProject_CheckOnly` 方法的相容性檢查結果，以便也可供後續呼叫 `CreateProject`時使用。  
  
 例如，如果專為 `UpgradeProject_CheckOnly` SP1 專案系統撰寫的 `CreateProject` 和 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 方法會檢查專案檔案，並發現 `<MinimumVisualStudioVersion>` 組建屬性為 "11.0"，則 Visual Studio 2010 SP1 便不會載入專案。 此外， **方案導覽** 會表示專案「不相容」，且不會載入它。  
  
## <a name="the-upgrade-logger"></a><a name="BKMK_UpgradeLogger"></a> 升級記錄器  
 對 `IVsProjectUpgradeViaFactory::UpgradeProject` 的呼叫包含 `IVsUpgradeLogger` 記錄器，專案系統和類別應該使用它來提供詳細的升級追蹤，以進行疑難排解。 如果記錄了警告或錯誤，Visual Studio 會顯示升級報表。  
  
 當您寫入升級記錄器時，請考慮下列指導方針：  
  
- 在所有專案都完成升級後，Visual Studio 會呼叫 Flush。 請不要在您的專案系統中呼叫。  
  
- LogMessage 函式具有下列 ErrorLevel：  
  
  - 0 適用於任何您想要追蹤的資訊。  

  - 1 適用於警告。  

  - 2 適用於錯誤。  

  - 3 適用於報表格式器。 升級您的專案時，記錄單字 “Converted” 一次，且不要將它當地語系化。  
  
- 如果專案不需要任何修復或升級時，則唯有專案系統已在 UpgradeProject_CheckOnly 或 UpgradeProjectFlavor_CheckOnly 方法期間記錄警告或錯誤時，Visual Studio 才會產生記錄檔。
