---
title: 排除 Office 解決方案部署的故障
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de036ce9b0b566a6028b0ccfe45cfe5f2ac49da9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444930"
---
# <a name="troubleshoot-office-solution-deployment"></a>排除 Office 解決方案部署的故障
  本主題包含如何解決部署 Office 解決方案常見問題的相關資訊。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>使用事件檢視器對 Office 解決方案進行故障排除
 在安裝或解除安裝 Office 解決方案時，您可以使用 Windows 的事件檢視器查看 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 擷取的錯誤訊息。 您可以使用事件記錄器的這些訊息，解決安裝和部署問題。 有關詳細資訊,請參閱[Office 解決方案的事件紀錄記錄](../vsto/event-logging-for-office-solutions.md)。

## <a name="change-the-assembly-name-causes-conflicts"></a>變更程式集名稱會導致衝突
 如果在已部署解決方案後更改**專案設計器****應用程式**頁中的**程式集名稱**值,則發布工具將修改安裝程式包,以具有一個*安裝程式.exe*檔和兩個部署清單。 如果您部署兩個資訊清單檔案，就可能發生下列狀況：

- 如果使用者兩個版本都安裝，應用程式就會載入兩個 VSTO 增益集。

- 如果先安裝了 VSTO 增益集才變更組件名稱，使用者永遠都收不到更新。

  為了避免這些情況,在部署解決方案後,不要更改解決方案的**程式集名稱**值。

## <a name="check-for-updates-takes-a-long-time"></a>檢查更新需要很長時間
 Visual Studio 2010 Office 運行時工具提供了一個註冊表項,管理員可以使用該註冊表項設置下載清單和解決方案的超時值。

#### <a name="to-set-the-time-out-value"></a>設定逾時值

1. 在登錄中，瀏覽至下列機碼：

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. 在 **AddInTimeout** 子機碼中，將逾時值設定為毫秒。

     如果沒有 **AddInTimeout** 子機碼，請將其建立為 DWORD。

## <a name="cant-update-or-publish-to-a-network-file-share"></a>無法更新或發布到網路檔案分享
 如果解決方案的*安裝程式.exe*檔在發佈更新時鎖定在進程中,則網路檔共用上的 Office 解決方案可能會在更新期間顯示誤導性訊息。 訊息內容可能是：「無法將 'setup.exe' 加入 Web。 Web 中已有檔案 'setup.exe'。」

 為防止檔案鎖定，您可以與使用者共用唯讀。 不過，如果文件位於共用，它們對使用者也會變成唯讀。

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>未安裝 Microsoft Office 的先決條件
 您可以將 .NET Framework、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]和 Office 主要 interop 組件加入安裝套件當做與 Office 解決方案一起部署的必要條件。 有關如何安裝主互操作程式集的資訊,請參閱[設定電腦以開發 Office 解決方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)以及如何[:安裝 Office 主互通程式集](../vsto/how-to-install-office-primary-interop-assemblies.md)。

## <a name="publish-using-localhost-can-cause-installation-problems"></a>使用本地主機進行發佈可能會導致安裝問題
 當您用作`http://localhost`文件級解決方案的發表或安裝位置時,**發布精靈**不會將字串轉換為實際電腦名稱。 在這種情況下，解決方案必須安裝在開發電腦上。 為使得部署的方案在開發電腦上使用 IIS，所有的 HTTP/HTTPS/FTP 位置請使用完整格式名稱，不要使用 localhost。

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>載入快取的程式集,而不是更新的程式集
 當專案輸出路徑位於網路檔案共用時、組件以強式名稱簽署時，以及自訂的組件版本未改變時，Fusion (.NET Framework 組件載入器) 會載入組件的快取複本。 如果您更新的組件符合這些條件，因為已載入了快取的複本，所以下次執行專案時，更新就不會出現。

 您可以設定 Visual Studio，每次執行專案時都讓 Fusion 下載組件。

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>下載組件，不載入快取複本

1. 在選單列上,選擇 **「 項目**」 。_ProjectName_**Properties**

2. 在 [應用程式] **** 頁面上選擇 [組件資訊] ****。

3. 將**程式集版本的**修訂號(第三個字段)設置為通配符\*()。 例如,"1.0.*"。  然後選擇「**確定」** 按鈕。

   變更組件版本之後，您可以繼續以強式名稱簽署組件，Fusion 會載入最新的自訂版本。

 [!NOTE]
