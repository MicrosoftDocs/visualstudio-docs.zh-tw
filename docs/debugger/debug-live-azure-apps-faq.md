---
title: 快照集偵錯的常見問題集 | Microsoft Docs
description: 查看使用 Visual Studio 中的快照偵錯工具來對即時 Azure 應用程式進行偵錯工具時，可能會出現的常見問題)  (常見問題的清單。
ms.custom: SEO-VS-2020
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9bd8a80f7f6d11587c9f0cd5c6b9bf96e38a0a74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873233"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 中快照集偵錯的常見問題集

以下是使用快照偵錯工具針對即時 Azure 應用程式進行偵錯時，可能出現問題的清單。

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>建立快照集的效能成本為何？

當快照偵錯工具擷取您應用程式的快照集時，它會分支應用程式的程序，並暫止分支複本。 當您針對快照集進行偵錯時，其實是針對程序的分支複本進行偵錯。 此程序只需要 10 到 20 毫秒，但不會複製應用程式的完整堆積。 而是只會複製頁面資料表，並將頁面設定為寫入時複製。 如果堆積中應用程式的部分物件有所變更，就會複製它們的個別頁面。 這是每個快照集都會佔用小部分記憶體 (對大多數應用程序而言，大約為幾百KB) 的原因。

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>如果我有相應放大的 Azure App Service (應用程式的多個執行個體) 的話，會發生什麼事？

當您的應用程式有多個執行個體時，快照點會套用至每一個執行個體。 只有使用指定條件叫用的第一個快照點會建立快照集。 如果有多個快照點，之後的快照集會來自建立第一個快照集的同一個執行處理。 傳送至輸出視窗的記錄點只會顯示來自一個執行個體的訊息，傳送至應用程式記錄檔的記錄點則會傳送來自每個執行個體的訊息。

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>快照偵錯工具如何載入符號？

快照偵錯工具要求在本機有您應用程式的相符符號，或將符號部署至您的 Azure App Service。 目前不支援 (Embedded Pdb。 ) 快照偵錯工具會自動從您的 Azure App Service 下載符號。 從 Visual Studio 2017 15.2 版開始，部署至 Azure App Service 也會部署您應用程式的符號。

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>快照偵錯工具是否可用於應用程式的發行組建？

是 - 快照偵錯工具可用於發行組建。 在函式中置入快照點時，會將函式重新編譯回偵錯版本，因此可偵錯。 停止快照偵錯工具會讓函式回復成發行組建版本。

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>記錄點 會對生產環境應用程式造成副作用嗎？

否 - 新增至應用程式的任何記錄訊息都會以虛擬方式進行評估。 它們無法在您的應用程式中造成任何副作用。 不過，某些原生屬性可能無法使用記錄點存取。

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>如果我的伺服器負載很輕，快照偵錯工具是否可運作？

是。即使伺服器負載很輕，快照偵錯工具依然能夠運作。 在伺服器可用記憶體容量偏低的情況下，快照偵錯工具會進行節流且不會擷取快照集。

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>如何解除安裝快照偵錯工具？

可透過下列步驟，在 App Service 上解除安裝快照偵錯工具網站延伸模組：

1. 您可以透過 Visual Studio 或 Azure 入口網站中的 Cloud Explorer 來關閉 App Service。
1. 瀏覽至您 App Service 的 Kudu 網站 (也就是 yourappservice.**scm**.azurewebsites.net)，並瀏覽至 [網站延伸模組]。
1. 按一下快照偵錯工具網站延伸模組上的 X 即可將它移除。

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>為什麼會在快照偵錯工具工作階段期間開啟連接埠？

快照偵錯工具必須開啟一組連接埠，才能針對在 Azure 中建立的快照集進行偵錯，這些和進行遠端偵錯時所需的連接埠相同。 [您可以在此處找到連接埠清單](../debugger/remote-debugger-port-assignments.md)。

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>如何? 停用遠端偵錯程式延伸模組？

針對應用程式服務：
1. 透過 App Service 的 Azure 入口網站停用遠端偵錯程式擴充功能。
2. Azure 入口網站 > 應用程式服務資源 blade > *應用程式設定*
3. 流覽至 [ *調試* 程式] 區段，然後按一下 [ *關閉* ] 按鈕以進行 *遠端偵錯* 程式。

針對 AKS：
1. 更新您的 Dockerfile，以移除與 [Docker 映射上的 Visual Studio 快照偵錯工具](https://github.com/Microsoft/vssnapshotdebugger-docker)對應的區段。
2. 重建並重新部署修改過的 Docker 映射。

針對虛擬機器/虛擬機器擴展集，移除遠端偵錯程式延伸模組、憑證、庫] 和輸入 NAT 集區，如下所示：

1. 移除遠端偵錯程式延伸模組

   有幾種方式可以停用虛擬機器和虛擬機器擴展集的遠端偵錯程式：

      - 透過 Cloud Explorer 停用遠端偵錯程式

         - Cloud Explorer > 您的虛擬機器資源 > 停用偵錯工具 (Cloud Explorer) 上的虛擬機器擴展集不存在停用的偵錯工具。

      - 使用 PowerShell 腳本/Cmdlet 停用遠端偵錯程式

         若為虛擬機器：

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         針對虛擬機器擴展集：

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - 透過 Azure 入口網站停用遠端偵錯程式
         - Azure 入口網站 > 虛擬機器/虛擬機器擴展集的資源分頁 > 擴充功能
         - 卸載 VisualStudio. Remotedebug.js. VSRemoteDebugger 延伸模組

         > [!NOTE]
         > 虛擬機器擴展集-入口網站不允許移除 DebuggerListener 埠。 您將需要使用 Azure PowerShell。 如需詳細資料，請參閱下文。

2. 移除憑證和 Azure KeyVault

   為虛擬機器或虛擬機器擴展集安裝遠端偵錯程式延伸模組時，會建立用戶端和伺服器憑證，以使用 Azure 虛擬機器/虛擬機器擴展集資源來驗證 Visual Studio 用戶端。

   - 用戶端憑證

      此憑證是自我簽署的憑證，位於 Cert：/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      從您的電腦移除此憑證的其中一種方式是透過 PowerShell

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - 伺服器憑證
      - 對應的伺服器憑證指紋會以秘密的形式部署至 Azure KeyVault。 Visual Studio 會嘗試在對應至虛擬機器或虛擬機器擴展集資源的區域中尋找或建立具有前置詞 MSVSAZ * 的 KeyVault。 因此，所有虛擬機器或虛擬機器擴展集資源都會部署到該區域，因此會共用相同的 KeyVault。
      - 若要刪除伺服器憑證指紋秘密，請移至 Azure 入口網站，並在裝載資源的相同區域中尋找 MSVSAZ * KeyVault。 刪除應標示的秘密 `remotedebugcert<<ResourceName>>`
      - 您也需要透過 PowerShell 從您的資源刪除伺服器秘密。

      針對虛擬機器：

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      針對虛擬機器擴展集：

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. 只)  (的虛擬機器擴展集，移除所有 DebuggerListener 的輸入 NAT 集區

   遠端偵錯程式導入了 DebuggerListener 的系結 NAT 集區，這些集區會套用至擴展集的負載平衡器。

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>如何? 停用快照偵錯工具？

針對 App Service：
1. 透過 App Service 的 Azure 入口網站停用快照偵錯工具。
2. Azure 入口網站 > 應用程式服務資源 blade > *應用程式設定*
3. 刪除 Azure 入口網站中的下列應用程式設定，並儲存您的變更。
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > 應用程式設定的任何變更將會起始應用程式重新開機。 如需應用程式設定的詳細資訊，請參閱 [Azure 入口網站中的設定 App Service 應用程式](/azure/app-service/web-sites-configure)。

針對 AKS：
1. 更新您的 Dockerfile，以移除與 [Docker 映射上的 Visual Studio 快照偵錯工具](https://github.com/Microsoft/vssnapshotdebugger-docker)對應的區段。
2. 重建並重新部署修改過的 Docker 映射。

虛擬機器/虛擬機器擴展集：

有幾種方式可以停用快照偵錯工具：
- Cloud Explorer > 虛擬機器/虛擬機器擴展集資源 > 停用診斷

- Azure 入口網站 > 您的虛擬機器/虛擬機器擴展集資源分頁 > 延伸模組 > 卸載 >microsoft.insights.vmdiagnosticssettings 延伸模組

- 來自[Az powershell](/powershell/azure/overview)的 powershell Cmdlet

   虛擬機器：

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   虛擬機器擴展集：

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>另請參閱

- [Visual Studio 偵錯](../debugger/index.yml)
- [使用快照偵錯工具針對即時 ASP.NET 應用程式進行偵錯](../debugger/debug-live-azure-applications.md)
- [使用快照偵錯工具來偵測 Azure 虛擬 Machines\Virtual 機擴展集的即時 ASP.NET](../debugger/debug-live-azure-virtual-machines.md)
- [使用快照偵錯工具針對即時 ASP.NET Azure Kubernetes 進行偵錯](../debugger/debug-live-azure-kubernetes.md)
- [快照偵錯的疑難排解和已知問題](../debugger/debug-live-azure-apps-troubleshooting.md)
