---
title: 使用命令列參數安裝 Visual Studio 2015 |Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3fe0233f08f33535be4b02cc06c29d919d75169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180260"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>使用命令列參數來安裝 Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如需 Visual Studio 的最新檔，請參閱 [使用命令列參數安裝 Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)。

當您從命令提示字元安裝 Visual Studio 2015 時，可以使用下列命令列參數 (parameter，也稱為 switch)。

> [!NOTE]
> 請確定您使用的是實際的安裝程式，而不是啟動載入器檔案。 例如，請確定您使用， **`vs_enterprise.exe`** 而不是*GUID*vs_enterprise_ 的 mmc.exe。 您可以從 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)下載安裝程式。

## <a name="list-of-command-line-parameters"></a>命令列參數清單

Visual Studio 命令列參數不區分大小寫。

|參數|描述|
|---------------|-----------------|
|**/?**<br /><br /> **/help**<br /><br /> **/h**|顯示命令列參數。|
|**/AddRemoveFeatures**|指定要加入哪些功能或從已安裝的產品移除哪些功能。|
|**/AdminFile** *AdminDeployment.xml*|使用您指定用於管理安裝的資料檔案，安裝 Visual Studio。|
|**/ChainingPackage** *BundleName*|指定哪一個搭售方案要鏈結這個搭售方案。 這也可用來指定客戶經驗改進的群組。|
|**/CreateAdminFile \<filename>**|指定要搭配 /AdminFile 使用之控制檔的建立位置|
|**/CustomInstallPath** *InstallationDirectory*|將所有可重定目標的封裝安裝在您指定的目錄中。|
|**/ForceRestart**|一律在安裝之後重新啟動電腦。|
|**/full**|安裝所有產品功能。|
|**/InstallSelectableItems \<item name 1> [; \<item name 2> ]**|樹狀結構項目的選取清單，確認安裝精靈的選取畫面。|
|**/l**<br /><br /> **/Log** *檔案名*|指定記錄檔的位置。|
|**/layout** *Directory*|將安裝媒體上的檔案複製到您指定的目錄。|
|**/NoCacheOnlyMode**|防止封裝快取的預先填入。|
|**/NoRefresh**|不要檢查本產品較新版本所必需或建議的更新版本。|
|**/norestart**|在安裝期間或之後，防止安裝應用程式重新啟動電腦。 如需尋找傳回碼，請參閱 [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)的＜傳回碼＞一節。|
|**/noweb**|防止從網際網路進行安裝。|
|**/OverrideFeedUri \<path to feed file>**|本機的路徑，為描述軟體項目的外部輸入。|
|**/ProductKey**<br /><br /> *ProductKey*|設定不包含虛線和不超過 25 個字元的自訂產品金鑰。|
|**/PromptRestart**|在重新啟動電腦之前提示使用者。|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|隱藏安裝應用程式的使用者介面 (UI)。 如果 Visual Studio 已安裝，而且除了這個參數之外，您沒有指定其他參數，則安裝應用程式會在維護模式下執行。|
|**/qb**<br /><br /> **/passive**|顯示進度，但不等候使用者輸入。|
|**/repair**|修復 Visual Studio。|
|**/SuppressRefreshPrompt**|不要在安裝精靈中顯示可用更新對話方塊，如此一來，安裝精靈將會自動接受任何必要或建議的更新版本。|
|**u**<br /><br /> **/Uninstall**|解除安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。|
|**/Uninstall/Force**<br /><br /> **/u /force**|解除安裝 Visual Studio 以及與其他產品共用的所有功能。 **警告：**  如果您使用此參數，則安裝在同一部電腦上的其他產品可能會停止正常運作。|

## <a name="see-also"></a>另請參閱

- [Visual Studio 系統管理員指南](../install/visual-studio-administrator-guide.md)