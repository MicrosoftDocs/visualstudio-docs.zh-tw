---
title: 疑難排解 Vspackage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2141d2fd7d046f61ba6febecc427066d7a09ba18
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904484"
---
# <a name="troubleshooting-vspackages"></a>針對 VSPackage 進行疑難排解
以下是您在 VSPackage 時可能會遇到的常見問題，以及解決問題的秘訣。

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>疑難排解讓 Visual Studio 無法啟動的 VSPackage

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]以安全模式啟動。

   若要以 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安全模式啟動，請在命令提示字元中，輸入**devenv.exe/safemode**。

   在此過程中，不會載入包含在中的 Vspackage 以外的任何 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>針對未載入的 VSPackage 進行疑難排解

1. 請確定您使用登錄根目錄，其中 VSPackage 已註冊要執行，通常是實驗性登錄根目錄。

    如需詳細資訊，請參閱[實驗實例](../extensibility/the-experimental-instance.md)。

2. 如果 VSPackage 的目標是要在實驗性登錄根目錄中執行，請確定您正在執行的實驗版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

    若要執行實驗性版本，請在命令視窗中輸入下列內容： **devenv/rootsuffix exp**。

3. 檢查您的 VSPackage 登錄專案。

    如需詳細資訊，請參閱[註冊 vspackage](registering-and-unregistering-vspackages.md)和[管理 vspackage](../extensibility/managing-vspackages.md)。

4. 開啟無法載入 VSPackage 之實例的 [**輸出**] 視窗 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 為什麼無法載入 VSPackage 的相關資訊可能會顯示在該視窗中。

   > [!NOTE]
   > 如果您 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 從 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 整合式開發環境（IDE）啟動的實驗性版本，請檢查這兩個版本的 [**輸出**] 視窗。

5. 檢查活動記錄。

    如需詳細資訊，請參閱[如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。

6. 如需 IDE 所擲回之例外狀況的詳細資訊，請按一下 [**調試**程式] 功能表上的 [**例外**狀況] 以啟用例外狀況。 在 [**例外**狀況] 對話方塊中，選取您想要取得詳細資訊的例外狀況類型。

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>針對未註冊的 VSPackage 進行疑難排解

1. 請確定 VSPackage 元件位於受信任的位置。 RegPkg 無法在不受信任或部分信任的位置註冊元件，例如預設 .net 安全性設定中的網路共用。 當使用者在不受信任的位置中建立專案時，雖然會出現警告，但是 [不要再顯示此訊息] 核取方塊可能會導致此警告無法重複發生。

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>若要疑難排解不可見或在您按一下命令時會產生錯誤的命令

1. 藉由在命令提示字元中輸入下列命令，來合併新的或已變更的功能表命令和已在 IDE 中的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ： **Devenv/rootsuffix Exp/setup**。

2. 請確定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可以找到 VSPackage 的 UI.dll。

   1. 在登錄的 [套件] 區段中，尋找 VSPackage 的 CLSID：

        HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \Packages

   2. 請確認 SatelliteDll 子機碼所指定的路徑是否正確。

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>針對非預期行為的 VSPackage 進行疑難排解

1. 在您的程式碼中設定中斷點。

     偵錯工具的良好起始點是「函式」和「初始化」方法。 您也可以在想要評估的區域（例如功能表命令）中設定中斷點。 若要啟用中斷點，您必須在偵錯工具下執行。

    1. 按一下 [專案]**** 功能表上的 [屬性]****。

    2. 在 [**屬性頁**] 對話方塊中，選取 [**調試**] 索引標籤。

    3. 在 [**命令列引數**] 方塊中，輸入您的 VSPackage 目標之開發環境的根尾碼。 例如，若要選取實驗性組建，請輸入： **/RootSuffix Exp**。

    4. 在 [**調試**] 功能表上，按一下 [**開始調試**] 或按 F5。

        > [!NOTE]
        > 如果您要對專案進行偵錯工具，請立即建立或載入專案的現有實例。

2. 使用 [活動記錄]。

     追蹤 VSPackage 行為，方法是在關鍵點將資訊寫入活動記錄。 當您在零售環境中執行 VSPackage 時，這項技術特別有用。 如需詳細資訊，請參閱[如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。

3. 使用公用符號。

     若要在進行偵錯工具時改善可讀性，您可以將符號附加至偵錯工具。

    1. 從 [**工具]/[選項**] 功能表，流覽至 [**調試]/[符號**] 對話方塊。

    2. 新增此**符號檔（.pdb）位置**：

         `https://msdl.microsoft.com/download/symbols`

    3. 若要改善效能，請指定符號快取資料夾，例如：

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>疑難排解遺失的 VSPackage 或其相依性的其中之一

1. 若為 managed 程式碼，請確定參考路徑是正確的。

   1. 按一下 [專案]**** 功能表上的 [屬性]****。

   2. 選取 [**屬性頁**] 對話方塊中的 [**參考**] 索引標籤，並確定所有路徑都正確。 或者，您可以使用**物件瀏覽器**來流覽參考的物件。

        若為 managed 程式碼，您可以使用[Fuslogvw.exe （元件系結記錄檔檢視器）](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer)來顯示失敗元件載入的詳細資料。

2. 若為非受控碼，請在 clsid 登錄節點中尋找 VSPackage 的 CLSID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ：

    HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \CLSID

   請確定 InprocServer32 專案具有 VSPackage dll 的正確路徑。

## <a name="see-also"></a>另請參閱
- [VSPackage](../extensibility/internals/vspackages.md)
