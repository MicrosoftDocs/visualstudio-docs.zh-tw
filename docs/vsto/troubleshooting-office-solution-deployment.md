---
title: 針對 Office 方案部署進行疑難排解
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
ms.openlocfilehash: dfebb3ce5293e7594827a17b30261403b0f3ae9a
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821304"
---
# <a name="troubleshoot-office-solution-deployment"></a>針對 Office 方案部署進行疑難排解
  本主題包含如何解決部署 Office 解決方案常見問題的相關資訊。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>使用事件檢視器疑難排解 Office 方案
 在安裝或解除安裝 Office 解決方案時，您可以使用 Windows 的事件檢視器查看 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 擷取的錯誤訊息。 您可以使用事件記錄器的這些訊息，解決安裝和部署問題。 如需詳細資訊，請參閱 < [Office 方案的事件記錄](../vsto/event-logging-for-office-solutions.md)。

## <a name="change-the-assembly-name-causes-conflicts"></a>變更組件名稱發生衝突
 如果您變更**組件名稱**中的值**應用程式**頁面**專案設計工具**發佈工具已經部署方案之後，將會修改安裝套件，變成有一個*Setup.exe*檔案和兩個部署資訊清單。 如果您部署兩個資訊清單檔案，就可能發生下列狀況：

- 如果使用者兩個版本都安裝，應用程式就會載入兩個 VSTO 增益集。

- 如果先安裝了 VSTO 增益集才變更組件名稱，使用者永遠都收不到更新。

  若要避免這些狀況，不要變更解決方案的**組件名稱**值之後部署方案。

## <a name="check-for-updates-takes-a-long-time"></a>檢查有更新需要很長的時間
 Visual Studio 2010 Tools for Office runtime 提供系統管理員可用來設定下載資訊清單和解決方案的逾時值的登錄項目。

#### <a name="to-set-the-time-out-value"></a>設定逾時值

1. 在登錄中，瀏覽至下列機碼：

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. 在 **AddInTimeout** 子機碼中，將逾時值設定為毫秒。

     如果沒有 **AddInTimeout** 子機碼，請將其建立為 DWORD。

## <a name="cant-update-or-publish-to-a-network-file-share"></a>無法更新或發佈至網路檔案共用
 網路檔案共用上的 office 解決方案可能會顯示可能造成誤導的訊息在更新期間如果解決方案*Setup.exe*檔案鎖定的處理序中所發行的更新。 訊息內容可能是下列：「 無法將 'setup.exe' 加入至 Web。 Web 中已有檔案 'setup.exe'。」

 為防止檔案鎖定，您可以與使用者共用唯讀。 不過，如果文件位於共用，它們對使用者也會變成唯讀。

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>未安裝 Microsoft Office 的必要條件
 您可以將 .NET Framework、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]和 Office 主要 interop 組件加入安裝套件當做與 Office 解決方案一起部署的必要條件。 如需有關如何安裝主要 interop 組件的資訊，請參閱 <<c0> [ 設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)和[How to:安裝 Office 主要 interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)。

## <a name="publish-using-localhost-can-cause-installation-problems"></a>發行使用 'Localhost' 會導致安裝問題
 當您使用 「<http://localhost>"做為文件層級解決方案的發佈或安裝位置**發行精靈**不會將字串轉換成實際的電腦名稱。 在這種情況下，解決方案必須安裝在開發電腦上。 為使得部署的方案在開發電腦上使用 IIS，所有的 HTTP/HTTPS/FTP 位置請使用完整格式名稱，不要使用 localhost。

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>已載入，而不是更新的組件快取的組件
 當專案輸出路徑位於網路檔案共用時、組件以強式名稱簽署時，以及自訂的組件版本未改變時，Fusion (.NET Framework 組件載入器) 會載入組件的快取複本。 如果您更新的組件符合這些條件，因為已載入了快取的複本，所以下次執行專案時，更新就不會出現。

 您可以設定 Visual Studio，每次執行專案時都讓 Fusion 下載組件。

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>下載組件，不載入快取複本

1. 在功能表列上選擇 **專案**， _ProjectName_**屬性**。

2. 在 [應用程式]  頁面上選擇 [組件資訊]  。

3. 一組修訂編號，第三個欄位中，**組件版本**，以萬用字元 (\*)。 比方說，「 1.0。 * 」。  然後選擇**確定** 按鈕。

   變更組件版本之後，您可以繼續以強式名稱簽署組件，Fusion 會載入最新的自訂版本。

 [!NOTE]
