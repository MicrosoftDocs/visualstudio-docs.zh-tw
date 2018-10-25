---
title: 設定 Windows 防火牆進行遠端偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f6904313ff585b8099c993f83e90bacb91a4ba2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847951"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>設定 Windows 防火牆進行遠端偵錯
本主題描述如何設定防火牆，在執行下列作業系統的電腦上啟用遠端偵錯：  
  
- Windows 10  
  
- Windows 8/8.1  
  
- Windows 7   
  
- Windows Server 2012 R2  

- Windows Server 2012
  
- Windows Server 2008 R2 
  
  如果正在偵錯的網路未受到防火牆保護，便不需要進行這項設定。 否則，裝載 Visual Studio 的電腦和要進行偵錯的遠端電腦都需要進行變更防火牆設定。  
  
  **IPSec** 如果您的網路要求使用 IPSec 執行通訊，您必須在 Visual Studio 主機電腦和遠端電腦上都開啟其他連接埠。  
  
  **網頁伺服器** 如果您正在偵錯遠端網頁伺服器，您必須在遠端電腦上開啟其他連接埠。 （如 IIS、 連接埠 80 必須開啟。）  
  
  請注意，這兩部電腦不需要執行相同的作業系統。 例如，Visual Studio 電腦可以執行 Windows 10，而遠端電腦則可以執行 Windows Server 2012 R2。      
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>在遠端電腦上啟用遠端偵錯的連接埠  
  
|**連接埠**|**傳入/傳出**|**通訊協定**|**描述**|   
|-|-|-|-|  
|4022|連入|TCP|適用於 VS 2017。 針對每個 Visual Studio 版本，通訊埠編號會遞增 2。 如需詳細資訊，請參閱 < [Visual Studio 遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)。|  
|4023|連入|TCP|適用於 VS 2017。 針對每個 Visual Studio 版本，通訊埠編號會遞增 2。 （只用於從遠端偵錯 64 位元版本的遠端偵錯工具的 32 位元處理程序。）如需詳細資訊，請參閱 < [Visual Studio 遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)。| 
|3702|傳出|UDP|（選擇性）遠端偵錯工具探索的必要項。|    
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>如何在 Windows 防火牆中設定連接埠  

