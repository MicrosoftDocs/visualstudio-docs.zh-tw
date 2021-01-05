---
title: 疑難排解 Vspackage |Microsoft Docs
description: 瞭解您在 VSPackage 時可能遇到的常見問題，以及解決問題的疑難排解秘訣。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0c1e85c59d49f4079172cfb098701b09d461bdf3
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716038"
---
# <a name="troubleshooting-vspackages"></a>針對 VSPackage 進行疑難排解
以下是您可能會遇到的 VSPackage 問題，以及解決問題的秘訣。

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>針對可讓 Visual Studio 無法啟動的 VSPackage 進行疑難排解

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]以安全模式啟動。

   若要 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在安全模式中啟動，請在命令提示字元中，輸入 **devenv.exe/safemode**。

   在這個過程中，除了隨附的 Vspackage 以外，不會載入任何 Vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>針對未載入的 VSPackage 進行疑難排解

1. 請確定您使用的登錄根目錄是 VSPackage 註冊用來執行，通常是實驗登錄根目錄。

    如需詳細資訊，請參閱 [實驗實例](../extensibility/the-experimental-instance.md)。

2. 如果 VSPackage 的目標是要在實驗登錄根目錄中執行，請確定您正在執行的實驗版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。

    若要執行實驗版本，請在命令視窗中輸入下列命令： **devenv/rootsuffix exp**。

3. 檢查您的 VSPackage 登錄專案。

    如需詳細資訊，請參閱 [註冊 vspackage](registering-and-unregistering-vspackages.md) 和 [管理 vspackage](../extensibility/managing-vspackages.md)。

4. 開啟失敗載入 VSPackage 之實例的 **輸出** 視窗 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 VSPackage 載入失敗原因的相關資訊可能會顯示在該視窗中。

   > [!NOTE]
   > 如果您要 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 從整合式開發環境啟動的實驗版本 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (IDE) ，請檢查兩個版本的 **輸出** 視窗。

5. 檢查活動記錄。

    如需詳細資訊，請參閱 [如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。

6. 如需 IDE 擲回之例外狀況的詳細資訊，請按一下 [**調試** 程式] 功能表上的 [**例外** 狀況] 來啟用例外狀況。 在 [ **例外** 狀況] 對話方塊中，選取您需要詳細資訊的例外狀況類型。

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>針對未註冊的 VSPackage 進行疑難排解

1. 請確定 VSPackage 元件位於受信任的位置。 RegPkg 無法在不受信任或部分信任的位置（例如，預設 .net 安全性設定中的網路共用）註冊元件。 雖然每當使用者在不受信任的位置建立專案時，就會顯示警告，但 [不要再顯示此訊息] 核取方塊可以防止此警告重複發生。

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>針對看不到或在您按一下命令時產生錯誤的命令進行疑難排解

1. 在命令提示字元中輸入下列命令，以合併新的或已變更的功能表命令和已在 IDE 中的命令 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ： **Devenv/rootsuffix Exp/setup**。

2. 請確定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可以找到您 VSPackage 的 UI.dll。

   1. 在登錄的 [封裝] 區段中，尋找 VSPackage 的 CLSID：

        HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \Packages

   2. 確認 SatelliteDll 子機碼指定的路徑正確。

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>若要針對非預期行為的 VSPackage 進行疑難排解

1. 在您的程式碼中設定中斷點。

     偵測函式和初始化方法是很好的切入點。 您也可以在想要評估的區域（例如功能表命令）中設定中斷點。 若要啟用中斷點，您必須在偵錯工具下執行。

    1. 按一下 [專案]  功能表上的 [屬性]  。

    2. 在 [ **屬性頁** ] 對話方塊中，選取 [ **Debug** ] 索引標籤。

    3. 在 [ **命令列引數** ] 方塊中，輸入 VSPackage 的目標開發環境的根目錄尾碼。 例如，若要選取實驗性組建，請輸入： **/RootSuffix Exp**。

    4. 在 [ **調試** ] 功能表上，按一下 [ **開始調試** ] 或按 F5。

        > [!NOTE]
        > 如果您正在進行專案的偵錯工具，請立即建立或載入專案的現有實例。

2. 使用活動記錄。

     藉由在關鍵點將資訊寫入活動記錄檔來追蹤 VSPackage 行為。 當您在零售環境中執行 VSPackage 時，此技術特別有用。 如需詳細資訊，請參閱 [如何：使用活動記錄](../extensibility/how-to-use-the-activity-log.md)。

3. 使用公用符號。

     若要在偵錯工具中改善可讀性，您可以將符號附加至偵錯工具。

    1. 從 [ **工具]/[選項** ] 功能表，流覽至 [ **調試/符號** ] 對話方塊。

    2. 將此 **符號檔 ( .pdb) 位置**：

         `https://msdl.microsoft.com/download/symbols`

    3. 若要改善效能，請指定符號快取資料夾，例如：

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>疑難排解遺失的 VSPackage 或其相依性的其中之一

1. 針對 managed 程式碼，請確定參考路徑是否正確。

   1. 按一下 [專案]  功能表上的 [屬性]  。

   2. 選取 [**屬性頁**] 對話方塊中的 [**參考**] 索引標籤，並確定所有路徑都是正確的。 或者，您也可以使用 **物件瀏覽器** 來流覽參考的物件。

        針對 managed 程式碼，您可以使用 [Fuslogvw.exe (元件系結記錄檔檢視器) ](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) 來顯示失敗元件載入的詳細資料。

2. 針對非受控碼，在 clsid 登錄節點中尋找 VSPackage 的 CLSID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ：

    HKLM\Software\Microsoft\Visual Studio \\ *\<version>* \CLSID

   請確定 InprocServer32 專案具有正確的 VSPackage dll 路徑。

## <a name="see-also"></a>請參閱
- [VSPackages](../extensibility/internals/vspackages.md)
- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)