> 開始使用 Visual Studio 2017 時，如果您嘗試使用萬用字元，在組件版本建置錯誤就會發生。  這是因為在組件版本中的萬用字元會中斷 MSBuild 具決定性的功能。 您將會指示要從組件版本中，移除萬用字元，或停用決定性。  若要深入了解具決定性的功能，請參閱：[一般 MSBuild 專案屬性](../msbuild/common-msbuild-project-properties.md)和[自訂您的組建](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>URI 有非 US-ASCII 字元時，安裝失敗
 當您發佈 Office 解決方案到 HTTP/HTTPS/FTP 位置時，路徑不能有不是 US-ASCII 的任何 Unicode 字元。 這種字元會造成安裝程式的不一致行為。 安裝路徑請使用 US-ASCII 字元。

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>當您發行，並在開發電腦上安裝解決方案時，會出現提示，手動解除安裝
 當您建置 Office 解決方案時，建置的版本會自動註冊。 如果先前已在開發電腦發佈和安裝了相同的解決方案，當再次建置、重建或發佈解決方案之後， [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 會偵測到發佈版本和建置版本的安裝路徑不同。 錯誤訊息顯示：「無法安裝自訂，因為目前安裝了其他版本，而且無法從這個位置進行升級。」 每次重建解決方案都會更新登錄機碼。 因此，您必須先解除安裝舊版再發佈、偵錯或執行新的版本。

 若要防止訊息出現，請在開發電腦上建立另一個使用者帳戶測試部署。 或者，您可以先從電腦的已安裝程式清單中解除安裝版本，再發佈、偵錯或重建解決方案。

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>無法攔截的例外狀況或方法找不到錯誤時安裝解決方案
 當您開啟部署資訊清單，會在安裝 Office 解決方案時 ( *.vsto*檔案)，可能會出現在下列情況下的 Office 應用程式、 文件或活頁簿中，錯誤訊息：

- 找不到方法。

- MissingMethodException。

- 無法攔截的例外狀況。

  若要避免這些錯誤訊息，請執行安裝程式安裝解決方案。

  當您安裝解決方案卻沒有執行安裝程式時，安裝程式不會檢查或安裝必要條件。 安裝程式會檢查必要條件的正確版本，並視需要加以安裝。

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>在建置 InstallShield 限量版專案後，資訊清單增益集變更的登錄機的碼
 資訊清單登錄機碼是 VSTO 增益集安裝的一部分，有時候程式的變更 *.vsto*要 *。 dll.manifest*當您建置 InstallShield 限量版專案。

 若要解決這個問題，請在不同的解決方案中建立 InstallShield 限量版專案，或使用 CompanyName.AddinName 當做包含 VSTO 增益集名稱的登錄機碼值。

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Office 方案之 ClickOnce 安裝程式不會安裝主要 interop 組件
 當您執行 ClickOnce 為 Office 解決方案建立的安裝程式時，只有在未安裝任何主要 interop 組件 (PIA) 的情況下，Office PIA 的安裝程式才會執行。

 如果安裝程式不會正確安裝 Pia，來手動安裝執行安裝程式檔案，稱為*o2007pia.msi*從安裝目錄。

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>重新安裝 Office 解決方案會導致引數超出範圍的例外狀況
 當您重新安裝 Office 方案，<xref:System.ArgumentOutOfRangeException>例外狀況可能會出現下列錯誤訊息：指定的引數超出有效值的範圍。

 如果安裝位置的 URL 大小寫不同，就會發生這種情況。 例如，如果您已安裝 Office 解決方案就會出現此錯誤[ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto)第一次，然後使用[ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto)第二次。

 若要防止訊息出現，請在安裝 Office 解決方案時使用相同的大小寫。

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>無法安裝 ClickOnce 解決方案從 web 開啟部署資訊清單
 使用者可以從 Web 開啟部署資訊清單，藉以安裝 Office 解決方案。 不過，某些安裝網際網路資訊服務 (IIS) 會封鎖 *.vsto*副檔名。 您使用它來部署 Office 方案之前，您必須在 IIS 中定義 MIME 類型。

 如需有關如何在 IIS 7 中定義 MIME 類型的資訊，請參閱 <<c0> [ 加入 MIME 類型 (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx)。

 將副檔名設為 **.vsto** ，MIME 類型設為 **application/x-ms-vsto**。

## <a name="see-also"></a>另請參閱

- [針對 ClickOnce 部署進行疑難排解](../deployment/troubleshooting-clickonce-deployments.md)
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