當您安裝 Visual Studio 或遠端偵錯工具時，軟體會嘗試開啟正確的連接埠。 不過，在某些情況下 （例如使用協力廠商防火牆），您可能需要手動開啟連接埠。 如果您需要確認連接埠已開啟，請參閱[疑難排解](#troubleshooting)。 一些指示開啟連接埠可能會不同，在舊版 Windows 上的。

若要開啟連接埠：
  
1. 開啟**開始**功能表中，搜尋**具有進階安全性的 Windows 防火牆**。

2. 然後選擇**輸入規則 > 新的規則 > 連接埠**，然後按一下**下一步**。 (針對連出規則，請選擇**輸出規則**改用。)

3. 選擇  **TCP**或是**UDP**，取決於連接埠號碼。

4. 底下**特定本機連接埠**，輸入連接埠號碼，按一下**下一步**。

5. 按一下 [**允許連線**，然後按一下**下一步]**。

6. 選取一或多個網路類型，以啟用連接埠，並按一下**下一步**。

    您選取的類型必須包括遠端電腦連線的網路。
7. 新增名稱 (例如**msvsmon**， **IIS**，或**Web Deploy**) 規則，然後按一下 **完成**。

    您應該會看到您在 [輸入規則] 或 [輸出規則] 清單中的新規則。

## <a name="troubleshooting"></a>疑難排解

如果您無法使用遠端偵錯工具附加至您的應用程式，您可能需要確認正確的連接埠已開啟。

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-visual-studio-computer"></a>請確認連接埠已在 Visual Studio 電腦上的 Windows 防火牆中開啟  
 設定 Windows 防火牆的指示在不同作業系統上稍有不同。 Windows 8/8.1、 Windows 10 和 Windows Server 2012，word**應用程式**則使用 Windows 7 或 Windows Server 2008，word**程式**用; 在下列步驟中，我們將使用單字**應用程式**。  
  
1.  開啟 [Windows 防火牆] 頁面。 (在 [開始]  功能表搜尋方塊中，輸入 [Windows 防火牆] )。  
  
2.  按一下 [允許應用程式或功能通過 Windows 防火牆] 。  
  
3.  在 [允許應用程式和功能]  清單中尋找 [Visual Studio 遠端偵錯工具探索] 。 如果有列出，請確定已選取，而且也選取一或多個網路類型。  
  
4.  如果未列出 [Visual Studio 遠端偵錯工具探索]  ，請按一下 [允許另一個應用程式] 。 如果您仍然不會看到**新增應用程式** 視窗中，按一下**瀏覽**並瀏覽至 **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具**. 尋找應用程式適當的資料夾 (x86、x64、Appx)，然後選取 **msvsmon.exe**。 然後按一下 [加入] 。  
  
5.  在 **允許應用程式和功能**清單中，選取**Visual Studio 遠端偵錯工具**。 核取您想要遠端偵錯監視與其通訊的一或多個網路類型 ([網域]、[家用/工作 (私用)]、[公用])。 類型必須包括 Visual Studio 電腦連線的網路。 

### <a name="verify-that-ports-are-open-in-the-windows-firewall-on-the-remote-computer"></a>驗證連接埠在遠端電腦上的 Windows 防火牆中開啟  
 遠端偵錯元件可以安裝在遠端電腦上，或從共用目錄執行。 這兩種情況下都必須設定遠端電腦的防火牆。 遠端偵錯元件位於：  
  
 **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具**  
  
 設定 Windows 防火牆的指示在不同作業系統上稍有不同。 Windows 8/8.1、 Windows 10 和 Windows Server 2012，word**應用程式**則使用 Windows 7 或 Windows Server 2008，word**程式**用; 在下列步驟中，我們將使用單字**應用程式**。  
  
1.  開啟 [Windows 防火牆] 頁面。 (在 [開始]  功能表搜尋方塊中，輸入 [Windows 防火牆] )。  
  
2.  按一下 [允許應用程式或功能通過 Windows 防火牆] 。  
  
3.  在 **允許應用程式和功能**清單中，尋找**Visual Studio 遠端偵錯工具**。 如果有列出，請確定已選取，而且也選取一或多個網路類型。  
  
4.  如果**Visual Studio 遠端偵錯工具**是未列出，請按一下 **允許另一個應用程式**。 如果您仍然沒有看到它在 **[新增應用程式] 視窗**，按一下**瀏覽**並瀏覽至 **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具**. 尋找應用程式適當的資料夾 (x86、x64、Appx)，然後選取 **msvsmon.exe**。 然後按一下 [加入] 。  
  
5.  在 **允許的應用程式**清單中，選取**Visual Studio 遠端偵錯工具**。 核取您想要遠端偵錯監視與其通訊的一或多個網路類型 ([網域]、[家用/工作 (私用)]、[公用])。 類型必須包括 Visual Studio 電腦連線的網路。 

### <a name="managed-or-native-compatibility-mode-open-additional-ports-on-the-remote-computer"></a>（managed 或原生相容性模式）在遠端電腦上開啟其他連接埠

如果您要用於偵錯工具中的相容性模式 (**工具 > 選項 > 偵錯**)，額外的連接埠必須開啟。 相容性模式可讓舊版偵錯工具，而且需要不同的連接埠。

> [!NOTE]
> 舊版偵錯工具是 Visual Studio 2010 的偵錯工具。
  
|**連接埠**|**傳入/傳出**|**通訊協定**|**描述**|  
|-|-|-|-|  
|135、139、445|傳出|TCP|必要。|  
|137、138|傳出|UDP|必要。|  
|500、4500|傳出|UDP|如果您的網域原則需要透過 IPSec 進行網路通訊時，則為必要項。|  
|80|傳出|TCP|網頁伺服器偵錯的必要項。|
  
## <a name="see-also"></a>另請參閱  
 [Remote Debugging](../debugger/remote-debugging.md)