> 從 Visual Studio 2017 開始,如果您在程式集版本中嘗試使用通配符,則會出現生成錯誤。  這是因為程式集版本中的通配符將破壞 MSBuild 確定性功能。 將指示您從程式集版本中刪除通配符,或禁用確定性。  要瞭解有關確定性功能的更多詳細資訊,請參閱:[通用 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)和[自訂生成](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>當 URI 具有非美國 ASCII 字元時,安裝失敗
 當您發佈 Office 解決方案到 HTTP/HTTPS/FTP 位置時，路徑不能有不是 US-ASCII 的任何 Unicode 字元。 這種字元會造成安裝程式的不一致行為。 安裝路徑請使用 US-ASCII 字元。

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>在開發電腦上發表並安裝解決方案時,將顯示手動卸載的提示
 當您建置 Office 解決方案時，建置的版本會自動註冊。 如果先前已在開發電腦發佈和安裝了相同的解決方案，當再次建置、重建或發佈解決方案之後， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會偵測到發佈版本和建置版本的安裝路徑不同。 錯誤訊息顯示：「無法安裝自訂，因為目前安裝了其他版本，而且無法從這個位置進行升級。」 每次重建解決方案都會更新登錄機碼。 因此，您必須先解除安裝舊版再發佈、偵錯或執行新的版本。

 若要防止訊息出現，請在開發電腦上建立另一個使用者帳戶測試部署。 或者，您可以先從電腦的已安裝程式清單中解除安裝版本，再發佈、偵錯或重建解決方案。

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>安裝解決方案時未捕捉的例外或方法未發現錯誤
 當您透過開啟部署清單 *(.vsto*檔案)、Office 應用程式、文件或工作簿來安裝 Office 解決方案時,可能會出現以下條件的錯誤訊息:

- 找不到方法。

- MissingMethodException。

- 無法攔截的例外狀況。

  若要避免這些錯誤訊息，請執行安裝程式安裝解決方案。

  當您安裝解決方案卻沒有執行安裝程式時，安裝程式不會檢查或安裝必要條件。 安裝程式會檢查必要條件的正確版本，並視需要加以安裝。

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>在安裝盾有限版項目構建後,載入項的清單註冊表項更改
 在構建安裝Shield有限版專案時,作為 VSTO 外接程式一部分的清單註冊表項有時會從 *.vsto*更改為 *.dll.manifest。*

 若要解決這個問題，請在不同的解決方案中建立 InstallShield 限量版專案，或使用 CompanyName.AddinName 當做包含 VSTO 增益集名稱的登錄機碼值。

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Office 解決方案的 ClickOnce 安裝程式不會安裝主互通程式集
 當您執行 ClickOnce 為 Office 解決方案建立的安裝程式時，只有在未安裝任何主要 interop 組件 (PIA) 的情況下，Office PIA 的安裝程式才會執行。

 如果安裝程式未正確安裝 PIA,請透過執行安裝目錄中名為*o2007pia.msi*的安裝程式檔手動安裝它們。

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>重新安裝 Office 解決方案會導致參數範圍外例外
 當您重新安裝 Office 解決方案時，可能會出現 <xref:System.ArgumentOutOfRangeException> 例外狀況及下列錯誤訊息：指定的引數超出有效值的範圍。

 如果安裝位置的 URL 大小寫不同，就會發生這種情況。 例如,如果您從第一次安裝 Office`http://fabrikam.com/ExcelSolution.vsto`解決方案 ,然後第`http://fabrikam.com/excelsolution.vsto`二次使用 ,則會出現此錯誤。

 若要防止訊息出現，請在安裝 Office 解決方案時使用相同的大小寫。

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>無法透過網頁開啟部署清單來安裝 ClickOnce 解決方案
 使用者可以從 Web 開啟部署資訊清單，藉以安裝 Office 解決方案。 但是,某些 Internet 資訊服務 (IIS) 安裝會阻止 *.vsto*檔案名副檔名。 在使用 IIS 部署 Office 解決方案之前,必須在 IIS 中定義 MIME 類型。

 有關如何在IIS 7中定義MIME類型的資訊,請參閱[添加MIME類型 (IIS7)。](https://technet.microsoft.com/library/cc725608(WS.10).aspx)

 將副檔名設為 **.vsto** ，MIME 類型設為 **application/x-ms-vsto**。

## <a name="see-also"></a>另請參閱

- [針對 ClickOnce 部署進行疑難排解](../deployment/troubleshooting-clickonce-deployments.md)
- [部署 Office 解決方案](../vsto/deploying-an-office-solution.md)
