---
title: 設定 Windows 防火牆進行遠端偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 10/31/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4e4ccc09d8919260b1634fd02790c1bf5b10636
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750932"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>設定 Windows 防火牆進行遠端偵錯

在網路上受保護的 Windows 防火牆，您必須設定防火牆，以允許遠端偵錯。 Visual Studio 和遠端偵錯工具嘗試在安裝或啟動時，開啟正確的防火牆連接埠，但您也可能需要開啟連接埠，或以手動方式允許應用程式。 

本主題描述如何設定 Windows 防火牆以啟用在 Windows 10、windows 8/8.1 和 7; 上的遠端偵錯與 Windows Server 2012 R2、 2012年和 2008 R2 電腦。 Visual Studio 和遠端電腦不用執行相同的作業系統。 比方說，在 Visual Studio 電腦可以執行 Windows 10 和遠端電腦可以執行 Windows Server 2012 R2。      
  
>[!NOTE]
>在不同的作業系統，以及舊版 Windows 的指示來設定 Windows 防火牆有些許不同。 Windows 8/8.1、 Windows 10 和 Windows Server 2012 的設定，請使用這個字*應用程式*，而 Windows 7 和 Windows Server 2008 使用 word*程式*。  

## <a name="configure-ports-for-remote-debugging"></a>設定遠端偵錯的連接埠  

Visual Studio 和遠端偵錯工具嘗試在安裝或啟動期間開啟正確的連接埠。 不過，在某些情況下，例如協力廠商防火牆，您可能需要手動開啟連接埠。 

**若要開啟連接埠：**
  
1. 在 [Windows**開始**] 功能表中，搜尋並開啟**具有進階安全性的 Windows 防火牆**。 這是在 Windows 10、windows**具有進階安全性的 Windows Defender 防火牆**。
   
1. 針對新的連入連接埠中，選取**輸入規則**，然後選取**新規則**。 針對外寄的規則，請選取**輸出規則**改。

1. 在 [**新增輸入規則精靈**，選取**連接埠**，然後選取**下一步]**。 
   
1. 選取  **TCP**或是**UDP**，取決於下表中的連接埠號碼。
   
1. 底下**特定本機連接埠**，從下表中，輸入連接埠號碼，然後選取**下一步**。
   
1. 選取 [**允許連線**，然後選取**下一步]**。
   
1. 選取一或多個網路類型，若要啟用，包括遠端連線的網路類型，然後選取**下一步**。
   
1. 新增規則的名稱 (例如**msvsmon**， **IIS**，或**Web Deploy**)，然後選取**完成**。

   新的規則應該會出現，並在選取**輸入規則**或是**輸出規則**清單。

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>在遠端電腦上啟用遠端偵錯的連接埠

遠端偵錯，必須在遠端電腦上開啟下列連接埠：

|**連接埠**|**傳入/傳出**|**通訊協定**|**描述**|   
|-|-|-|-|
|4022|連入|TCP|適用於 VS 2017。 針對每個 Visual Studio 版本 2 通訊埠數字會遞增。 如需詳細資訊，請參閱 < [Visual Studio 遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)。|  
|4023|連入|TCP|適用於 VS 2017。 針對每個 Visual Studio 版本 2 通訊埠數字會遞增。 此連接埠是只用於從遠端偵錯從 64 位元版本的遠端偵錯工具的 32 位元處理程序。 如需詳細資訊，請參閱 < [Visual Studio 遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)。| 
|3702|傳出|UDP|（選擇性）遠端偵錯工具探索的必要項。|    
  
如果您選取**使用 Managed 相容性模式**下方**工具** > **選項** > **偵錯**，開啟這些額外的遠端偵錯工具連接埠。 偵錯工具 Managed 相容性模式可讓舊版、 偵錯工具的 Visual Studio 2010 版本。 

|**連接埠**|**傳入/傳出**|**通訊協定**|**描述**|  
|-|-|-|-|  
|135、139、445|傳出|TCP|必要。|  
|137、138|傳出|UDP|必要。|  

