---
title: "管理並行的檔案關聯 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7d0a6f8ec88a49b785b771aef51dc25b5646ffda
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="managing-side-by-side-file-associations"></a>管理並行的檔案關聯
如果您的 VSPackage 提供的檔案關聯，您必須決定如何處理的並行安裝所在的特定版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]應該被叫用以開啟檔案。 不相容的檔案格式複合問題。  
  
 使用者可預期的產品為相容於舊版本中，使現有的檔案可以載入新版本中，而不會遺失資料的新版本。 在理想情況下，您的 VSPackage 可以同時載入及儲存較舊版本的檔案格式。 如果不是，則為 true，您應該提供升級至新版的 VSPackage 的檔案格式。 這種方法的缺點是，無法在先前版本中開啟升級的檔案。  
  
 若要避免這個問題，您可以變更擴充功能時變成不相容的檔案格式。 例如，VSPackage 的第 1 版可以使用延伸模組、.mypkg10 和 2 也可以使用延伸模組的版本.mypkg20。 這項差異會識別開啟特定檔案的 VSPackage。 如果您加入較新的 Vspackage 的舊擴充功能相關聯的程式清單，使用者可以以滑鼠右鍵按一下檔案，並選擇在較新的 VSPackage 中開啟它。 此時，您的 VSPackage 可以提供給升級至新格式的檔案或開啟檔案，並維持與舊版 VSPackage 的相容性。  
  
> [!NOTE]
>  您可以結合這些方式。 比方說，您可以載入較舊的檔案，以提供回溯相容性，並提供升級的檔案格式，當使用者儲存它。  
  
## <a name="facing-the-problem"></a>面向問題  
 如果您想使用相同的延伸模組的多個並行的 Vspackage，您必須選擇的新版[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]與副檔名相關聯。 以下是兩個替代方法：  
  
-   最新版本中開啟檔案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]使用者的電腦上安裝。  
  
     在這種方式，您的安裝程式會負責決定的最新版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]並納入所撰寫的檔案關聯的登錄項目中。 您可以在 Windows Installer 封裝時，包含要設定此屬性，指出最新版的自訂動作[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
    > [!NOTE]
    >  在此情況下，「 最新 」 表示 「 最新支援的版本。 」 這些安裝程式項目不會自動偵測到的後續版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 中的項目[偵測系統需求](../extensibility/internals/detecting-system-requirements.md)和[命令，必須是執行之後安裝](../extensibility/internals/commands-that-must-be-run-after-installation.md)類似於這裡所呈現的項目，則必須支援的其他版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     CustomAction 資料表中的下列資料列將 DEVENV_EXE_LATEST 屬性設為是 AppSearch 所設定的屬性和 RegLocator 資料表中所討論[命令，必須是執行之後安裝](../extensibility/internals/commands-that-must-be-run-after-installation.md)。 InstallExecuteSequence 資料表中的資料列來排程執行順序中較早的自訂動作。 條件的資料行進行邏輯工作中的值：  
  
    -   Visual Studio.NET 2002年是最新版本，如果它是僅有的版本。  
  
    -   Visual Studio.NET 2003年是最新版本，只有當存在和[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]不存在。  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]如果它是僅有的版本，是最新版本。  
  
     最後結果就是 DEVENV_EXE_LATEST 包含 devenv.exe 的最新版本的路徑。  
  
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
  
     您可以使用 DEVENV_EXE_LATEST 屬性中的 Windows Installer 套件登錄寫入 HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand 索引鍵的預設值，[DEVENV_EXE_LATEST]"%1"  
  
-   執行可以做出最好的選擇，從可用的 VSPackage 版本的共用的啟動器程式。  
  
     開發人員[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]選擇這種方法來處理複雜的方案和專案所產生的許多版本的多個格式的需求[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 這種方法，您可以註冊啟動器程式做為延伸模組處理常式。 啟動器會檢查檔案，並決定哪個版本的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]而且 VSPackage 可以處理該特定檔案。 比方說，如果使用者開啟上次儲存的特定版本的 VSPackage 的檔案，啟動器可以啟動該 VSPackage 中的版本相符[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 此外，使用者無法設定永遠啟動的最新版本的啟動程式。 啟動器也可能會提示使用者升級檔案的格式。 如果檔案的格式包含版本號碼，啟動器無法在從晚於一或多個已安裝 Vspackage 版本的檔案格式是否通知使用者。  
  
     啟動器應該與您的 VSPackage 的所有版本共用的 Windows Installer 元件中。 此程序確保一律安裝最新版本，並已解除安裝所有 VSPackage 版本之前，不會移除。 如此一來，檔案關聯啟動程式元件的其他登錄項目會保留和即使 VSPackage 版本已解除安裝。  
  
## <a name="uninstall-and-file-associations"></a>解除安裝與檔案關聯  
 解除安裝的 VSPackage，將檔案關聯的登錄項目移除的檔案關聯。 因此，延伸會有任何相關聯的程式。 Windows 安裝程式不會 「 修復 」 安裝 VSPackage 時，已新增的登錄項目。 以下是一些修正使用者的檔案關聯的方式：  
  
-   使用共用的啟動器元件，如先前所述。  
  
-   指示使用者執行使用者想要擁有檔案關聯的 VSPackage 版本的修復。  
  
-   提供個別的可執行檔程式重寫的適當的登錄項目。  
  
-   提供組態選項的頁面或對話方塊方塊，可讓使用者選擇檔案關聯，以便回收遺失的關聯。 指示使用者解除安裝後執行它。  
  
## <a name="see-also"></a>請參閱  
 [註冊檔案名稱擴充功能-並存部署](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [註冊適用於副檔名的動詞命令](../extensibility/registering-verbs-for-file-name-extensions.md)