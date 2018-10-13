---
title: 管理並排顯示檔案的關聯 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55a3649385ca8fc840bed8bd28555bcb17f6ac91
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253977"
---
# <a name="managing-side-by-side-file-associations"></a>管理並存的檔案關聯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果 VSPackage 提供的檔案關聯，您必須決定如何處理在其中的並排顯示安裝特定版本的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]應該叫用它來開啟檔案。 不相容的檔案格式複合問題。  
  
 使用者期望的產品，為相容於舊版本中，使現有的檔案可以載入新版本中，而不會遺失資料的新版本。 在理想情況下，VSPackage 可載入和儲存的舊版檔案格式。 如果不是，則為 true，則您應該提供升級至新版本的 VSPackage 的檔案格式。 這種方法的缺點是舊版本中，無法開啟已升級的檔案。  
  
 若要避免這個問題，您可以在檔案格式不相容時變更延伸模組。 比方說，第 1 版的 VSPackage 可以使用延伸模組、.mypkg10 和 2 可以使用延伸模組的版本.mypkg20。 這項差異會識別開啟特定檔案的 VSPackage。 如果您在與舊的延伸模組相關聯的程式清單中新增較新的 Vspackage，使用者可以用滑鼠右鍵按一下檔案，並選擇在較新的 VSPackage 中開啟它。 此時，VSPackage 可以提供給升級為新格式的檔案或開啟檔案，並維持與舊版 VSPackage 的相容性。  
  
> [!NOTE]
>  您可以結合這些方法。 比方說，您可以藉由載入較舊的檔案提供回溯相容性，並提供升級的檔案格式，當使用者儲存它。  
  
## <a name="facing-the-problem"></a>面對的問題  
 如果您想要使用同一個延伸模組的多個並排顯示 Vspackage，您必須選擇的新版[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]與延伸模組相關聯。 以下是兩個替代方案：  
  
-   開啟檔案中的最新版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]使用者的電腦上安裝。  
  
     在此方法中，您的安裝程式會負責判斷最新版的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]並納入，撰寫的檔案關聯的登錄項目中。 您可以在 Windows Installer 封裝時，包含要設定此屬性，指出最新版的自訂動作[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
    > [!NOTE]
    >  在此情況下，「 最新 」 表示 「 最新支援的版本。 」 這些安裝程式項目將不會自動偵測的後續版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 中的項目[偵測系統需求](../extensibility/internals/detecting-system-requirements.md)然後在[命令，必須是執行安裝後](../extensibility/internals/commands-that-must-be-run-after-installation.md)類似於此處所提供的項目，支援的其他版本所需[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。  
  
     下列資料表中的資料列 CustomAction DEVENV_EXE_LATEST 屬性設定 AppSearch 所設定的屬性，並 RegLocator 資料表所述[命令，必須是執行安裝後](../extensibility/internals/commands-that-must-be-run-after-installation.md)。 InstallExecuteSequence 資料表中的資料列來排程執行順序在早期的自訂動作。 條件資料行進行邏輯工作中的值：  
  
    -   Visual Studio.NET 2002年是最新版本，如果它是僅有的版本。  
  
    -   Visual Studio.NET 2003年是最新版本，只有當存在和[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]不存在。  
  
    -   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 如果它是僅有的版本，則是最新版本。  
  
     最終結果是 devenv.exe 的 DEVENV_EXE_LATEST 包含最新版本的路徑。  
  
    ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>判斷最新版本的 Visual Studio 的 CustomAction 資料表資料列  
  
    |動作|類型|原始程式檔|目標|  
    |------------|----------|------------|------------|  
    |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
    |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
    |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
    ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>判斷最新版本的 Visual Studio 的 InstallExecuteSequence 資料表資料列  
  
    |動作|條件|序列|  
    |------------|---------------|--------------|  
    |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 和 NOT （DEVENV_EXE_2003 或 DEVENV_EXE_2005）|410|  
    |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 和不 DEVENV_EXE_2005|420|  
    |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
     您可以使用 DEVENV_EXE_LATEST 屬性中的 Windows 安裝程式套件登錄寫入 HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand 索引鍵的預設值，[DEVENV_EXE_LATEST]"%1"  
  
-   執行共用的啟動器程式，可讓來自可用 VSPackage 版本的最佳選擇。  
  
     開發人員[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]選擇這個方法來處理複雜需求的方案和專案所產生的許多版本的多個格式[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 這種方法中，您可以註冊啟動器程式做為延伸模組處理常式。 啟動器會檢查檔案，並決定哪個版本的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]和 VSPackage 可以處理該特定的檔案。 比方說，如果使用者開啟 naposledy uložil VSPackage 的特定版本的檔案，啟動器可以啟動該 VSPackage 中的相符版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。 此外，使用者可以設定永遠啟動的最新版本的啟動程式。 啟動程式也可能會提示使用者進行升級的檔案格式。 如果檔案的格式包含版本號碼，啟動器可以通知使用者，如果檔案格式是從版本晚於一或多個已安裝的 Vspackage。  
  
     啟動程式應該在共用的 VSPackage 的所有版本的 Windows 安裝程式元件。 此程序可確保永遠都會安裝最新版本，和所有版本的 VSPackage 會解除都安裝之前，不會移除項目。 如此一來，檔案關聯和啟動程式元件的其他登錄項目會保留即使解除安裝一個版本的 VSPackage。  
  
## <a name="uninstall-and-file-associations"></a>解除安裝與檔案關聯  
 解除安裝 VSPackage 可寫入的檔案關聯的登錄項目中移除的檔案關聯。 因此，擴充功能會有任何相關聯的程式。 Windows 安裝程式不會 「 修復 」 安裝 VSPackage 時新增的登錄項目。 以下是一些修正使用者的檔案關聯的方法：  
  
-   使用共用的啟動器元件，如先前所述。  
  
-   指示使用者執行使用者想要擁有的檔案關聯的 VSPackage 版本的修復。  
  
-   提供個別的可執行程式，重寫的適當的登錄項目。  
  
-   提供組態選項頁面或對話方塊中，可讓使用者選擇 檔案關聯，並回收遺失的關聯。 指示使用者解除安裝之後執行它。  
  
## <a name="see-also"></a>另請參閱  
 [並排顯示部署註冊副檔名的檔案](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)

