---
title: "在離線環境中安裝 Visual Studio 的特殊考量 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 62fc2d38a628cfc28913a0a45e1e3cb5d3852330
ms.contentlocale: zh-tw
ms.lasthandoff: 08/14/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>在離線環境中安裝 Visual Studio 的特殊考量

因為許多元件都會定期更新，所以 Visual Studio 主要設計成安裝在連線到網際網路的電腦上。 不過，透過一些額外的步驟，就可能在沒有可運作之網際網路連線的環境部署 Visual Studio。

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>安裝 Visual Studio 離線安裝所需的憑證
Visual Studio 安裝程式引擎只會安裝受信任的內容。 它的作法是檢查要下載之內容的 Authenticode 簽章，並在安裝前驗證所有內容是否受信任。 如此可讓您的環境安全不受到入侵下載位置的攻擊。 Visual Studio 安裝程式因此需要在使用者的電腦上安裝數個標準的 Microsoft 根和中繼憑證，並且要是最新狀態。 如果電腦保持使用 Windows Update 更新，則會自動更新簽署憑證；並且在安裝期間，Visual Studio 會視需要重新整理憑證，以驗證檔案簽章。

對於離線電腦沒有最新根憑證的企業，系統管理員可以使用[設定受信任的根目錄和不允許的憑證](https://technet.microsoft.com/en-us/library/dn265983.aspx)頁面上的指示來更新它們。 或者，當您建立網路配置時，會將必要的憑證下載至 `certificates` 資料夾。 您接著可以按兩下憑證檔案，然後透過 [憑證管理員精靈] 按一下憑證檔案，以手動安裝憑證。 如果要求您輸入密碼，請保留空白。

如果您撰寫指令碼，在離線環境中將 Visual Studio 部署至用戶端工作站，您應該遵循下列步驟：

1. 複製[憑證管理員工具](https://msdn.microsoft.com/en-us/library/e78byta0.aspx) (`certmgr.exe`) 到安裝共用 (例如，`\\server\share\vs2017`)。 `certmgr.exe` 不包含為 Windows 本身的一部分，但提供於 [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) 中。

2. 使用下列命令建立批次檔：

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. 將批次檔部署至用戶端。 此命令應該從提升權限的程序執行。

### <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>`certificates` 資料夾中的憑證檔案是什麼？
此資料夾中的三個 `.p12` 檔案都包含中繼憑證和根憑證。 使用 Windows Update 維持最新狀態的大部分系統都已經安裝這些憑證。

* `ManifestSignCertificates.p12` 包含：
    * 中繼憑證：**Microsoft 程式碼簽署 PCA 2011**
        * 不需要。 如果有的話，可改善某些案例的效能。
    * 根憑證：**Microsoft 根憑證授權單位 2011**
        * 在沒有安裝最新 Windows Updates 的 Windows 7 Service Pack 1 系統上需要。
* `ManifestCounterSignCertificates.p12`
    * 中繼憑證：**Microsoft 時間戳記 PCA 2010**
        * 不需要。 如果有的話，可改善某些案例的效能。
    * 根憑證：**Microsoft 根憑證授權單位 2010**
        * 在沒有安裝最新 Windows Updates 的 Windows 7 Service Pack 1 系統上需要。
* `vs_installer_opc.SignCertificates.p12`
    * 中繼憑證：**Microsoft 程式碼簽署 PCA**
        * 所有系統都需要。 請注意，從 Windows Update 套用所有更新的系統可能沒有此憑證。
    * 根憑證：**Microsoft 根憑證授權單位**
        * 必要項。 此憑證隨附於執行 Windows 7 或更新版本的系統。

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>為何不會自動安裝來自 `certificates` 資料夾的憑證？
當簽章在線上環境中驗證時，會使用 Windows API 下載憑證並新增至系統。 在此程序期間，會驗證是否已透過系統管理設定來信任並允許憑證。 此驗證程序無法在大部分離線環境中進行。 手動安裝憑證可讓企業系統管理員確定憑證受到信任，且符合他們組織的安全原則。

### <a name="checking-if-certificates-are-already-installed"></a>檢查是否已安裝憑證
在安裝系統上的一個檢查方法是遵循下列步驟：
1. 執行 `mmc.exe`。<br/>
  a. 按一下 [檔案]，然後選取 [新增/移除嵌入式管理單元]。<br/>
  b. 按兩下 [憑證]，並選取 [電腦帳戶]，然後按一下 [下一步]。<br/>
  c.  選取 [本機電腦]，並按一下 [完成]，然後按一下 [確定]。<br/>
  d. 展開 [憑證 (本機電腦)]。<br/>
  e. 展開 [信任的根憑證授權]，然後選取 [憑證]。<br/>
    * 檢查這份必要根憑證清單。<br/>
  
   f. 展開 [中繼憑證授權]，然後選取 [憑證]。<br/>
    * 檢查這份必要中繼憑證清單。<br/>

2. 按一下 [檔案]，然後選取 [新增/移除嵌入式管理單元]。<br/>
  a. 按兩下 [憑證]，並選取 [我的使用者帳戶]，然後依序按一下 [完成] 和 [確定]。<br/>
  b. 展開 [憑證 - 目前的使用者]。<br/>
  c.  展開 [中繼憑證授權]，然後選取 [憑證]。<br/>
    * 檢查這份必要中繼憑證清單。<br/>

如果憑證名稱不在 [Issued To] (核發給) 資料行中，則必須予以安裝。  如果中繼憑證只位於 [目前使用者] 中繼憑證存放區中，則只有已登入的使用者才能使用它，並且可能需要為其他使用者安裝它。

## <a name="install-visual-studio"></a>安裝 Visual Studio
在您安裝憑證之後，可以使用 [建立 Visual Studio 的網路安裝] 頁面的 [從網路安裝部署]((create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation) 區段中的指示，繼續離線部署 Visual Studio，而不需要額外的特殊步驟。


## <a name="see-also"></a>請參閱
* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)