如果您的網域原則需要透過 IPSec 進行網路通訊，您必須開啟 Visual Studio 和遠端電腦上的其他連接埠。 若要偵錯遠端 IIS web 伺服器上，開啟遠端電腦上的連接埠 80。

|**連接埠**|**傳入/傳出**|**通訊協定**|**描述**|  
|-|-|-|-|  
|500、4500|傳出|UDP|如果您的網域原則需要透過 IPSec 進行網路通訊時，則為必要項。|  
|80|傳出|TCP|Web 伺服器偵錯的必要項。|

若要允許通過 Windows 防火牆的特定應用程式，請參閱[設定通過 Windows 防火牆的遠端偵錯](#configure-remote-debugging-through-windows-firewall)。 

## <a name="configure-remote-debugging-through-windows-firewall"></a>設定通過 Windows 防火牆的遠端偵錯

您可以在遠端電腦上安裝遠端偵錯工具，或從共用資料夾執行。 在任一情況下，遠端電腦的防火牆必須正確設定。 

在遠端電腦上的遠端偵錯工具位於：  
  
*\<Visual Studio 安裝目錄\>\\Common7\\IDE\\遠端偵錯工具\\\<x86*， *x64*，或*Appx*\> 
  
### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>允許，設定通過 Windows 防火牆的遠端偵錯工具 
  
1. 在 [Windows**開始**] 功能表中，搜尋並開啟**Windows 防火牆**，或**Windows Defender 防火牆**。 
  
1. 選取 **允許應用程式通過 Windows 防火牆**。  
  
1.  如果**遠端偵錯工具**或是**Visual Studio 遠端偵錯工具**不會出現在**允許的應用程式和功能**，選取**變更設定**，然後選取**允許另一個應用程式**。 

1.  如果遠端偵錯工具應用程式仍未列在**新增應用程式**對話方塊中，選取**瀏覽**，然後瀏覽至 *\<Visual Studio 安裝目錄\>\\Common7\\IDE\\遠端偵錯工具\\\<x86*， *x64*，或*Appx* \>根據您的應用程式的適當架構。 選取  *msvsmon.exe*，然後選取**新增**。  
    
1.  在 **應用程式**清單中，選取**遠端偵錯工具**您剛才加入。 選取 **網路類型**，然後選取一或多個網路類型，包括遠端連線的網路類型。 
    
1.  選取 **新增**，然後選取**確定**。

## <a name="troubleshooting"></a>針對遠端偵錯連線進行疑難排解
  
如果無法使用遠端偵錯工具附加至您的應用程式，請確定遠端偵錯的防火牆連接埠通訊協定、 網路類型，以及應用程式設定都正確。 

- 在 Windows 中**開始** 功能表中，搜尋並開啟**Windows 防火牆**，然後選取**允許通過 Windows 防火牆的應用程式**。 請確定**遠端偵錯工具**或是**Visual Studio 遠端偵錯工具**會出現在**允許的應用程式和功能**清單中選取的核取方塊，與正確的網路類型選取此項目。 否則，請[新增正確的應用程式和設定](#configure-remote-debugging-through-windows-firewall)。
  
- 在 [Windows**開始**] 功能表中，搜尋並開啟**具有進階安全性的 Windows 防火牆**。 請確定**遠端偵錯工具**或是**Visual Studio 遠端偵錯工具**之下**輸入規則**(並選擇性地**輸出規則**)具有綠色核取記號圖示，而且的所有設定都都正確。 
  
  - 若要檢視或變更規則設定，以滑鼠右鍵按一下**遠端偵錯工具**應用程式清單中選取**屬性**。 使用**屬性**索引標籤，以啟用或停用規則，或變更連接埠號碼、 通訊協定或網路類型。 
  - 遠端偵錯工具應用程式不會出現在 [規則] 清單中，如果[新增並設定正確的連接埠](#configure-ports-for-remote-debugging)。 

## <a name="see-also"></a>另請參閱  
[遠端偵錯](../debugger/remote-debugging.md)

[Visual Studio 遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)
