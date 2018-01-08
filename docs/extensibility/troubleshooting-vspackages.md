---
title: "疑難排解 Vspackage |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c4c2fc24775cee3d40857166d3415f90b2adf756
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-vspackages"></a>疑難排解 Vspackage
以下是常見的問題，您可能有與您的 VSPackage，並解決問題的秘訣。  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>若要疑難排解的 VSPackage，啟動可防止 Visual Studio  
  
-   啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]以安全模式。  
  
     若要啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]處於安全模式，在命令提示字元中，輸入**devenv.exe /safemode**。  
  
     此程序期間沒有 Vspackage 會載入除了隨附於 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>若要疑難排解不會載入 VSPackage  
  
1.  請確定您使用的註冊通常執行的實驗登錄根目錄 VSPackage 的登錄根目錄。  
  
     如需詳細資訊，請參閱[實驗執行個體的](../extensibility/the-experimental-instance.md)。  
  
2.  如果 VSPackage 的目標為執行實驗登錄根目錄中，請確定您正在執行的實驗版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     若要執行的實驗版本，請在命令視窗中輸入下列： **devenv /rootsuffix exp**。  
  
3.  請檢查您的 VSPackage 登錄項目。  
  
     如需詳細資訊，請參閱[註冊 Vspackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)和[管理 Vspackage](../extensibility/managing-vspackages.md)。  
  
4.  開啟**輸出**視窗的執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，無法載入 VSPackage。 VSPackage 載入失敗的原因的相關資訊可能會顯示該視窗中。  
  
    > [!NOTE]
    >  如果您要啟動的實驗版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]從[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)，檢查**輸出**兩個版本的視窗。  
  
5.  檢查活動記錄檔。  
  
     如需詳細資訊，請參閱[How to： 使用活動記錄檔](../extensibility/how-to-use-the-activity-log.md)。  
  
6.  如需有關由 IDE 所擲回例外狀況的詳細資訊，請按一下**例外狀況**上**偵錯**功能表啟用例外狀況。 在**例外狀況**對話方塊中選取您想通知的詳細資訊的例外狀況的類型。  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>若要疑難排解不會註冊 VSPackage  
  
1.  請確定 VSPackage 組件位於受信任的位置。 RegPkg 無法在未受信任或部分信任的位置，例如網路共用在預設.net 安全性組態中註冊組件。 每當使用者在不受信任的位置中建立專案時，會出現警告，雖然 「 不要顯示此訊息一次 」 的核取方塊可以避免發生此警告訊息。  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>若要疑難排解，看不到或，會產生錯誤，當您按一下命令的命令  
  
1.  合併新增或變更功能表命令以及已在 IDE 中，輸入下列命令[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]命令提示字元： **devenv /rootsuffix Exp /setup**。  
  
2.  請確定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可以找到 UI.dll vspackage。  
  
    1.  VSPackage 的 CLSID 的區段中找到封裝的登錄：  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<版本 >*\Packages  
  
    2.  請確認 SatelliteDll 子機碼所提供的路徑正確。  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>若要疑難排解的 VSPackage，非預期的行為  
  
1.  在您的程式碼中設定中斷點。  
  
     偵錯很好的起點是建構函式和初始設定方法。 您也可以在您想要評估，例如功能表命令的區域中設定中斷點。 若要啟用中斷點，您必須偵錯工具下執行。  
  
    1.  在 [專案] 功能表上，按一下 [屬性]。  
  
    2.  在**屬性頁**對話方塊中，選取**偵錯** 索引標籤。  
  
    3.  在**命令列引數**方塊中，輸入在開發環境的根尾碼，VSPackage 目標。 例如，若要選取的實驗組建，請輸入： **RootSuffix Exp**。  
  
    4.  在**偵錯**功能表上，按一下 **開始偵錯**或按 F5。  
  
        > [!NOTE]
        >  如果您正在偵錯的專案，建立或立即載入專案的現有執行個體。  
  
2.  使用活動記錄檔。  
  
     活動記錄在關鍵時刻寫入資訊的追蹤 VSPackage 的行為。 當您執行 VSPackage 零售環境中這項技術會很實用。 如需詳細資訊，請參閱[How to： 使用活動記錄檔](../extensibility/how-to-use-the-activity-log.md)。  
  
3.  使用公用符號。  
  
     若要改善可讀性，偵錯時，您可以附加偵錯工具的符號。  
  
    1.  從**工具/選項**功能表上，瀏覽至**偵錯/符號** 對話方塊。  
  
    2.  加入這個**符號檔 (.pdb) 位置**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  若要改善效能，例如指定符號快取資料夾：  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>疑難排解遺失的 VSPackage 或其相依性的其中一個  
  
1.  Managed 程式碼，請確定參考路徑正確無誤。  
  
    1.  在 [專案] 功能表上，按一下 [屬性]。  
  
    2.  選取**參考**索引標籤中**屬性頁**對話方塊，請確定所有路徑都是否正確。 或者，您可以使用**物件瀏覽器**瀏覽參考的物件。  
  
         Managed 程式碼，您可以使用[Fuslogvw.exe （組件繫結記錄檔檢視器）](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer)顯示失敗的組件載入的詳細資料。  
  
2.  Unmanaged 程式碼，找出在 VSPackage 的 CLSID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID 登錄節點：  
  
     HKLM\Software\Microsoft\Visual Studio\\*\<版本 >*\CLSID  
  
 請確定 [InprocServer32] 項目具有 VSPackage dll 的正確路徑。  
  
## <a name="see-also"></a>請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)