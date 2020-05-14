---
title: 容損 VS 包 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698922"
---
# <a name="troubleshooting-vspackages"></a>針對 VSPackage 進行疑難排解
以下是 VSPackage 中可能存在的常見問題以及解決問題的提示。

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>排除阻止視覺化工作室啟動的 VS 套件的故障

- 在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]安全模式下啟動。

   在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]安全模式下啟動,在指令提示符下,鍵入**devenv.exe /safemode**。

   在此過程中,除了附帶的 VS 包外,不會載入[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]任何 VS 包。

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>排除未載入的 VS 套件

1. 請確保正在使用註冊 VSPackage 的註冊表根(通常是實驗註冊錶根)。

    有關詳細資訊,請參閱[實驗實例](../extensibility/the-experimental-instance.md)。

2. 如果 VSPackage 的目標是在實驗註冊表根中執行,請確保執行的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]實驗版本 。

    要執行實驗版本,在命令視窗中鍵入以下內容 **:devenv /rootuffix exp**。

3. 檢查您的 VSPackage 註冊表項。

    有關詳細資訊,請參閱註冊[VS 套件](registering-and-unregistering-vspackages.md)與管理 VS[套件](../extensibility/managing-vspackages.md)。

4. 打開無法**Output**載入 VSPackage 的[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]實體的輸出視窗。 有關 VSPackage 無法載入原因的資訊可能會顯示在該視窗中。

   > [!NOTE]
   > 如果要從[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)][!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式開發環境(IDE) 啟動其實驗版本,請檢查兩個版本的**輸出**視窗。

5. 檢查活動日誌。

    有關詳細資訊,請參閱[:使用活動紀錄](../extensibility/how-to-use-the-activity-log.md)。

6. 有關IDE引發的異常的詳細資訊,請單擊 **「調試**」功能表上**的異常**以啟用異常。 在 **"例外"** 對話框中,選擇您希望瞭解有關的詳細資訊的異常類型。

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>排除未註冊的 VS 套件

1. 確保 VSPackage 程式集駐留在受信任的位置。 RegPkg 無法在不受信任或部分受信任的位置(如預設 .net 安全配置中的網路共享)註冊程式集。 儘管每當使用者在不受信任的位置創建專案時都會出現警告,但"不再顯示此消息"複選框可以防止此警告再次發生。

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>對不可見的指令進行故障排除,或在單擊指令時產生錯誤

1. 通過在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]指令提示符中鍵入以下內容 **:devenv /rootuffix Exp /setup,** 合併新的或更改的功能表命令以及已在 IDE 中的命令。

2. 請確保[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可以為 VSPackage 找到 UI.dll。

   1. 在註冊表的「打包」部分查找 VS 套件的 CLSID:

        HKLM_軟體_微軟_視覺工作室\\*\<版本>[* 包]

   2. 驗證 SatelliteDll 子鍵給出的路徑是否正確。

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>排除行為意外的 VS 套件

1. 在您的程式碼中設定中斷點。

     調試的良好起點是構造函數和初始化方法。 您還可以在要計算的區域(如功能表命令)中設置斷點。 要啟用斷點,必須在調試器下運行。

    1. 按一下 [專案]**** 功能表上的 [屬性]****。

    2. 在「**屬性頁」** 對話框中,選擇 **「除錯**」選項卡。

    3. 在 **「命令列參數」** 框中,鍵入 VSPackage 目標開發環境的根後綴。 例如,要選擇實驗生成,請鍵入 **:/RootSuffix Exp**。

    4. 在 **「調試」** 選單上,按下 **「開始調試」** 或按 F5。

        > [!NOTE]
        > 如果要除錯專案,請立即建立或載入專案的現有實例。

2. 使用活動日誌。

     通過在關鍵點將資訊寫入活動日誌來跟蹤 VSPackage 行為。 當您在零售環境中運行 VSPackage 時,此技術特別有用。 有關詳細資訊,請參閱[:使用活動紀錄](../extensibility/how-to-use-the-activity-log.md)。

3. 使用公共符號。

     為了提高調試時的可讀性,可以將符號附加到調試器。

    1. 從 **「工具/選項**」選單中導航到 **「除錯/符號」** 對話框。

    2. 新增此**符號檔 (.pdb) 位置**:

         `https://msdl.microsoft.com/download/symbols`

    3. 為了提高性能,請指定符號快取資料夾,例如:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>排除遺失的 VSPackage 或其相依項之一

1. 對於託管代碼,請確保引用路徑正確。

   1. 按一下 [專案]**** 功能表上的 [屬性]****。

   2. 在「**屬性頁」** 對話方塊中選擇 **「引用**」選項卡,並確保所有路徑都正確。 或者,您可以使用**物件瀏覽器**流覽引用的物件。

        對於託管代碼,可以使用[Fuslogvw.exe(程式集綁定日誌檢視器)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer)來顯示程式集負載失敗的詳細資訊。

2. 對於非託管代碼,在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]CLSID 註冊表節點中找到 VSPackage 的 CLSID:

    HKLM_軟體_微軟_視覺工作室\\*\<版本*>[CLSID]

   確保 InprocServer32 條目具有 VSPackage dll 的正確路徑。

## <a name="see-also"></a>另請參閱
- [VSPackage](../extensibility/internals/vspackages.md)
