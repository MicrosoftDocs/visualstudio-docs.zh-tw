---
title: 設定 Windows 防火牆進行遠端偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96b4e4cc929dc7941fac5e8a7f090e701fe2810f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935389"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>設定 Windows 防火牆進行遠端偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述如何設定防火牆，在執行下列作業系統的電腦上啟用遠端偵錯：  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 R2  
  
  如果正在偵錯的網路未受到防火牆保護，便不需要進行這項設定。 否則，裝載 Visual Studio 的電腦和要進行偵錯的遠端電腦都需要進行變更防火牆設定。  
  
  **IPSec** 如果您的網路要求使用 IPSec 執行通訊，您必須在 Visual Studio 主機電腦和遠端電腦上都開啟其他連接埠。  
  
  **網頁伺服器** 如果您正在偵錯遠端網頁伺服器，您必須在遠端電腦上開啟其他連接埠。  
  
  請注意，這兩部電腦不需要執行相同的作業系統。 例如，Visual Studio 電腦可以執行 Windows 10，而遠端電腦則可以執行 Windows Server 2012 R2。  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>在 Visual Studio 電腦上設定 Windows 防火牆  
 設定 Windows 防火牆的指示在不同作業系統上稍有不同。 在 Windows 7 或 Windows Server 2008，使用 **程式** 字樣，在 Windows 8/8.1、Windows 10 和 Windows Server 2012 上，則使用 **應用程式** 字樣。  我們將在下列步驟中使用 **應用程式**字樣。  
  
1.  開啟 [Windows 防火牆] 頁面。 (在 [開始]  功能表搜尋方塊中，輸入 [Windows 防火牆] )。  
  
2.  按一下 [允許應用程式或功能通過 Windows 防火牆] 。  
  
3.  在 [允許應用程式和功能]  清單中尋找 [Visual Studio 遠端偵錯工具探索] 。 如果有列出，請確定已選取，而且也選取一或多個網路類型。  
  
4.  如果未列出 [Visual Studio 遠端偵錯工具探索]  ，請按一下 [允許另一個應用程式] 。 如果您仍然不會看到**新增應用程式** 視窗中，按一下**瀏覽**並瀏覽至 **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具**. 尋找應用程式適當的資料夾 (x86、x64、Appx)，然後選取 **msvsmon.exe**。 然後按一下 [加入] 。  
  
5.  在 [允許的應用程式和功能]  清單中，選取 [Visual Studio 遠端偵錯監視] 。 核取您想要遠端偵錯監視與其通訊的一或多個網路類型 ([網域]、[家用/工作 (私用)]、[公用])。 類型必須包括 Visual Studio 電腦連線的網路。  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>在 Visual Studio 電腦上開啟連接埠以啟用探索  
 您必須允許 UDP 連接埠 3702 傳入以允許探索執行遠端偵錯工具的電腦。 若要將它加入，請參閱＜如何在防火牆中設定連接埠＞。  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>設定遠端電腦的 Windows 防火牆以進行遠端偵錯  
 遠端偵錯元件可以安裝在遠端電腦上，或從共用目錄執行。 這兩種情況下都必須設定遠端電腦的防火牆。 遠端偵錯元件位於：  
  
 **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具**  
  
 設定 Windows 防火牆的指示在不同作業系統上稍有不同。 在 Windows 7 或 Windows Server 2008，使用 **程式** 字樣，在 Windows 8/8.1、Windows 10 和 Windows Server 2012 上，則使用 **應用程式** 字樣。  我們將在下列步驟中使用 **應用程式**字樣。  
  
1.  開啟 [Windows 防火牆] 頁面。 (在 [開始]  功能表搜尋方塊中，輸入 [Windows 防火牆] )。  
  
2.  按一下 [允許應用程式或功能通過 Windows 防火牆] 。  
  
3.  在 [允許應用程式和功能]  清單中尋找 [Visual Studio 遠端偵錯監視] 。 如果有列出，請確定已選取，而且也選取一或多個網路類型。  
  
4.  如果未列出 [Visual Studio 遠端偵監視]  ，請按一下 [允許另一個應用程式] 。 如果您仍然沒有看到它在 **[新增應用程式] 視窗**，按一下**瀏覽**並瀏覽至 **\<Visual Studio 安裝目錄 > \Common7\IDE\Remote 偵錯工具**. 尋找應用程式適當的資料夾 (x86、x64、Appx)，然後選取 **msvsmon.exe**。 然後按一下 [加入] 。  
  
5.  在 [允許的應用程式]  清單中，選取 [Visual Studio 遠端偵錯監視] 。 核取您想要遠端偵錯監視與其通訊的一或多個網路類型 ([網域]、[家用/工作 (私用)]、[公用])。 類型必須包括 Visual Studio 電腦連線的網路。  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>在遠端電腦上啟用遠端偵錯的連接埠  
  
|||||  
|-|-|-|-|  
|**連接埠**|**傳入/傳出**|**通訊協定**|**描述**|  
|3702|傳出|UDP|遠端偵錯工具探索的必要項。|  
|4020||TCP|針對 VS 2015。 針對每個 Visual Studio 版本，連接埠號碼會遞增 2。 如需詳細資訊，請參閱＜Visual Studio 遠端偵錯工具連接埠指派＞。|  
|4021||TCP|針對 VS 2015。 針對每個 Visual Studio 版本，連接埠號碼會遞增 2。 如需詳細資訊，請參閱＜Visual Studio 遠端偵錯工具連接埠指派＞。|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>在遠端電腦上以 Managed 或原生相容性模式啟用遠端偵錯的連接埠  
  
|||||  
|-|-|-|-|  
|**連接埠**|**傳入/傳出**|**通訊協定**|**描述**|  
|135、139、445|傳出|TCP|必要。|  
|137、138|傳出|UDP|必要。|  
|500、4500|傳出|UDP|如果您的網域原則需要透過 IPSec 進行網路通訊時，則為必要項。|  
|80|傳出|TCP|網頁伺服器偵錯的必要項。|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>如何在 Windows 防火牆中設定連接埠  
  
1.  在 [開始]  功能表中，搜尋 [具有進階安全性的 Windows 防火牆] 。  
  
2.  按一下 [輸入規則]  或 [輸出規則]  ，然後按一下 [動作]  清單中的 [新增規則]  。  
  
3.  在 [規則類型]  頁面上，選取 [連接埠]  然後按 [下一步] 。  
  
4.  在 [通訊協定和連接埠]  頁面上，選取連接埠通訊協定 (TCP 或 UDP)。 選取 [特定本機連接埠]  並輸入您想要針對通訊協定啟用的一個或多個連接埠號碼。 以逗號分隔數字。 然後按 [下一步] 。  
  
5.  在 [動作]  頁面上，選取 [允許連線]  然後按 [下一步] 。  
  
6.  在 [設定檔]  頁面上，選取要為連接埠啟用的一個或多個網路類型。 您選取的類型必須包括遠端電腦連線的網路。 然後按 [下一步] 。  
  
7.  在 [名稱]  頁面上，輸入規則的名稱，然後按一下 [完成] 。  
  
8.  您應該會在 [輸入規則]  或 [輸出規則]  清單中看到您的新規則。  
  
## <a name="see-also"></a>另請參閱  
 [Remote Debugging](../debugger/remote-debugging.md)



